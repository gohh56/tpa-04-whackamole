<template>
  <div class="moles-container" :class="checkGameActive">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'MoleList',
  props: {
    isGameActive: {
      type: Boolean,
      required: true
    }
  },
  computed: {
    checkGameActive() {
      return this.isGameActive ? 'game-active' : '';
    }
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
