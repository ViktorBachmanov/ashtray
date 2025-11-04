<script setup>
const designPictures = [
  { title: 'Опорные кривые', src: '/images/3.jpg', left: 200, top: 90, height: 700, },
  { title: 'Лоскут-1/8', src: '/images/4.jpg', left: 200, top: 90, height: 700, },
  { title: 'Зеркальная копия', src: '/images/5.jpg', left: 200, top: 10, height: 840 },
  { title: 'Сшивка', src: '/images/7.jpg', left: 200, top: 10, height: 840 },
  { title: 'Лоскут-1/4', src: '/images/6.jpg', left: 200, top: 10, height: 840 },
  { title: '4/4', src: '/images/8.jpg', left: 200 },
  { title: 'Сшивка', src: '/images/9.jpg', left: 200 },
  { title: 'Опорная поверхность', src: '/images/10.jpg', left: 200 },
  { title: 'Отверждение', src: '/images/12.jpg', left: 200 },
  { title: 'Каркас', src: '/images/15.jpg' },
  { title: 'Технологические лыски', src: '/images/13.jpg' },
  { title: '3D-модель', src: '/images/14.jpg' },
]

const lastPicIndex = computed(() => designPictures.length - 1)

const curPicIndex = ref(lastPicIndex.value)

const firstPic = ref(designPictures[curPicIndex.value])
const secondPic = ref(designPictures[curPicIndex.value])

let intervalId

let playDirection = 'backward'

onMounted(() => {
  intervalId = setInterval(() => {
    if (isFirstIndex.value) {
      playDirection = 'forward' 
    } else if (isLastIndex.value) {
      playDirection = 'backward' 
    }

    if (playDirection == 'forward' ) {
      handleNextPic()
    } else {
      handlePrevPic()
    }
  }, 3000)
})

onUnmounted(() => clearInterval(intervalId))

const secondPicVisible = ref(false)

async function handlePrevPic() {
  if (isFirstIndex.value) return

  curPicIndex.value--

  if (secondPicVisible.value) {
    firstPic.value = { ...designPictures[curPicIndex.value] }
  } else {
    secondPic.value = { ...designPictures[curPicIndex.value] }
  }
}

async function handleNextPic() {
  if(isLastIndex.value) return

  curPicIndex.value++

  if(secondPicVisible.value) {
    firstPic.value = { ...designPictures[curPicIndex.value] }
  } else {
    secondPic.value = { ...designPictures[curPicIndex.value] }
  }
}

function toggleSecondVisibility() {
  secondPicVisible.value = !secondPicVisible.value
}

const isFirstIndex = computed(() => curPicIndex.value === 0)
const isLastIndex = computed(() => curPicIndex.value === lastPicIndex.value)

const stopped = ref(false)

function handleStop() {
  clearInterval(intervalId)
  stopped.value = true
}

// const secondOpacity = computed(() => secondPicVisible.value ? 1 : 0)

function handleSetStage(index) {
  setStage(index)
}

function setStage(index) {
  curPicIndex.value = index
  if(secondPicVisible.value) {
    firstPic.value = { ...designPictures[index] }
  } else {
    secondPic.value = { ...designPictures[index] }
  }
}
</script>

<template>
  <div
    class="relative"
  >
    <DesignPicture
      :src="firstPic.src"
      :name="firstPic.title"
      :top="firstPic.top"
      :left="firstPic.left"
      :height="firstPic.height"
      @loaded="toggleSecondVisibility"
      :key="firstPic"
    />

    <Transition>
      <DesignPicture
        v-show="secondPicVisible"
        :src="secondPic.src"
        :name="secondPic.title"
        :top="secondPic.top"
        :left="secondPic.left"
        :height="secondPic.height"
        class="absolute inset-0 "
        @loaded="toggleSecondVisibility"
        :key="secondPic"
      />
    </Transition>
  </div>

  <div
    class="mt-2 flex gap-2 items-center"
  >
    <IconChevronDeg
      @click="handlePrevPic"
      :disabled="isFirstIndex"
      :angle="180"
      class="text-[#05df72]"
    />

    <IconStop
      @click="handleStop"
      :disabled="stopped"
      class="text-[#05df72] w-12 h-12"
    />

    <IconChevronDeg
      @click="handleNextPic"
      :disabled="isLastIndex"
      class="text-[#05df72]"
    />

    <div
      v-for="(stage, index) in designPictures"
      class="min-h-4 min-w-2 bg-[#05df72] grow cursor-pointer"
      :class="{ 'opacity-25': curPicIndex <= index - 1 }"
      @click="handleSetStage(index)"
    >
    </div>
  </div>

</template>

<style scoped>
/* .op {
  transition: opacity 1s ease;
} */

.v-enter-active,
.v-leave-active {
  transition: opacity 1s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>