<script setup lang="ts">
const q = ref("");
</script>

<template>
  <div class="flex flex-col pt-20 -mt-20">
    <div class="mt-8 pb-24">
      <div class="flex items-center justify-between gap-3 mb-8">
        <UInput
          v-model="q"
          icon="i-ph-magnifying-glass-duotone"
          placeholder="Search..."
          class="w-56"
          size="md"
          autocomplete="off"
          :ui="{ icon: { trailing: { pointer: '' } } }"
        >
          <template #trailing>
            <UButton
              v-if="q"
              color="gray"
              variant="link"
              size="xs"
              icon="i-ph-x"
              :padded="false"
            />
            <UKbd v-else>
              /
            </UKbd>
          </template>
        </UInput>

        <UButtonGroup>
          <USelectMenu
            size="md"
            color="white"
            class="w-32"
          />
        </UButtonGroup>
      </div>
      <div class="grid lg:grid-cols-3 xl:grid-cols-4 grid-cols-1 gap-4">
        <div class="p-4 h-64 rounded-lg shadow-lg bg-indigo-300"></div>
        <div class="p-4 h-64 rounded-lg shadow-lg bg-indigo-300"></div>
        <div class="p-4 h-64 rounded-lg shadow-lg bg-indigo-300"></div>
        <div class="p-4 h-64 rounded-lg shadow-lg bg-indigo-300"></div>
        <div class="p-4 h-64 rounded-lg shadow-lg bg-indigo-300"></div>
        <div class="p-4 h-64 rounded-lg shadow-lg bg-indigo-300"></div>
        <div class="p-4 h-64 rounded-lg shadow-lg bg-indigo-300"></div>
        <div class="p-4 h-64 rounded-lg shadow-lg bg-indigo-300"></div>
      </div>
    </div>
  </div>
</template>
