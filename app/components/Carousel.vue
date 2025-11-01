<script setup>
const designPictures = [
  { title: '3D-модель:', src: '/images/14.jpg' },
  { title: 'Опорные кривые:', src: '/images/3.jpg' },
  { title: 'Поверхность:', src: '/images/4.jpg' },
  { title: 'Зеркальная копия:', src: '/images/5.jpg' },
  { title: 'Готовая опорная поверхность:', src: '/images/9.jpg' },
]

const curPicIndex = ref(1)

function setPicIndex(val) {
  curPicIndex.value = val
}

const curSrc = ref('')
// const prevSrc = ref('')
const nextSrc = ref('')

const secondOpacity = ref(0)

function toggleSecondOpacity() {
  secondOpacity.value = Math.abs(secondOpacity.value - 1)
}

const img = useImage()

function getSrc(index) {
  const image = new Image()
  console.log('Image:', image);
  console.log('index:', index);

  image.onload = function () {
    console.log('Image loaded successfully!');
  }

  const modifiers = {
    extract: `${designPictures[index].left ?? 200}_${designPictures[index].top ?? 50}_800_${designPictures[index].height ?? 750}`,
    // width: 1100,
    // height: 859,
  }

  const options = {
    width: 1100,
    height: 859,
  }

  image.src = img(designPictures[index].src, modifiers)

  return image.src
} 


watch(curPicIndex, newIndex => {
  let prevIndex = newIndex - 1
  if(prevIndex < 0) {
    prevIndex = designPictures.length - 1
  }
  let nextIndex = newIndex + 1
  if(nextIndex > designPictures.length - 1) {
    nextIndex = 0
  }

  curSrc.value = getSrc(newIndex)
  nextSrc.value = getSrc(nextIndex)

  toggleSecondOpacity()
})

let intervalId

onMounted(() => {
  curPicIndex.value = 0

  // intervalId = setInterval(() => {
  //   let nextPicIndex = curPicIndex.value + 1
  //   if(nextPicIndex > designPictures.length - 1) {
  //     clearInterval(intervalId)
  //     return 
  //   }
  //   setPicIndex(nextPicIndex)
  // }, 3000)
})

// onUnmounted(() => clearInterval(intervalId))

function handleNextPic() {
  if(isLastIndex()) return

  curPicIndex.value++
}

function isLastIndex() {
  return curPicIndex.value === designPictures.length - 1
}
</script>

<template>
  <div
    class="relative"
  >
    <DesignPicture
      :src="curSrc"
    />

    <DesignPicture
      :src="nextSrc"
      class="absolute inset-0 op"
      :style="{ opacity: secondOpacity }"
    />
  </div>

  <UButton
    @click="handleNextPic"
  >Next</UButton>

</template>

<style scoped>
.op {
  transition: opacity 0.5s ease
}
</style>