<template>
  <div class="moles-container gameActive">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'MoleList',
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
