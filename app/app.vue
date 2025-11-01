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
       
      <!-- <table class="m-8">
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
      </table> -->

      <section
        class="flex flex-wrap justify-center max-w-[90vw] gap-10"
      >
        <div class="sm:w-[45vw]">
          <h2 class="text-xl font-medium text-center my-2">
            Дизайн
          </h2>

          <Carousel 
          />
        </div>

        <div>
          <h2 class="text-xl font-medium text-center my-2">
            Симуляция черновой и получистовой фрезеровок
          </h2>

          <video
            width="700"
            muted
            playsinline
            controls
            src="/video/full-1.webm"
            class="mx-auto"
            poster="/images/semi-finish-traj.png"
          >
          </video>
        </div>

        <!-- <div>
          <h2 class="text-xl font-medium text-center my-2">
            Траектория получистовой обработки
          </h2>

          <video
            width="700"
            muted
            playsinline
            controls
            src="/video/semi-finish-traj.webm"
            class="mx-auto"
            poster="/images/semi-finish-traj.png"
          >
          </video>
        </div> -->

        <div>
          <h2 class="text-xl font-medium text-center my-2">
            Фото готового изделия
          </h2>

          <NuxtImg
            src="/images/IMG_20181117_140947_BURST1.jpg"
            :modifiers="{
              extract: '700_400_2600_1900'
            }"
            width="3800"
            sizes="90vw sm:800px"
            class="sm:w-[800px] mx-auto"
            format="webp"
            alt="Фото"
          />
        </div>
      </section>
      
      </main>
  </UApp>
</template>

<style scoped>
td {
  padding: 0.25em;
}
</style>