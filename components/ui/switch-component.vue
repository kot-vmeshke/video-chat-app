<!-- eslint-disable max-len -->
<template>
  <HeadlessSwitch
    v-model="modelValue"
    :class="modelValue ? 'bg-white' : 'bg-gray-50'"
    class="cursor-pointer duration-200 ease-in-out flex p-1 ring-1 ring-gray-900/5 ring-inset rounded-full transition-colors w-14">
    <span
      aria-hidden="true"
      :class="modelValue ? 'translate-x-3.5' : 'translate-x-0'"
      class="bg-white duration-200 ease-in-out h-6 ring-1 ring-gray-900/5 rounded-full shadow-sm transform transition w-6">
      <img src="../assets/img/moon.svg" alt="moon image" />
    </span>
  </HeadlessSwitch>
</template>

<script setup>
// eslint-disable-next-line import/no-extraneous-dependencies
import { computed } from 'vue';

const props = defineProps({
  modelValue: {
    type: Boolean,
    default: false,
  },
});

const emit = defineEmits(['update:modelValue']);

const modelValue = computed({
  get: () => props.modelValue,
  set: (value) => {
    emit('update:modelValue', value);
  },
});
</script>
