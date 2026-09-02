# 91club
Color prediction
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>91Club Color Demo</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: Arial, sans-serif;
      min-height: 100vh;
      background: linear-gradient(135deg, #111827, #1e293b);
      color: white;
      padding: 20px;
    }

    .container {
      max-width: 480px;
      margin: auto;
    }

    .header {
      text-align: center;
      padding: 25px 10px;
    }

    .header h1 {
      font-size: 32px;
      margin-bottom: 8px;
    }

    .header p {
      color: #cbd5e1;
    }

    .card {
      background: rgba(255,255,255,0.08);
      border: 1px solid rgba(255,255,255,0.12);
      border-radius: 20px;
      padding: 22px;
      margin-bottom: 18px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.25);
    }

    .round {
      text-align: center;
      color: #94a3b8;
      margin-bottom: 15px;
    }

    .result {
      width: 130px;
      height: 130px;
      margin: 20px auto;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 42px;
      font-weight: bold;
      background: #334155;
      border: 6px solid #64748b;
      transition: 0.3s;
    }

    .red {
      background: #dc2626;
      border-color: #f87171;
    }

    .green {
      background: #16a34a;
      border-color: #4ade80;
    }

    .violet {
      background: #7c3aed;
      border-color: #a78bfa;
    }

    button {
      width: 100%;
      border: none;
      padding: 16px;
      border-radius: 14px;
      background: #2563eb;
      color: white;
      font-size: 17px;
      font-weight: bold;
      cursor: pointer;
    }

    button:active {
      transform: scale(0.98);
    }

    .status {
      text-align: center;
      margin-top: 15px;
      color: #cbd5e1;
      min-height: 22px;
    }

    .history-title {
      margin-bottom: 15px;
      font-size: 20px;
    }

    .history {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .history-item {
      display: flex;
      justify-content: space-between;
      background: rgba(255,255,255,0.06);
      padding: 13px;
      border-radius: 10px;
    }

    .notice {
      text-align: center;
      font-size: 12px;
      color: #94a3b8;
      line-height: 1.5;
      margin-top: 15px;
    }
  </style>
</head>

<body>

  <div class="container">

    <div class="header">
      <h1>🎨 91Club</h1>
      <p>Color Prediction Demo</p>
    </div>

    <div class="card">

      <div class="round">
        Round #<span id="round">1001</span>
      </div>

      <div id="result" class="result">
        ?
      </div>

      <button onclick="generateResult()">
        GENERATE DEMO RESULT
      </button>

      <div id="status" class="status">
        Tap the button to generate a demo result
      </div>

    </div>

    <div class="card">

      <div class="history-title">
        📊 Recent Results
      </div>

      <div id="history" class="history">
        <div class="history-item">
          <span>Round #1000</span>
          <b>🟢 Green</b>
        </div>

        <div class="history-item">
          <span>Round #999</span>
          <b>🔴 Red</b>
        </div>

        <div class="history-item">
          <span>Round #998</span>
          <b>🟣 Violet</b>
        </div>
      </div>

    </div>

    <div class="notice">
      ⚠️ Demo only. Results are randomly generated.
      This page does not provide guaranteed predictions,
      betting advice, or real-money results.
    </div>

  </div>


  <script>

    let roundNumber = 1001;

    function generateResult() {

      const resultBox = document.getElementById("result");
      const status = document.getElementById("status");

      const colors = [
        {
          name: "Red",
          emoji: "🔴",
          className: "red"
        },
        {
          name: "Green",
          emoji: "🟢",
          className: "green"
        },
        {
          name: "Violet",
          emoji: "🟣",
          className: "violet"
        }
      ];

      status.textContent = "Generating...";

      setTimeout(() => {

        const result =
          colors[Math.floor(Math.random() * colors.length)];

        resultBox.className =
          "result " + result.className;

        resultBox.textContent = result.emoji;

        status.textContent =
          "Demo result: " + result.name;

        addHistory(
          roundNumber,
          result.emoji + " " + result.name
        );

        roundNumber++;

        document.getElementById("round").textContent =
          roundNumber;

      }, 500);
    }


    function addHistory(round, result) {

      const history =
        document.getElementById("history");

      const item =
        document.createElement("div");

      item.className = "history-item";

      item.innerHTML =
        "<span>Round #" + round +
        "</span><b>" + result + "</b>";

      history.prepend(item);

      if (history.children.length > 8) {
        history.removeChild(history.lastChild);
      }
    }

  </script>

</body>
</html>