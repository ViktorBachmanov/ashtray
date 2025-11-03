<script setup>


</script>

<template>
  <UApp>
    <main class="max-v-[100vw] md:max-w-[1000px] mx-auto pb-16 mt-4">
      <div class="flex justify-end min-h-10">
        <UColorModeButton class="mt-2 mr-4" />
      </div>

      <h1
        class="text-3xl font-medium text-center leading-12 mb-8 -mt-4"
      >
        Пепельница
      </h1>    

      <section
        class="flex flex-col items-center gap-10 px-2"
      >
        <div class="max-w-[890px] drop-shadow-2xl  rounded-t-xl">
          <h2 class="text-xl sm:text-2xl font-medium indent-3 p-2">
            Дизайн и построение <span class="whitespace-nowrap">3D-модели</span>
          </h2>

          <Carousel />
        </div>

        <div class="shadow-2xl  rounded-t-xl ">
          <h2 class="text-xl sm:text-2xl font-medium indent-3 p-2">
            Симуляция черновой и получистовой обработки
          </h2>

          <video
            width="890"
            muted
            playsinline
            controls
            src="/video/set-10.webm"
            class="mx-auto max-h-screen"
            poster="/images/mach-poster-2.png"
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

        <div class="shadow-2xl rounded-t-xl">
          <h2 class="text-xl sm:text-2xl font-medium indent-3 my-4 ">
            Готовое изделие
          </h2>

          <NuxtImg
            src="/images/photo.jpg"
            :modifiers="{
              extract: '800_480_2300_1640'
            }"
            width="3800"
            sizes="90vw sm:890"
            class="sm:w-[890px] mx-auto max-h-screen"
            format="webp"
            alt="Фото"
            loading="lazy"
          />
        </div>
      </section>
      
      </main>

      <footer class="flex flex-col items-center border-t-1 border-gray-300 pt-12 pb-16">
        <table>          
          <tbody>
            <tr>
              <td>Дизайн <span class="whitespace-nowrap">3D-модели</span></td>
              <td>Бачманов</td>
            </tr>
            <tr>
              <td>Программирование ЧПУ</td>
              <td>Виктор</td>
            </tr>
            <tr>
              <td>Фрезеровка на станке <span class="whitespace-nowrap">AWEA</span></td>
              <td>Владимирович</td>
            </tr>
          </tbody>
        </table>

        <div class="text-center mt-8">
          Материал
          <span class="ml-4">Алюминий</span>
        </div>

      </footer>
  </UApp>
</template>

<style scoped>
th {
  padding: 0.5em;
}

td {
  padding: 0.2em;
}

th:first-child, td:first-child {
  padding-right: 1em;
  text-align: right;
}
</style>