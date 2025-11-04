<script setup>
const origin = import.meta.env.VITE_ORIGIN

const isWorkDomain = origin === 'https://ashtray.cnc-op.ru' 

useHead({
  meta: [
    isWorkDomain ? { name: 'yandex-verification', content: 'cdd397d6fd8a12b1' } : { },
  ]
})
</script>

<template>
  <UApp>
    <main class="max-v-[100vw] md:max-w-[1000px] mx-auto pb-14 mt-4">
      <div class="flex justify-end min-h-10">
        <UColorModeButton class="mt-2 mr-4" />
      </div>

      <h1
        class="text-3xl font-medium text-center leading-12 mb-4 sm:mb-8 -mt-4"
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
            width="700"
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

          <NuxtLink
            to="/_ipx/extract_800_480_2300_1640&w_2300&f_webp/images/photo.jpg"
            target="_blank"
          >
            <NuxtImg
              src="/images/photo.jpg"
              :modifiers="{
                extract: '800_480_2300_1640'
              }"
              width="3800"
              sizes="90vw sm:700"
              class="sm:w-[700px] mx-auto max-h-screen object-contain"
              format="webp"
              alt="Фото"
              loading="lazy"
            />
          </NuxtLink>
        </div>
      </section>
      
      </main>

      <footer class="flex flex-col items-center border-t-1 border-gray-300 pt-10 pb-16">
        <div class="flex items-center">
          <!-- <table>          
            <tbody>
              <tr>
                <td>Дизайн <span class="whitespace-nowrap">3D-модели</span></td>
              </tr>
              <tr>
                <td>Программирование ЧПУ</td>
              </tr>
              <tr>
                <td>Фрезеровка на станке <span class="whitespace-nowrap">AWEA</span></td>
              </tr>
            </tbody>
          </table> -->
          <ul>
            <li>Дизайн <span class="whitespace-nowrap">3D-модели</span></li>
            <li>ЧПУ - программы</li>
            <li>Фрезеровка на станке</li>
          </ul>

          <div class="border border-l-0 min-w-2 ml-3 rounded-tr-lg rounded-br-lg py-3 self-stretch"></div>
          <!-- <div class="-ml-[3px] -mt-[3px] opacity-75">&#9658;</div> -->

          <div class="ml-3">Бачманов В.В.</div>
        </div>

        <div class="text-center mt-8">
          Материал:
          <span class="ml-2">Алюминий</span>
        </div>

      </footer>

      <LazyYandexMetrika
        v-if="isWorkDomain"
      />
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
  padding-right: 0.5em;
  text-align: right;
}

ul {
  text-align: right;
  /* list-style-type: circle; 
  direction: rtl; */
}
</style>