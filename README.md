# Javascript-Clock
Just a simple clock made from javascript, css and html


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JS + CSS Clock</title>
</head>
<body>


    <div class="clock">
      <div class="clock-face">
        <div class="hand hour-hand"></div>
        <div class="hand min-hand"></div>
        <div class="hand second-hand"></div> 
      </div>
    </div>


  <style>
    html {
      background: #018DED url(http://unsplash.it/1500/1000?image=881&blur=5);
      background-size: cover;
      font-family: 'helvetica neue';
      text-align: center;
      font-size: 10px;
    }

    body {
      margin: 0;
      font-size: 2rem;
      display: flex;
      flex: 1;
      min-height: 100vh;
      align-items: center;
    }

    .clock {
      width: 30rem;
      height: 30rem;
      border: 20px solid white;
      border-radius: 50%;
      margin: 50px auto;
      position: relative;
      padding: 2rem;
      box-shadow:
        0 0 0 4px rgba(0,0,0,0.1),
        inset 0 0 0 3px #EFEFEF,
        inset 0 0 10px black,
        0 0 10px rgba(0,0,0,0.2);
    }

    .clock-face {
      position: relative;
      width: 100%;
      height: 100%;
      transform: translateY(-3px); /* account for the height of the clock hands */
    }

    .hand {
      width: 50%;
      height: 6px;
      background: black;
      position: absolute;
      top: 50%;
      transform-origin: 100%;
      transform: rotate(90deg);
      transition: all 0.05s;
      transition-timing-function: cubic-bezier(0.4, 0.61, 0.76, 0.18);
    }

  </style>


  <script>
const secondHand = document.querySelector('.second-hand');
const minHand = document.querySelector('.min-hand');
const hourHand = document.querySelector('.hour-hand');

function setDate() {
  const now = new Date();

  const seconds = now.getSeconds();
  const secondsDegrees = ((seconds / 60) * 360) + 90;
    secondHand.style.transform = `rotate(${secondsDegrees}deg)`;
    console.log(seconds);

  const minutes = now.getMinutes();
  const minsDegrees = ((minutes / 60) * 360) + 90;
    minHand.style.transform = `rotate(${minsDegrees}deg)`;
    console.log(minutes);

  const hours = now.getHours();
  const hoursDegrees = ((hours / 12) * 360) + 90;
    hourHand.style.transform = `(${hoursDegrees}deg)`;
    console.log(hours);
}
  setInterval(setDate, 1000);
  </script>
</body>
</html>
