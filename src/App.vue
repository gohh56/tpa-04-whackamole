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
      <Counter title="Score:" v-bind:counter="score"></Counter>
      <Counter title="High Score:" v-bind:counter="highScore"></Counter>
      <Counter title="Timer:" v-bind:counter="time"></Counter>
    </div>
    <div class="moles-container gameActive">
      <MolesContainer v-bind:active="moles[0]"></MolesContainer>
      <MolesContainer v-bind:active="moles[1]"></MolesContainer>
      <MolesContainer v-bind:active="moles[2]"></MolesContainer>
      <MolesContainer v-bind:active="moles[3]"></MolesContainer>
    </div>
  </div>
</template>

<script>
import Counter from './components/Counter.vue';
import MolesContainer from './components/MolesContainer.vue';

export default {
  name: 'App',
  components: {
    Counter,
    MolesContainer,
  },
  data: function() {
    return {
      score: 0,
      highScore: 0,
      time: 0,
      moles: [false, false, false, false],
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

.moles-container {
  margin-top: 20px;
  display: flex;
  justify-content: space-between;
  opacity: 0.5;
  transition: opacity 0.3s ease;
}

.moles-container.game-active {
  opacity: 1;
}
</style>
