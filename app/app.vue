<script setup>
const designPictures = [
  // { title: 'Опорная кривая', src: '/images/d1.jpg' },
  // { title: 'Опорные кривые', src: '/images/d2.jpg' },
  { title: 'Опорные кривые:', src: '/images/d3.jpg', top: 850, left: 2000, height: 2000 },
  { title: 'Поверхность:', src: '/images/d4.jpg', top: 850, left: 2000, height: 2000  },
  { title: 'Зеркальная копия:', src: '/images/d5.jpg', top: 850, left: 2000, height: 2000 },
  { title: 'Готовая опорная поверхность:', src: '/images/d6.jpg', top: 700, left: 1300},
  { title: 'Модель:', src: '/images/d7.jpg' },
]

</script>

<template>
  <UApp>
    <UColorModeButton class="fixed top-4 right-4" />

    <div class="mt-10 max-w-fit mx-auto pb-28">
      <DesignPicture
        v-for="designPicture in designPictures"
        :key="designPicture.src"
        :src="designPicture.src"
        :name="designPicture.title"
        :top="designPicture.top"
        :left="designPicture.left"
        :height="designPicture.height"
        class="my-1"
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
