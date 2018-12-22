<template>
  <div class="moles-container gameActive">
    <MoleListItem
     v-for="(mole, index) in moles"
     :key="index"
     :is-active="mole" />
  </div>
</template>

<script>
import MoleListItem from './MoleListItem.vue';

export default {
  name: 'MoleList',
  data: function() {
    return {
      moles: [false, false, false, false]
    };
  },
  components: {
    MoleListItem,
  }
};
</script>

<style>
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
