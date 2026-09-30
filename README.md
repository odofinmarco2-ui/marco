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
      <input
        id="search"
        type="text"
        placeholder="🔎 Search games..."
      >

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

<script>

const games = [
  {
    title: "Snake",
    category: "Popular",
    rating: 4.9,
    plays: 1200000,
    emoji: "🐍"
  },
  {
    title: "2048",
    category: "Puzzle",
    rating: 4.8,
    plays: 950000,
    emoji: "🔢"
  },
  {
    title: "Space Shooter",
    category: "Action",
    rating: 4.7,
    plays: 870000,
    emoji: "🚀"
  },
  {
    title: "Top-down Racing",
    category: "Racing",
    rating: 4.6,
    plays: 640000,
    emoji: "🏎️"
  },
  {
    title: "Chess",
    category: "Puzzle",
    rating: 4.9,
    plays: 720000,
    emoji: "♟️"
  },
  {
    title: "Aim Trainer",
    category: "Casual",
    rating: 4.5,
    plays: 580000,
    emoji: "🎯"
  }
];

const gameList = document.getElementById("gameList");
const search = document.getElementById("search");
const categoryFilter = document.getElementById("categoryFilter");
const sortFilter = document.getElementById("sortFilter");

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
    filtered = filtered.filter(game =>
      game.title.toLowerCase().includes(searchText)
    );
  }

  if (category !== "All") {
    filtered = filtered.filter(game =>
      game.category === category
    );
  }

  if (sort === "plays") {
    filtered.sort((a, b) => b.plays - a.plays);
  }

  if (sort === "rating") {
    filtered.sort((a, b) => b.rating - a.rating);
  }

  if (sort === "name") {
    filtered.sort((a, b) =>
      a.title.localeCompare(b.title)
    );
  }

  gameList.innerHTML = "";

  if (filtered.length === 0) {
    gameList.innerHTML =
      "<p style='color:#a1a1aa'>No games found.</p>";
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
      alert(
        `${game.title} selected!\n\nYou can connect this card to the actual game later.`
      );
    });

    gameList.appendChild(card);
  });
}

search.addEventListener("input", renderGames);
categoryFilter.addEventListener("change", renderGames);
sortFilter.addEventListener("change", renderGames);

renderGames();

</script>

</body>
</html>
