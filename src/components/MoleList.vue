<template>
  <div class="moles-container gameActive">
    <MoleListItem :isActive="moles[0]" />
    <MoleListItem :isActive="moles[1]" />
    <MoleListItem :isActive="moles[2]" />
    <MoleListItem :isActive="moles[3]" />
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
