<script setup>
const props = defineProps({
  src: String,
  name: String,
  left: {
    type: Number,
    default: 200,
  },
  top: {
    type: Number,
    default: 50,
  },
  height: {
    type: Number,
    default: 750,
  }
})
</script>

<template>
  <div
    class="bg-black"
  >
    <div
      class="text-white p-2 absolute right-2 bottom-2"
    >
      {{ name }}
    </div>

    <NuxtImg
      :src
      :modifiers="{
        extract: `${props.left}_${props.top}_800_${props.height}`
      }"
      width="1100"
      height="859"
      sizes="90vw sm:800px"
      class="max-w-full mx-auto border-emerald-600 border"
      format="webp"
    />

    <!-- <img 
      :src 
      width='1100'
      height='859'
    /> -->
  </div>
</template>