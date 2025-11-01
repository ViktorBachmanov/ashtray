<script setup>


</script>

<template>
  <UApp>
    <UColorModeButton class="fixed top-4 right-4" />

    <main class="pt-20 max-w-fit mx-auto pb-28">
      <h1
        class="text-3xl font-medium text-center leading-12 mb-10"
      >
        Пепельница<br>«Юбилейная»
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
        <div class="max-w-[890px]">
          <h2 class="text-2xl font-medium indent-3 mb-4">
            Дизайн и построение 3D-модели
          </h2>

          <Carousel 
          />
        </div>

        <div>
          <h2 class="text-2xl font-medium indent-3 mb-4">
            Симуляция черновой и получистовой фрезеровок
          </h2>

          <video
            width="890"
            muted
            playsinline
            controls
            src="/video/set-10.webm"
            class="mx-auto"
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

        <div>
          <h2 class="text-2xl font-medium indent-3 mb-4">
            Готовое изделие
          </h2>

          <NuxtImg
            src="/images/IMG_20181117_140947_BURST1.jpg"
            :modifiers="{
              extract: '700_400_2600_1900'
            }"
            width="3800"
            sizes="90vw sm:890"
            class="sm:w-[890px] mx-auto"
            format="webp"
            alt="Фото"
          />
        </div>
      </section>
      
      </main>

      <footer class="flex flex-col items-center border-t-1 border-gray-300 pt-12 pb-16">
        <table>
          <caption  class="text-center text-xl font-medium tracking-wide pb-5 pl-16">
            В ролях:
          </caption>
          
          <tbody>
            <tr>
              <td>Дизайн и построение 3D-модели</td>
              <td>Бачманов</td>
            </tr>
            <tr>
              <td>Технология и программирование ЧПУ</td>
              <td>Виктор</td>
            </tr>
            <tr>
              <td>Фрезеровка на станке MiniMill</td>
              <td>Владимирович</td>
            </tr>
            <tr>
              <td></td>
              <td></td>
            </tr>
            <tr>
              <td>Материал</td>
              <td>Алюминий</td>
            </tr>
          </tbody>
        </table>

      </footer>
  </UApp>
</template>

<style scoped>
th {
  padding: 0.5em;
}

td {
  padding: 0.33em;
}

th:first-child, td:first-child {
  padding-right: 1em;
  text-align: right;
}
</style>