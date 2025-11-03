<script setup>
const designPictures = [
  { title: 'Опорные кривые', src: '/images/3.jpg', left: 140, top: 80, height: 700, },
  { title: 'Лоскут-1/8', src: '/images/4.jpg', left: 140, top: 80, height: 700, },
  { title: 'Зеркальная копия', src: '/images/5.jpg', left: 140, top: 60, },
  { title: 'Сшивка', src: '/images/7.jpg', left: 140, top: 60, },
  { title: 'Лоскут-1/4', src: '/images/6.jpg', left: 140, top: 60, },
  { title: '4/4', src: '/images/8.jpg', left: 150, top: 60, },
  { title: 'Сшивка', src: '/images/9.jpg', left: 150, top: 60, },
  { title: 'Опорная поверхность', src: '/images/10.jpg', left: 150, top: 60, },
  { title: 'Отверждение', src: '/images/12.jpg', left: 140, top: 50, },
  { title: 'Каркас', src: '/images/15.jpg' },
  { title: 'Технологические лыски', src: '/images/13.jpg' },
  { title: '3D-модель', src: '/images/14.jpg' },
]

const lastPicIndex = computed(() => designPictures.length - 1)

const curPicIndex = ref(lastPicIndex.value)

const firstPic = ref(designPictures[curPicIndex.value])
const secondPic = ref(designPictures[curPicIndex.value - 1])

// function setPicIndex(val) {
//   curPicIndex.value = val
// }

// const curSrc = ref('')
// const prevSrc = ref('')
// const nextSrc = ref('')

// const secondOpacity = ref(0)

// function toggleSecondOpacity() {
//   secondOpacity.value = secondOpacity.value === 0
//     ? 1
//     : 0
// }

// const img = useImage()

// function getSrc(index) {
//   const image = new Image()
//   console.log('Image:', image);
//   console.log('index:', index);

//   image.onload = function () {
//     console.log('Image loaded successfully!');
//   }

//   const modifiers = {
//     extract: `${designPictures[index].left ?? 200}_${designPictures[index].top ?? 50}_800_${designPictures[index].height ?? 750}`,
//   }

//   const options = {
//     width: 1100,
//     height: 859,
//   }

//   image.src = img(designPictures[index].src, modifiers)

//   return image.src
// } 

let intervalId

let playDirection = 'backward'

onMounted(() => {
  // curPicIndex.value = 0

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
  await new Promise(res => setTimeout(res))  

  if (secondPicVisible.value) {
    firstPic.value = designPictures[curPicIndex.value]
  } else {
    secondPic.value = designPictures[curPicIndex.value]
  }

  await new Promise(res => setTimeout(res))  
  toggleSecondVisibility()
}

async function handleNextPic() {
  if(isLastIndex.value) return

  curPicIndex.value++
  await new Promise(res => setTimeout(res))  

  if(secondPicVisible.value) {
    firstPic.value = designPictures[curPicIndex.value]
  } else {
    secondPic.value = designPictures[curPicIndex.value]
  }

  await new Promise(res => setTimeout(res))  
  toggleSecondVisibility()
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
    />

    <Transition>
      <DesignPicture
        v-if="secondPicVisible"
        :src="secondPic.src"
        :name="secondPic.title"
        :top="secondPic.top"
        :left="secondPic.left"
        :height="secondPic.height"
        class="absolute inset-0"
      />
    </Transition>
  </div>

  <div
    class="mt-2 flex gap-2"
  >
    <UButton
      @click="handlePrevPic"
      :disabled="isFirstIndex"
    >Prev</UButton>

    <UButton
      @click="handleNextPic"
      :disabled="isLastIndex"
    >Next</UButton>

    <UButton
      @click="handleStop"
      :disabled="stopped"
    >Stop</UButton>
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