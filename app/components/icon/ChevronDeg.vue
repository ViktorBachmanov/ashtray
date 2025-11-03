<script setup>
const props = defineProps({
  angle: {
    type: Number,
    default: 0, // right
  },
  disabled: {
    type: Boolean,
    default: false,
  }
})
</script>

<template>
  <svg 
    xmlns="http://www.w3.org/2000/svg" 
    fill="none" 
    viewBox="0 0 12 24" 
    stroke-width="4" 
    stroke="currentColor"
    :class="{ disabled: disabled }" 
    :style="{ transform: `rotateZ(${angle}deg)` }"
  >
    <path d="M2,2 L10,12 L2,22" stroke-linecap="round" stroke-linejoin="round"/>
  </svg>
</template>

<style scoped>
svg {
  cursor: pointer;
  width: 24px;
}

svg.disabled {
  cursor: default;
  opacity: 0.5;
  pointer-events: none;
}
</style>