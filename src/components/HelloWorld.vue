<script setup lang="ts">
defineProps<{ msg: string }>();
const startCamera = async () => {
  try {
    const stream = await navigator.mediaDevices.getUserMedia({
      video: true,
    });
    const videoElement = document.getElementById("camera-preview");
    console.log(videoElement);
    if (videoElement) (videoElement as HTMLVideoElement).srcObject = stream;
  } catch (error) {
    console.error("Error accessing camera:", error);
  }
};
startCamera();
</script>

<template>
  <video class="box" id="camera-preview" autoplay playsinline>
    Click on the Vite and Vue logos to learn more
  </video>
</template>

<style scoped>
.box {
  color: #fff;
  /* background-color: #888; */
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
