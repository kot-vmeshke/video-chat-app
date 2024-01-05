<!-- eslint-disable max-len -->
<template>
  <div class="flex flex-col gap-11 bg-zinc-800 min-h-screen">
    <!-- navbar -->
    <block-navbar>
      <ui-switch v-model="toggle" />
    </block-navbar>
    <div class="max-w-7xl w-full my-0 mx-auto px-8 flex flex-col gap-10 py-10">
      <div class="flex justify-between gap-4">
        <block-screen>
          <video
            :srcObject="videoSrc"
            autoplay
            id="localVideo"
            class="block w-full h-full object-cover"></video>
        </block-screen>
        <block-screen />
      </div>
      <div class="flex justify-center items-center gap-4">
        <ui-button
          @click="runChat"
          class="text-zinc-50 bg-green-700 text-lg p-4 w-full max-w-xs">
          Start
        </ui-button>
        <ui-button
          @click="stopChat"
          class="text-zinc-50 bg-red-700 text-lg p-4 w-full max-w-xs"
          :class="isConnected ? '' : 'hidden'">
          Stop
        </ui-button>
      </div>
    </div>
  </div>
</template>

<script setup>
// eslint-disable-next-line import/no-extraneous-dependencies
import { ref } from 'vue';
// const toggle = () => {
//   console.log('toggle');
// };
const toggle = ref(true);

const isConnected = ref(false);

const videoSrc = ref(null);
let mediaStream;

const runChat = () => {
  navigator.mediaDevices
    .getUserMedia({
      video: true,
      // audio: true,
    })
    .then((stream) => {
      videoSrc.value = stream;
      mediaStream = stream;
      isConnected.value = true;
    });
};
const stopChat = () => {
  const tracks = mediaStream.getTracks();
  tracks.forEach((track) => {
    track.stop(); // Остановить каждый трек
  });
  videoSrc.value = null;
  isConnected.value = false;
};
</script>
