<script setup>
import List from "./components/List.vue";
</script>

<template>
  <div class="main">
    <div class="flex">
      <div class="img">
        <img class="paimonimg" alt="Paimon" src="./assets/paimon.png" />
      </div>
      <p class="paimon">Paimon</p>
      <img class="line" alt="decor line" src="./assets/line.png" />
      <p class="welcome">
        Welcome, traveler! We have a lot to do. <br />
        Add your quests to the list and let's go on an adventure.
      </p>
    </div>
    <div>
      <List></List>
    </div>
  </div>
</template>

<style>
/* Fonts : 
font-family: 'Arima Madurai', cursive;
font-family: 'Nunito', sans-serif;
*/

@import url("https://fonts.googleapis.com/css2?family=Arima+Madurai:wght@900&family=Nunito:wght@700&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Arima Madurai", cursive;
  font-size: 1.8rem;
  line-height: 110%;
  min-height: 100vh;
  width: 100%;
  background-image: url(./assets/genshin-impact-wp.jpg);
  background-repeat: no-repeat;
  background-size: cover;
}

.main {
  width: 90%;
  margin-left: auto;
  margin-right: auto;
  display: flex;
  justify-content: space-between;
}

.img {
  height: 70vh;
  width: auto;
  margin: 20px 0 20px 0;
  padding: 20px;
}

.paimonimg {
  height: 100%;
  width: auto;
  animation-name: float;
  animation-duration: 20s;
  animation-iteration-count: infinite;
  animation-timing-function: ease-in-out;
}

@keyframes float {
  from {
    transform: translate(0, 0);
  }
  25% {
    transform: translate(40px, 40px);
  }
  50% {
    transform: translate(0, 0);
  }
  75% {
    transform: translate(-40px, 40px);
  }
  to {
    transform: translate(0, 0);
  }
}

.paimon {
  color: #ff9900;
  text-align: center;
  -webkit-text-stroke: 1px black;
  text-shadow: 0 0 3px #000000;
}

.line {
  display: block;
  width: 90%;
  margin: 10px auto;
}

.welcome {
  margin: 0;
  padding: 0;
  text-align: center;
  color: white;
  -webkit-text-stroke: 1px black;
  text-shadow: 1px 1px 3px #000000;
}

/* MEDIA QUERIES */

@media screen and (max-width: 1100px) {
  body {
    width: 100%;
    background-image: url(./assets/genshin-impact-wp-small.jpg);
    background-repeat: no-repeat;
    background-size: cover;
  }

  .main {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .img {
    height: 400px;
    width: auto;
  }
}
</style>
