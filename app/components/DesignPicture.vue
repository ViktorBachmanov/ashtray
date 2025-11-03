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
  },
  num: Number,
})

const emit = defineEmits(['loaded'])

function handleOnload() {
  // console.log('handleOnload')
  emit('loaded')
}
</script>

<template>
  <div
    class="bg-black"
  >
    <span class="absolute top-2 left-2">{{ num }}</span>
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
      sizes="90vw sm:890px"
      class="max-w-full mx-auto border-emerald-600 border"
      format="webp"
      @load="handleOnload"
    />

    <!-- <img 
      :src 
      width='1100'
      height='859'
    /> -->
  </div>
</template>