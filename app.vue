<template>
  <div class="flex flex-col gap-11 bg-zinc-800 min-h-screen">
    <!-- navbar -->
    <block-navbar>
      <ui-switch v-model="toggle"/>
    </block-navbar>
    <div class="flex-col container py-6 px-6 items-center">
      <div class="flex justify-center gap-10">
        <div class="flex-col">
          <block-screen />
          <div class="flex justify-center gap-10 py-3 px-3">
            <ui-button @click="runChat"> Start </ui-button>
            <ui-button @click="stopChat"> Stop </ui-button>
          </div>
        </div>
        <block-screen />
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
const runChat = () => {
  console.log('start chat');
};
const stopChat = () => {
  console.log('stop chat');
};
</script>
