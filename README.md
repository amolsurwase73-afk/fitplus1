FitPulse/
│
├── index.html
├── style.css
├── script.js
│
├── assets/
│   ├── icons/
│   └── images/
│
├── components/
│   ├── header.html
│   ├── dashboard.html
│   └── footer.html
│
├── README.md
└── package.json   (optional if no Node)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>FitPulse</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>FitPulse</h1>
  </header>

  <main>
    <section class="stats">
      <h2>Today’s Stats</h2>
      <p id="steps">Steps: 0</p>
      <p id="calories">Calories Burned: 0</p>
    </section>

    <button onclick="updateStats()">Refresh Stats</button>
  </main>

  <script src="script.js"></script>
</body>
</html>
body {
  margin: 0;
  padding: 0;
  font-family: Arial;
  background: #f5f5f5;
}

header {
  background: #4a7bf7;
  color: #fff;
  padding: 15px;
  text-align: center;
}

.stats {
  margin: 20px;
  background: #fff;
  padding: 15px;
  border-radius: 8px;
}
