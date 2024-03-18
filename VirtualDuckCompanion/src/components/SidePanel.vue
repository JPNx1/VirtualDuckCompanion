<template>
  <div :class="['side-panel', { 'is-hidden': !isVisible }]">
    <!-- Side Panel Content Here -->
  </div>
</template>

<script>
export default {
  props: {
    isVisible: Boolean
  },
  data() {
    return {
      isPanelVisible: true // Panel is visible by default
    }
  },
  methods: {
    togglePanelVisibility() {
      this.isPanelVisible = !this.isPanelVisible
    }
  }
}
</script>

<style scoped>
.side-panel {
  width: 250px; /* Adjust width as needed */
  position: fixed;
  left: 0;
  top: 0;
  bottom: 0;
  transition: transform 0.3s ease-in-out;
  background-color: #f4f4f4; /* Adjust color as needed */
  /* Additional styling here */
}

.is-hidden {
  transform: translateX(-100%);
}
</style>
