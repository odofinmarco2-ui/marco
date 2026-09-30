# marco
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>🎮 GameHub</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: Arial, Helvetica, sans-serif;
      background: #000;
      color: white;
      min-height: 100vh;
    }

    header {
      background: linear-gradient(90deg, #c026d3, #7e22ce, #06b6d4);
      padding: 22px 6%;
      position: sticky;
      top: 0;
      z-index: 10;
      box-shadow: 0 10px 30px rgba(0,0,0,.5);
    }

    .nav {
      max-width: 1200px;
      margin: auto;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 30px;
    }

    .logo {
      font-size: 30px;
      font-weight: 900;
      white-space: nowrap;
    }

    nav {
      display: flex;
      gap: 25px;
    }

    nav a {
      color: white;
      text-decoration: none;
      font-weight: bold;
      font-size: 14px;
    }

    nav a:hover {
      opacity: .7;
    }

    .hero {
      max-width: 1200px;
      margin: auto;
      padding: 100px 25px 70px;
      text-align: center;
    }

    .hero h2 {
      font-size: clamp(42px, 7vw, 80px);
      font-weight: 900;
      margin-bottom: 20px;
    }

    .hero p {
      color: #d1d5db;
      font-size: 20px;
      max-width: 750px;
      margin: auto;
      line-height: 1.6;
    }

    .container {
      max-width: 1200px;
      margin: auto;
      padding: 0 25px;
    }

    .filters {
      display: flex;
      gap: 15px;
      margin-bottom: 55px;
    }

    input,
    select {
      background: #18181b;
      color: white;
      border: 1px solid #27272a;
      border-radius: 15px;
      padding: 16px;
      font-size: 16px;
      outline: none;
    }

    input {
      flex: 1;
    }

    input:focus,
    select:focus {
      border-color: #d946ef;
    }

    section {
      margin-bottom: 70px;
    }

    h3 {
      font-size: 30px;
      margin-bottom: 25px;
    }

    .games {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 25px;
    }

    .game-card {
      background: linear-gradient(145deg, #18181b, #27272a);
      border: 1px solid rgba(217,70,239,.3);
      border-radius: 25px;
      padding: 25px;
      cursor: pointer;
      transition: .25s;
    }

    .game-card:hover {
      transform: translateY(-7px) scale(1.02);
      border-color: #d946ef;
      box-shadow: 0 15px 40px rgba(217,70,239,.2);
    }

    .emoji {
      font-size: 60px;
      margin-bottom: 15px;
    }

    .game-card h4 {
      font-size: 24px;
      margin-bottom: 8px;
    }

    .category {
      color: #22d3ee;
    }

    .stats {
      display: flex;
      justify-content: space-between;
      margin-top: 20px;
      color: #d4d4d8;
      font-size: 14px;
    }

    .category-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 25px;
    }

    .category-box,
    .info-box {
      background: #18181b;
      border-radius: 25px;
      padding: 30px;
    }

    .category-box ul,
    .info-box ul {
      list-style: none;
      color: #d4d4d8;
    }

    .category-box li {
      padding: 8px 0;
      cursor: pointer;
    }

    .category-box li:hover {
      color: #22d3ee;
    }

    .bottom-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 25px;
    }

    .leaderboard div {
      display: flex;
      justify-content: space-between;
      padding: 12px 0;
      border-bottom: 1px solid #27272a;
    }

    footer {
      text-align: center;
      padding: 40px 20px;
      border-top: 1px solid #27272a;
      color: #71717a;
    }

    .modal {
      position: fixed;
      inset: 0;
      background: rgba(2, 6, 23, 0.8);
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 20px;
      z-index: 50;
    }

    .modal.hidden {
      display: none;
    }

    .modal-card {
      width: min(100%, 520px);
      background: linear-gradient(180deg, #0f172a, #111827);
      border: 1px solid rgba(217,70,239,0.5);
      border-radius: 28px;
      padding: 24px;
      box-shadow: 0 30px 60px rgba(0,0,0,0.45);
      position: relative;
    }

    .close-btn {
      position: absolute;
      right: 18px;
      top: 14px;
      background: transparent;
      border: none;
      color: white;
      font-size: 28px;
      cursor: pointer;
      opacity: 0.8;
    }

    .modal-card h3 {
      margin-bottom: 14px;
      padding-right: 30px;
    }

    .score-row {
      display: flex;
      justify-content: space-between;
      margin-bottom: 16px;
      color: #e2e8f0;
      font-weight: 700;
    }

    canvas {
      display: block;
      width: 100%;
      max-width: 360px;
      height: auto;
      margin: 0 auto 18px;
      background: #020617;
      border: 3px solid rgba(34, 211, 238, 0.8);
      border-radius: 18px;
    }

    .game-controls {
      display: flex;
      justify-content: center;
      gap: 12px;
      flex-wrap: wrap;
    }

    button {
      background: linear-gradient(90deg, #c026d3, #7c3aed);
      color: white;
      border: none;
      padding: 12px 18px;
      font-size: 15px;
      border-radius: 12px;
      cursor: pointer;
      font-weight: 700;
      transition: 0.2s ease;
    }

    button:hover {
      filter: brightness(1.1);
      transform: translateY(-1px);
    }

    @media (max-width: 800px) {
      .nav {
        flex-direction: column;
      }

      nav {
        flex-wrap: wrap;
        justify-content: center;
      }

      .games {
        grid-template-columns: 1fr;
      }

      .category-grid,
      .bottom-grid {
        grid-template-columns: 1fr;
      }

      .filters {
        flex-direction: column;
      }
    }

    @media (max-width: 500px) {
      .hero {
        padding-top: 60px;
      }

      .hero h2 {
        font-size: 42px;
      }

      .logo {
        font-size: 25px;
      }
    }
  </style>
</head>

<body>

<header>
  <div class="nav">
    <div class="logo">🎮 GAMEHUB</div>

    <nav>
      <a href="#games">PLAY GAMES</a>
      <a href="#trending">TRENDING</a>
      <a href="#leaderboard">LEADERBOARD</a>
      <a href="#favorites">FAVORITES</a>
    </nav>
  </div>
</header>

<main>

  <div class="hero">
    <h2>Your Online Arcade</h2>
    <p>
      Jump into dozens of instant browser games.
      No downloads. No waiting. Just fun.
    </p>
  </div>

  <div class="container">

    <div class="filters">
      <input id="search" type="text" placeholder="🔎 Search games...">
      <select id="categoryFilter">
        <option value="All">All Categories</option>
        <option value="Popular">Popular</option>
        <option value="Action">Action</option>
        <option value="Puzzle">Puzzle</option>
        <option value="Racing">Racing</option>
        <option value="Casual">Casual</option>
      </select>

      <select id="sortFilter">
        <option value="plays">Most Played</option>
        <option value="rating">Highest Rated</option>
        <option value="name">Alphabetical</option>
      </select>
    </div>

    <section id="trending">
      <h3>🔥 Trending Games</h3>
      <div class="games" id="gameList"></div>
    </section>

    <section id="games">
      <div class="category-grid">

        <div class="category-box">
          <h3>🔥 Popular</h3>
          <ul>
            <li>🐍 Snake</li>
            <li>🐦 Flappy Bird</li>
            <li>🔢 2048</li>
            <li>🧱 Tetris</li>
            <li>💣 Minesweeper</li>
            <li>🧠 Memory Match</li>
          </ul>
        </div>

        <div class="category-box">
          <h3>⚡ Action</h3>
          <ul>
            <li>🚀 Space Shooter</li>
            <li>🧟 Zombie Survival</li>
            <li>🏃 Platformer</li>
            <li>🏃 Endless Runner</li>
            <li>💥 Dodge the Obstacles</li>
          </ul>
        </div>

        <div class="category-box">
          <h3>🧠 Puzzle</h3>
          <ul>
            <li>🔢 Sudoku</li>
            <li>🔤 Word Guess</li>
            <li>🧩 Match-3</li>
            <li>♟️ Chess</li>
            <li>🔴 Connect Four</li>
          </ul>
        </div>

        <div class="category-box">
          <h3>🏎️ Racing</h3>
          <ul>
            <li>🏎️ Top-down Racing</li>
            <li>⏱️ Time Trial</li>
            <li>🚧 Obstacle Racing</li>
          </ul>
        </div>

      </div>
    </section>

    <section id="leaderboard">
      <div class="bottom-grid">
        <div class="info-box">
          <h3>👤 Player Profile</h3>
          <ul>
            <li>🎮 Games Played</li>
            <li>🏆 High Scores</li>
            <li>⭐ Achievements</li>
            <li>❤️ Favorite Games</li>
            <li>⏱️ Total Play Time</li>
            <li>🌎 Global Ranking</li>
          </ul>
        </div>

        <div class="info-box leaderboard">
          <h3>🏆 Global Leaderboard</h3>

          <div>
            <span>#1 ArcadeMaster</span>
            <strong>98,500</strong>
          </div>

          <div>
            <span>#2 PixelPro</span>
            <strong>95,200</strong>
          </div>

          <div>
            <span>#3 TurboPlayer</span>
            <strong>90,100</strong>
          </div>

          <div>
            <span>#4 SnakeKing</span>
            <strong>85,800</strong>
          </div>
        </div>
      </div>
    </section>

  </div>

</main>

<footer>
  🎮 GameHub • Digital Arcade Experience • Play Anywhere
</footer>

<div id="snakeModal" class="modal hidden" aria-hidden="true">
  <div class="modal-card">
    <button id="closeSnakeGame" class="close-btn" aria-label="Close game">×</button>
    <h3>🐍 Snake</h3>

    <div class="score-row">
      <span>Score: <strong id="snakeScore">0</strong></span>
      <span id="snakeState">Ready</span>
    </div>

    <canvas id="snakeCanvas" width="360" height="360"></canvas>

    <div class="game-controls">
      <button id="startSnakeBtn">Start / Restart</button>
    </div>
  </div>
</div>

<script>
const games = [
  { title: "Snake", category: "Popular", rating: 4.9, plays: 1200000, emoji: "🐍" },
  { title: "2048", category: "Puzzle", rating: 4.8, plays: 950000, emoji: "🔢" },
  { title: "Space Shooter", category: "Action", rating: 4.7, plays: 870000, emoji: "🚀" },
  { title: "Top-down Racing", category: "Racing", rating: 4.6, plays: 640000, emoji: "🏎️" },
  { title: "Chess", category: "Puzzle", rating: 4.9, plays: 720000, emoji: "♟️" },
  { title: "Aim Trainer", category: "Casual", rating: 4.5, plays: 580000, emoji: "🎯" }
];

const gameList = document.getElementById("gameList");
const search = document.getElementById("search");
const categoryFilter = document.getElementById("categoryFilter");
const sortFilter = document.getElementById("sortFilter");

const snakeModal = document.getElementById("snakeModal");
const closeSnakeGameBtn = document.getElementById("closeSnakeGame");
const startSnakeBtn = document.getElementById("startSnakeBtn");
const snakeCanvas = document.getElementById("snakeCanvas");
const snakeCtx = snakeCanvas.getContext("2d");
const snakeScore = document.getElementById("snakeScore");
const snakeState = document.getElementById("snakeState");

const GRID_SIZE = 18;
const CELL_SIZE = snakeCanvas.width / GRID_SIZE;

const snakeGame = {
  snake: [],
  direction: { x: 1, y: 0 },
  food: { x: 0, y: 0 },
  score: 0,
  intervalId: null,
  running: false,
  speed: 120
};

function formatPlays(number) {
  if (number >= 1000000) {
    return (number / 1000000).toFixed(1) + "M";
  }
  return Math.round(number / 1000) + "K";
}

function renderGames() {
  let filtered = [...games];
  const searchText = search.value.toLowerCase();
  const category = categoryFilter.value;
  const sort = sortFilter.value;

  if (searchText) {
    filtered = filtered.filter(game => game.title.toLowerCase().includes(searchText));
  }

  if (category !== "All") {
    filtered = filtered.filter(game => game.category === category);
  }

  if (sort === "plays") {
    filtered.sort((a, b) => b.plays - a.plays);
  }

  if (sort === "rating") {
    filtered.sort((a, b) => b.rating - a.rating);
  }

  if (sort === "name") {
    filtered.sort((a, b) => a.title.localeCompare(b.title));
  }

  gameList.innerHTML = "";

  if (filtered.length === 0) {
    gameList.innerHTML = "<p style='color:#a1a1aa'>No games found.</p>";
    return;
  }

  filtered.forEach(game => {
    const card = document.createElement("div");
    card.className = "game-card";
    card.innerHTML = `
      <div class="emoji">${game.emoji}</div>
      <h4>${game.title}</h4>
      <p class="category">${game.category}</p>
      <div class="stats">
        <span>⭐ ${game.rating}</span>
        <span>▶ ${formatPlays(game.plays)}</span>
      </div>
    `;

    card.addEventListener("click", () => {
      if (game.title === "Snake") {
        openSnakeGame();
      } else {
        alert(`${game.title} selected!\n\nThis game is ready for a future expansion.`);
      }
    });

    gameList.appendChild(card);
  });
}

function openSnakeGame() {
  snakeModal.classList.remove("hidden");
  snakeModal.setAttribute("aria-hidden", "false");
  restartSnakeGame();
}

function closeSnakeGame() {
  snakeModal.classList.add("hidden");
  snakeModal.setAttribute("aria-hidden", "true");
  if (snakeGame.intervalId) {
    clearInterval(snakeGame.intervalId);
    snakeGame.intervalId = null;
  }
  snakeGame.running = false;
  snakeState.textContent = "Ready";
}

function restartSnakeGame() {
  if (snakeGame.intervalId) {
    clearInterval(snakeGame.intervalId);
    snakeGame.intervalId = null;
  }

  snakeGame.score = 0;
  snakeGame.direction = { x: 1, y: 0 };
  snakeGame.snake = [
    { x: 8, y: 9 },
    { x: 7, y: 9 },
    { x: 6, y: 9 }
  ];
  snakeGame.running = true;
  snakeScore.textContent = "0";
  snakeState.textContent = "Playing";
  placeFood();
  drawSnakeBoard();
  snakeGame.intervalId = setInterval(stepSnake, snakeGame.speed);
}

function placeFood() {
  let nextFood = {
    x: Math.floor(Math.random() * GRID_SIZE),
    y: Math.floor(Math.random() * GRID_SIZE)
  };

  while (snakeGame.snake.some(segment => segment.x === nextFood.x && segment.y === nextFood.y)) {
    nextFood = {
      x: Math.floor(Math.random() * GRID_SIZE),
      y: Math.floor(Math.random() * GRID_SIZE)
    };
  }

  snakeGame.food = nextFood;
}

function drawSnakeBoard() {
  snakeCtx.clearRect(0, 0, snakeCanvas.width, snakeCanvas.height);
  snakeCtx.fillStyle = "#020617";
  snakeCtx.fillRect(0, 0, snakeCanvas.width, snakeCanvas.height);

  for (let x = 0; x < GRID_SIZE; x++) {
    for (let y = 0; y < GRID_SIZE; y++) {
      snakeCtx.strokeStyle = "rgba(148, 163, 184, 0.12)";
      snakeCtx.strokeRect(x * CELL_SIZE, y * CELL_SIZE, CELL_SIZE, CELL_SIZE);
    }
  }

  snakeCtx.fillStyle = "#facc15";
  snakeCtx.fillRect(
    snakeGame.food.x * CELL_SIZE + 4,
    snakeGame.food.y * CELL_SIZE + 4,
    CELL_SIZE - 8,
    CELL_SIZE - 8
  );

  snakeGame.snake.forEach((segment, index) => {
    snakeCtx.fillStyle = index === 0 ? "#22c55e" : "#4ade80";
    snakeCtx.fillRect(
      segment.x * CELL_SIZE + 1,
      segment.y * CELL_SIZE + 1,
      CELL_SIZE - 2,
      CELL_SIZE - 2
    );
  });
}

function stepSnake() {
  const newHead = {
    x: snakeGame.snake[0].x + snakeGame.direction.x,
    y: snakeGame.snake[0].y + snakeGame.direction.y
  };

  const hitWall = newHead.x < 0 || newHead.x >= GRID_SIZE || newHead.y < 0 || newHead.y >= GRID_SIZE;
  const hitSelf = snakeGame.snake.slice(1).some(segment => segment.x === newHead.x && segment.y === newHead.y);

  if (hitWall || hitSelf) {
    snakeGame.running = false;
    clearInterval(snakeGame.intervalId);
    snakeGame.intervalId = null;
    snakeState.textContent = "Game over";
    return;
  }

  snakeGame.snake.unshift(newHead);

  if (newHead.x === snakeGame.food.x && newHead.y === snakeGame.food.y) {
    snakeGame.score += 10;
    snakeScore.textContent = String(snakeGame.score);
    placeFood();
  } else {
    snakeGame.snake.pop();
  }

  drawSnakeBoard();
}

function handleSnakeInput(event) {
  const key = event.key.toLowerCase();
  const directionMap = {
    arrowup: { x: 0, y: -1 },
    w: { x: 0, y: -1 },
    arrowdown: { x: 0, y: 1 },
    s: { x: 0, y: 1 },
    arrowleft: { x: -1, y: 0 },
    a: { x: -1, y: 0 },
    arrowright: { x: 1, y: 0 },
    d: { x: 1, y: 0 }
  };

  if (!directionMap[key]) {
    if (key === " " && !snakeGame.running) {
      event.preventDefault();
      restartSnakeGame();
    }
    return;
  }

  const next = directionMap[key];
  const isOpposite = snakeGame.direction.x + next.x === 0 && snakeGame.direction.y + next.y === 0;

  if (!isOpposite) {
    event.preventDefault();
    snakeGame.direction = next;
  }
}

search.addEventListener("input", renderGames);
categoryFilter.addEventListener("change", renderGames);
sortFilter.addEventListener("change", renderGames);
closeSnakeGameBtn.addEventListener("click", closeSnakeGame);
startSnakeBtn.addEventListener("click", restartSnakeGame);
document.addEventListener("keydown", handleSnakeInput);

renderGames();
drawSnakeBoard();
</script>

</body>
</html>
