<template>
  <footer
    class="border-t mt-16 py-6 text-center text-xs text-slate-500 dark:text-slate-400
           border-slate-200 dark:border-slate-700"
  >
    <p>
      © {{ year }} — <span class="font-semibold text-slate-700 dark:text-slate-200">Fatih Atar</span>
    </p>
    <p class="mt-1">
      {{ currentLang === 'tr'
        ? 'Bu portföy Vue.js + Tailwind CSS kullanılarak oluşturulmuştur.'
        : 'This portfolio was built using Vue.js + Tailwind CSS.' }}
    </p>
  </footer>
</template>

<script setup>
const props = defineProps({
  currentLang: {
    type: String,
    default: 'tr',
  },
})

const year = new Date().getFullYear()
</script>
