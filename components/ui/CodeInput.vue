<script setup>
import {ref, reactive} from 'vue';

const props = defineProps({
  codeLength: {
    type: Number,
    default: 4
  },
  isLoading: {
    type: Boolean,
    default: false
  }
});

const digits = reactive([])
const codeCont = ref(null)

for (let i = 0; i < props.codeLength; i++) {
  digits[i] = null;
}

const isDigitsFull = function () {
  for (const elem of digits) {
    if (elem == null || elem == undefined) {
      return false;
    }
  }
  return true;
}

const emit = defineEmits(['update:code']);

const handleKeyDown = function (event, index) {
  if (event.key !== "Tab" &&
    event.key !== "ArrowRight" &&
    event.key !== "ArrowLeft"
  ) {
    event.preventDefault();
  }

  if (event.key === "Backspace") {
    digits[index] = null;
    if (index !== 0) {
      (codeCont.value.children)[index - 1].focus();
    }
    return;
  }

  if ((new RegExp('^([0-9])$')).test(event.key)) {
    digits[index] = event.key;
    if (index !== props.codeLength - 1) {
      (codeCont.value.children)[index + 1].focus();
    }
    if (isDigitsFull()) {
      emit('update:code', digits.join(''))
    }
  }
}
</script>

<template>
  <div ref="codeCont" class="flex space-x-4 justify-center">
    <input
      type="number"
      v-for="(el, ind) in digits"
      :key="el+ind"
      v-model="digits[ind]"
      :autofocus="ind === 0"
      placeholder="*"
      @keydown="handleKeyDown($event, ind)"
      oninput="javascript: if (this.value.length > this.maxLength) this.value = this.value.slice(0, this.maxLength);"
      class="relative block w-12 disabled:cursor-not-allowed disabled:opacity-75 focus:outline-none border-0 form-input rounded-md placeholder-gray-400 dark:placeholder-gray-500 text-3xl text-center shadow-sm bg-gray-50 dark:bg-gray-800 text-gray-900 dark:text-white ring-1 ring-inset ring-gray-300 dark:ring-gray-700 focus:ring-2 focus:ring-primary-500 dark:focus:ring-primary-400"
      maxlength="1"
      :disabled="isLoading"
    />
  </div>
  <ui-loading :is-loading="isLoading"/>
</template>

<style scoped>
input[type="number"]::-webkit-outer-spin-button,
input[type="number"]::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type="number"] {
  -moz-appearance: textfield;
}
</style>
