<template>
  <div class="moles-container gameActive">
    <MoleListItem />
    <MoleListItem />
    <MoleListItem />
    <MoleListItem />
  </div>
</template>

<script>
import MoleListItem from './MoleListItem.vue';

export default {
  name: 'MoleList',
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
