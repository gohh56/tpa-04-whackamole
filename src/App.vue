<template>
  <div class="whackamole">
    <h1 class="logo">
      Whack-a-mole!
    </h1>
    <button
      class="start-game"
      v-on:click="startGame"
    >
      Start Game
    </button>
    <div class="counters-container">
      <CounterItem title="High Score:" :counter="score" />
      <CounterItem title="Score:" :counter="highScore" />
      <CounterItem title="Timer:" :counter="time" />
    </div>
    <MoleList>
      <MoleListItem
        v-for="(mole, index) in moles"
        :key="index"
        :is-active="mole" 
      />
    </MoleList>
  </div>
</template>

<script>
import CounterItem from './components/CounterItem.vue';
import MoleList from './components/MoleList.vue';
import MoleListItem from './components/MoleListItem.vue';

export default {
  name: 'App',
  components: {
    CounterItem,
    MoleList,
    MoleListItem,
  },
  data: function() {
    return {
      score: 0,
      highScore: 0,
      time: 0,
      moles: [false, false, false, true]
    };
  },
  methods: {
    startGame: function() {
      this.time = 20;
      this.startTimer();
    },
    endGame: function() {
      this.stopTimer();
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
