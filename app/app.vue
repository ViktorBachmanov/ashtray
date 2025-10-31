<script setup>


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
            <td>Алюминий</td>
          </tr>
        </tbody>
      </table>

      <Carousel />

      <video
        width="700"
        height="700"
        muted
        playsinline
        controls
        src="/video/full-1.webm"
        class="aspect-square mx-auto"
        poster="/images/semi-finish-traj.png"
      >
      </video>

      <video
        width="700"
        height="700"
        muted
        playsinline
        controls
        src="/video/semi-finish-traj.webm"
        class="aspect-square mx-auto"
        poster="/images/semi-finish-traj.png"
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