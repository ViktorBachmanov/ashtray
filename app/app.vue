<script setup>
const designPictures = [
  // { title: 'Опорная кривая', src: '/images/d1.jpg' },
  // { title: 'Опорные кривые', src: '/images/d2.jpg' },
  { title: 'Опорная поверхность', src: '/images/d3.jpg' },
  { title: 'Опорная кривая', src: '/images/d4.jpg' },
  { title: 'Опорная кривая', src: '/images/d5.jpg' },
  { title: 'Опорная кривая', src: '/images/d6.jpg' },
  { title: 'Модель', src: '/images/d7.jpg' },
]

</script>

<template>
  <UApp>
    <UColorModeButton class="fixed top-4 right-4" />

    <div class="max-w-fit mx-auto pb-28">
      <NuxtImg
        v-for="designPicture in designPictures"
        :key="designPicture.src"
        :src="designPicture.src"
        :modifiers="{
          extract: '1400_900_3800_3300'
        }"
        width="3800"
        sizes="90vw sm:500px"
        class="my-1 sm:w-[500px] mx-auto"
        format="webp"
      />

      <video
        width="550"
        height="550"
        muted
        playsinline
        controls
        src="/video/rough.webm"
        class="aspect-square mx-auto"
        poster="/images/rough-poster.png"
      >
      </video>

      <video
        width="550"
        height="550"
        muted
        playsinline
        controls
        src="/video/semi-finish.webm"
        class="aspect-square mx-auto"
        poster="/images/semi-finish-poster.png"
      >
      </video>

      <NuxtImg
        src="/images/IMG_20181117_140947_BURST1.jpg"
        :modifiers="{
          extract: '700_400_2600_1900'
        }"
        width="3800"
        sizes="90vw sm:600px"
        class="my-10 sm:w-[600px]  mx-auto"
        format="webp"
      />
      
    </div>
  </UApp>
</template>
