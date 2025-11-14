<script setup>
import { computed } from 'vue'
import { texts } from '../i18n'

const props = defineProps({
  currentLang: {
    type: String,
    default: 'tr',
  },
})

const t = computed(() => texts[props.currentLang].about)
</script>

<template>
  <div class="space-y-4">
    <h2 class="text-2xl font-semibold mb-2">
      {{ t.title }}
    </h2>

    <p class="text-slate-700 dark:text-slate-300">
      {{ t.p1 }}
    </p>

    <p class="text-slate-700 dark:text-slate-300">
      {{ t.p2 }}
    </p>

    <ul class="list-disc list-inside text-slate-700 dark:text-slate-300 space-y-1">
      <li>{{ t.bullet1 }}</li>
      <li>{{ t.bullet2 }}</li>
      <li>{{ t.bullet3 }}</li>
    </ul>
  </div>
</template>
