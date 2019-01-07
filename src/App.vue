<template>
  <div class="whackamole">
    <h1 class="logo">
      Whack-a-mole!
    </h1>
    <button
      class="start-game"
      :disabled="isGameActive"
      @click="startGame"
    >
      Start Game
    </button>
    <div class="counters-container">
      <CounterItem
        title="Score:"
        :counter="score"
      />
      <CounterItem
        title="High Score:"
        :counter="highScore"
      />
      <CounterItem
        title="Timer:"
        :counter="time"
      />
    </div>
    <MoleList :is-game-active="isGameActive">
      <MoleListItem
        v-for="(mole, index) in moles"
        :key="index"
        :is-active="mole" 
        @whack="whackMole(index)"
      />
    </MoleList>
  </div>
</template>

<script>
import CounterItem from './components/CounterItem.vue';
import MoleList from './components/MoleList.vue';
import MoleListItem from './components/MoleListItem.vue';
import getIndex from './mixins/util/getIndex.js';

export default {
  name: 'App',
  components: {
    CounterItem,
    MoleList,
    MoleListItem,
  },
  mixins: [getIndex],
  data: function() {
    return {
      score: 0,
      highScore: 0,
      time: 0,
      isGameActive: false,
      gameIntervId: null,
      moleActiveIntervId: null,
      moleinactiveIntervId: null,
      moles: [false, false, false, false]
    };
  },
  methods: {
    startGame: function() {
      this.isGameActive = true;
      this.time = 20;
      this.startTimer();
      this.startMoles();
    },
    endGame: function() {
      this.stopMoles();
      this.moles = [false, false, false, false];
      this.stopTimer();
      if (this.score > this.highScore) {
        this.highScore = this.score;
      }
      this.score = 0;
      this.isGameActive = false;
    },
    countDownTime: function() {
      if (this.time === 0) {
        this.endGame();
      } else {
        this.time = this.time - 1;
      }
    },
    startTimer: function() {
      this.gameIntervId = setInterval(this.countDownTime, 1000);
    },
    stopTimer: function() {
      clearInterval(this.gameIntervId);
    },
    whackMole: function(index) {
      this.score += 1;
      this.moles[index] = false;
    },
    activeRandomMole: function() {
      const moleIndex = this.getIndex(this.moles.length);
      this.moles[moleIndex] = true;
    },
    inactiveRandomMole: function() {
      const moleIndex = this.getIndex(this.moles.length);
      this.moles[moleIndex] = false;
    },
    startMoles: function() {
      this.moleActiveIntervId = setInterval(this.activeRandomMole, 500);
      this.moleinactiveIntervId = setInterval(this.inactiveRandomMole, 1000);
    },
    stopMoles: function() {
      clearInterval(this.moleActiveIntervId);
      clearInterval(this.moleinactiveIntervId);
    }
  },
};
</script>

<style>
.whackamole {
  font-family: 'Bungee', sans-serif;
  max-width: 960px;
  margin: auto;
  text-align: center;
}

.start-game {
  font-family: 'Bungee', sans-serif;
  padding: 20px;
  border-radius: 3px;
  border: 0;
  background-color: #52b1d6;
  color: #fff;
  font-size: 1em;
  cursor: pointer;
}

.counters-container {
  display: flex;
  justify-content: space-evenly;
}
</style>
