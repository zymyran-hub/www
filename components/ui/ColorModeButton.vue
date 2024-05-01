<script setup lang="ts">
const colorMode = useColorMode();

const isDark = computed({
  get() {
    return colorMode.value === "dark";
  },
  set() {
    colorMode.preference = colorMode.value === "dark" ? "light" : "dark";
  }
});
</script>

<template>
  <UButton
    :icon="isDark ? 'i-ph-moon-bold' : 'i-ph-sun-bold'"
    color="gray"
    block
    class="justify-start"
    size="xl"
    @click="isDark = !isDark"
  />
</template>
