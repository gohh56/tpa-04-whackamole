<template>
  <div class="whackamole">
    <h1 class="logo">
      Whack-a-mole!
    </h1>
    <button
      class="start-game"
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
