<!DOCTYPE html>
<html lang="uz">
<head>
<meta charset="UTF-8">
<title>Spinner Wheel</title>
<style>
  body {
    text-align: center;
    font-family: Arial;
    margin-top: 50px;
  }

  .wheel {
    width: 300px;
    height: 300px;
    border-radius: 50%;
    border: 5px solid black;
    margin: 20px auto;
    position: relative;
    transition: transform 4s ease-out;
  }

  .segment {
    position: absolute;
    width: 50%;
    height: 50%;
    background: lightblue;
    transform-origin: 100% 100%;
    text-align: center;
    line-height: 150px;
    font-weight: bold;
  }

  button {
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
  }

  .pointer {
    width: 0;
    height: 0;
    border-left: 15px solid transparent;
    border-right: 15px solid transparent;
    border-bottom: 30px solid red;
    margin: auto;
  }
</style>
</head>
<body>

<h2>Omad Barabani</h2>
<div class="pointer"></div>
<div class="wheel" id="wheel"></div>
<button onclick="spin()">Aylantir</button>

<script>
const wheel = document.getElementById("wheel");
const options = ["1", "2", "3", "4", "5", "6"];
const segmentAngle = 360 / options.length;

options.forEach((option, index) => {
  const segment = document.createElement("div");
  segment.className = "segment";
  segment.style.transform = `rotate(${index * segmentAngle}deg) skewY(${90 - segmentAngle}deg)`;
  segment.innerHTML = option;
  wheel.appendChild(segment);
});

let currentRotation = 0;

function spin() {
  const randomSpin = Math.floor(Math.random() * 360) + 720;
  currentRotation += randomSpin;
  wheel.style.transform = `rotate(${currentRotation}deg)`;
}
</script>

</body>
</html>
