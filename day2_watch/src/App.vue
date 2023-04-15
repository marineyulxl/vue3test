<!--
 * @Author: marineyulxl
 * @Date: 2023-04-15 15:03:17
 * @LastEditTime: 2023-04-15 16:20:28
-->
<template>
  <div class="content">
    <video ref="videoRef" :src="url" controls></video>
    <div class="btns">
      <button class="btn" :disabled="speed === 0.5" @click="speed -= 0.5">-0.5</button>
      {{ speed }}
      <button class="btn" :disabled="speed === 3" @click="speed += 0.5">+0.5</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, watchEffect } from 'vue'
const speed = ref<number>(1)
const url = ref<string>('')
const videoRef = ref<HTMLVideoElement | null>(null);

(
  async () => {
  const resolvedUrl = await import('./assets/6B623E34A9C64B4C6811585CE7C7EB54.mp4')
  url.value = resolvedUrl.default
  }
)()
watchEffect(async () => {
  if (videoRef.value) {
      videoRef.value.playbackRate = speed.value
    }
})
</script>

<style scoped>
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 30px;
  row-gap: 20px;
}

video {
  height: 600px;
  width: 700px;
}

</style>