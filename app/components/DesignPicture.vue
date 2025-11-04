<script setup>
const props = defineProps({
  src: String,
  name: String,
  left: {
    type: Number,
    default: 260,
  },
  top: {
    type: Number,
    default: 0,
  },
  height: {
    type: Number,
    default: 850,
  },
})

const emit = defineEmits(['loaded'])

function handleOnload() {
  emit('loaded')
}
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
        extract: `${props.left}_${props.top}_700_${props.height}`
      }"
      width="700"
      height="620"
      sizes="90vw sm:700px"
      class="max-w-full max-h-[90vh] object-contain mx-auto border-emerald-600 border"
      format="webp"
      @load="handleOnload"
    />
  </div>
</template>