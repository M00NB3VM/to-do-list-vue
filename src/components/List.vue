<script setup>
import { ref } from "vue";

/* VARIABLES */

const input = ref("");
const maxChar = 36;
const time = Math.floor(Date.now() / 1000);
const quests = ref([
  {
    id: time,
    text: "Return books to the library, on time",
    completed: false,
  },
  {
    id: time,
    text: "Feed Paimon",
    completed: true,
  },
]);

/* FUNCTIONS */

function markComplete(quest) {
  quest.completed = !quest.completed;
}

function addQuest() {
  quests.value.push({ id: time, text: input.value, completed: false });
  console.log(input.value.length);
  input.value = "";
}

function removeQuest(quest) {
  quests.value = quests.value.filter((q) => q !== quest);
}
</script>

<template>
  <div class="list">
    <div class="inputfield">
      <input
        type="text"
        v-model="input"
        :maxlength="maxChar"
        placeholder="Write here ..."
      />
    </div>
    <p class="maxChar">Max 36 characters</p>
    <button class="addButton" :disabled="!input.length" @click="addQuest">
      <img class="bigSparkle" src="../assets/sparkle_big.png" alt="sparkle" />
      ADD
      <img
        class="smallSparkle"
        src="../assets/sparkle_small.png"
        alt="sparkle"
      />
    </button>
    <ul>
      <li
        v-for="quest in quests"
        :key="quest.id"
        :class="{ complete: quest.completed }"
      >
        <button
          class="doneButton"
          @click="markComplete(quest)"
          :class="{ completeButton: quest.completed }"
        >
          DONE
        </button>
        {{ quest.text }}
        <button class="removeButton" @click="removeQuest(quest)">X</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.list {
  height: 90vh;
  max-width: 500px;
  margin: 30px 0 30px;
  background-color: rgba(102, 207, 229, 0.5);
  backdrop-filter: blur(5px);
  border-radius: 10px;
  overflow: auto;
  overflow-x: hidden;
  text-align: center;
}

.list::-webkit-scrollbar {
  width: 15px;
}
.list::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  -webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  border-radius: 50px;
}

.list::-webkit-scrollbar-thumb {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
  -webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
  border-radius: 50px;
}

input {
  display: block;
  font-family: "Arima Madurai", cursive;
  height: 80px;
  max-width: 250px;
  margin: 0;
  font-size: 1.5rem;
  background-color: transparent;
  border: none;
}

input:focus,
input:active {
  outline: none;
}

.inputfield {
  min-height: 80px;
  margin: 20px 20px 0 20px;
  padding-left: 100px;
  padding-right: 100px;
  background-image: url(../assets/input.png);
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
}

.maxChar {
  font-family: "Nunito", sans-serif;
  font-size: small;
  color: #555f61;
  text-align: right;
  margin-right: 110px;
}

.addButton {
  cursor: pointer;
  font-family: "Nunito", sans-serif;
  font-size: 1.2rem;
  color: #fffa74;
  margin: 10px;
  padding: 5px 20px;
  background-color: #ff9900;
  border: 2px solid #fffa74;
  border-image: linear-gradient(45deg, #ff9900, #fffa74, #fffa74, #ff9900) 1;
  position: relative;
  box-shadow: 3px 3px 3px 1px rgba(0, 0, 0, 0.3);
}

.bigSparkle {
  width: 25px;
  position: absolute;
  top: -18px;
  right: -10px;
}

.smallSparkle {
  position: absolute;
  bottom: -15px;
  left: -5px;
}

ul {
  margin: 0;
  padding: 0;
}

li {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  min-height: 80px;
  margin: 30px 0;
  padding: 0 120px;
  list-style-type: none;
  font-size: 1.5rem;
  background-image: url(../assets/quest.png);
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
}

.doneButton {
  height: 25px;
  width: auto;
  font-family: "Nunito", sans-serif;
  font-size: 1rem;
  text-align: center;
  line-height: 0;
  color: #fffa74;
  background-color: #ff9900;
  border: 2px solid #fffa74;
  padding: 2px;
  position: absolute;
  top: -16px;
  left: 110px;
}

.removeButton {
  height: 24px;
  width: 25px;
  font-family: "Nunito", sans-serif;
  font-size: 1.2rem;
  text-align: center;
  line-height: 0;
  color: #fffa74;
  background-color: #ff9900;
  border: 2px solid #fffa74;
  padding: 2px;
  position: absolute;
  bottom: -10px;
  right: 110px;
}

.complete {
  background-image: url(../assets/complete.png);
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
  text-decoration: line-through;
}

.completeButton {
  color: #ff9900;
  background-color: #fffa74;
  border: 2px solid #fffa74;
}

/* MEDIA QUERIES */

@media screen and (max-width: 1100px) {
  .list {
    height: 600px;
  }
}
</style>
