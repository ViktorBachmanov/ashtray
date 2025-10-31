<script setup>
const designPictures = [
  // { title: 'Опорная кривая', src: '/images/d1.jpg' },
  // { title: 'Опорные кривые', src: '/images/d2.jpg' },
  { title: '3D-модель:', src: '/images/d7.jpg' },
  { title: 'Опорные кривые:', src: '/images/d3.jpg', top: 850, left: 2000, height: 2000 },
  { title: 'Поверхность:', src: '/images/d4.jpg', top: 850, left: 2000, height: 2000  },
  { title: 'Зеркальная копия:', src: '/images/d5.jpg', top: 850, left: 2000, height: 2000 },
  { title: 'Готовая опорная поверхность:', src: '/images/d6.jpg', top: 700, left: 1300},
]

</script>

<template>
  <UApp>
    <UColorModeButton class="fixed top-4 right-4" />

    <main class="mt-10 max-w-fit mx-auto pb-28">
      <h1
        class="text-2xl font-medium text-center mb-5"
      >
        Изделие «Пепельница»
      </h1>    
       
      <table class="m-8">
        <tbody>
          <tr>
            <td class="text-right">Автор:</td>
            <td>Бачманов Виктор</td>
          </tr>
          <tr>
            <td>Материал:</td>
            <td>алюминий</td>
          </tr>
        </tbody>
      </table>

      <DesignPicture
        v-for="designPicture in designPictures"
        :key="designPicture.src"
        :src="designPicture.src"
        :name="designPicture.title"
        :top="designPicture.top"
        :left="designPicture.left"
        :height="designPicture.height"
        class="my-6"
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
      
      </main>
  </UApp>
</template>

<style scoped>
td {
  padding: 0.25em;
}
</style>