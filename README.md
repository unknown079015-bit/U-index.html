# U-index.html
<!DOCTYPE html>
<html>
<head>
  <title>Sunflower Proposal</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      font-family: Arial, sans-serif;
      text-align: center;
      background: #fff8e7;
    }

    h1 {
      margin-top: 50px;
      font-size: 28px;
    }

    .container {
      position: relative;
      margin-top: 50px;
    }

    .hand {
      font-size: 80px;
    }

    .flower {
      font-size: 60px;
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      top: 40px;
      transition: all 1s ease;
    }

    button {
      padding: 12px 25px;
      margin: 20px;
      font-size: 18px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }

    #yes {
      background: #4CAF50;
      color: white;
    }

    #no {
      background: #f44336;
      color: white;
    }

    /* Sunset popup */
    .sunset {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(to top, #ff7e5f, #feb47b);
      color: white;
      font-size: 30px;
      justify-content: center;
      align-items: center;
      flex-direction: column;
    }

    /* Rain effect */
    .rain {
      position: fixed;
      width: 100%;
      height: 100%;
      display: none;
      top: 0;
      left: 0;
      pointer-events: none;
    }

    .drop {
      position: absolute;
      width: 2px;
      height: 15px;
      background: blue;
      animation: fall linear infinite;
    }

    @keyframes fall {
      from { transform: translateY(-100px); }
      to { transform: translateY(100vh); }
    }

  </style>
</head>

<body>

<h1>Will you accept this sunflower? 🌻</h1>

<div class="container">
  <div class="hand" id="leftHand">🤲</div>
  <div class="flower" id="flower">🌻</div>
  <div class="hand" id="rightHand" style="margin-top:100px;">🫴</div>
</div>

<button id="yes" onclick="accept()">Yes 💛</button>
<button id="no" onclick="reject()">No 💔</button>

<!-- Sunset -->
<div class="sunset" id="sunset">
  🌅 <br><br>
  You accepted the flower 💛
</div>

<!-- Rain -->
<div class="rain" id="rain"></div>

<script>
function accept() {
  let flower = document.getElementById("flower");
  flower.style.top = "140px"; // move to other hand

  setTimeout(() => {
    document.getElementById("sunset").style.display = "flex";
  }, 1000);
}

function reject() {
  let flower = document.getElementById("flower");
  flower.innerHTML = "🥀"; // decomposed flower

  startRain();
}

function startRain() {
  let rain = document.getElementById("rain");
  rain.style.display = "block";

  for (let i = 0; i < 100; i++) {
    let drop = document.createElement("div");
    drop.classList.add("drop");
    drop.style.left = Math.random() * 100 + "vw";
    drop.style.animationDuration = (0.5 + Math.random()) + "s";
    rain.appendChild(drop);
  }
}
</script>

</body>
</html>
