<template>
  <div class="mx-auto px-4 max-w-5xl select-none">
    <header class="flex flex-wrap items-center justify-between mx-auto py-2">
      <div class="flex items-center space-x-2">
        <nuxt-link to="/">
          <span class="self-center text-2xl font-bold whitespace-nowrap dark:text-white">Zymyran</span>
        </nuxt-link>
      </div>
      <div class="flex rounded-lg bg-gray-50 flex-row space-x-2">
        <u-button size="md" color="black" variant="solid" label="Войти"/>
      </div>
    </header>
    <slot/>
    <footer class="py-8 text-xs">
      <div class="sm:flex sm:items-center sm:justify-between">
        <div class="flex flex-col sm:w-3/12">
        <span class="text-base">
          8 800 700-93-29
        </span>
          <span class="text-sm text-gray-400">
         Звонок по Казахстану бесплатный
        </span>
        </div>
        <div class="flex sm:w-9/12 mt-4 sm:justify-center sm:mt-0">
        <span class="text-[8px] text-gray-500 dark:text-gray-400">
          Образовательные услуги оказываются АНО ДПО «Образовательные технологии Яндекса» на основании Лицензии №Л035-01298-77/00185314 от 24 марта 2015 года. Документ о прохождении обучения по программе дополнительного профессионального образования также выдается АНО ДПО «Образовательные технологии Яндекса». © 2024 АНО ДПО «Образовательные технологии Яндекса», ООО «Яндекс». Проект компании Яндекс.
        </span>
        </div>
      </div>
    </footer>
  </div>
  <lazy-dev-only>
    <div class="fixed bottom-4 right-4">
      <ui-color-mode-button/>
    </div>
  </lazy-dev-only>
</template>
<script setup lang="ts">
</script>
