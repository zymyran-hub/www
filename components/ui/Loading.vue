<script>
export default {
  props: {
    isLoading: {
      type: Boolean,
      required: false,
    },
  },
};
</script>

<template>
  <div class="relative z-50" v-if="isLoading">
    <div class="fixed inset-0 transition-opacity bg-gray-200/75 dark:bg-gray-800/75"></div>
    <div class="fixed inset-0 overflow-y-auto">
      <div class="flex min-h-full items-center justify-center text-center">
        <div class="relative text-left flex flex-col bg-white dark:bg-gray-900 shadow-xl w-28 rounded-lg">
          <div class="px-4 py-5 sm:px-6">
            <div class="relative overflow-hidden flex items-center justify-center h-14">
              <UIcon name="i-ph-arrows-clockwise" class="w-14 h-14 text-gray-500 animate-spin absolute"/>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
