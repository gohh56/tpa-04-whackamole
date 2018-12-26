<template>
  <div class="mole-container" :class="checkActive">
    <div class="mole-image-container">
      <img class="mole" src="../assets/mole.png" alt="mole"/>
    </div>
    <img class="dirt" src="../assets/dirt.svg" alt="mole dirt"/>
  </div>
</template>

<script>
export default {
  name: 'MoleListItem',
  props: {
    isActive: {
      type: Boolean,
      required: true
    }
  },
  computed: {
    checkActive() {
      return this.isActive ? 'active' : 'inactive';
    }
  },
};
</script>

<style scoped>
.mole-container {
  width: 160px;
  height: 160px;
  display: inline-block;
  margin: 10px;
  position: relative;
}

.mole-image-container {
  overflow: hidden;
  width: 160px;
  height: 140px;
}

.mole-container img {
  display: block;
  transition: all 0.3s ease;
}

.mole {
  position: relative;
  width: 60%;
  margin: auto;
  cursor: pointer;
}

.mole-container.active .mole {
  /* display: block; */
  top: 0px;
}

.mole-container.inactive .mole {
  top: 200px;
}

.dirt {
  width: 100%;
  margin: auto;
  z-index: 1;
  position: absolute;
  bottom: 0;
}
</style>
