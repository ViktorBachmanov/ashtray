<script setup>
const props = defineProps({
  src: String,
  name: String,
  top: {
    type: Number,
    default: 900,
  },
  left: {
    type: Number,
    default: 1400,
  },
  height: {
    type: Number,
    default: 3300,
  }
})
</script>

<template>
  <div>
    <div
      class="text-center mb-2"
    >
      {{ name }}
    </div>

    <NuxtImg
      :src
      :modifiers="{
        extract: `${props.left}_${props.top}_3800_${props.height}`
      }"
      width="3800"
      height="3300"
      sizes="90vw sm:500px"
      class="sm:w-[500px] mx-auto"
      format="webp"
    />
  </div>
</template>