<script setup>
import { computed } from 'vue'
import { texts } from '../i18n'

const props = defineProps({
  currentLang: {
    type: String,
    default: 'tr',
  },
})

const t = computed(() => texts[props.currentLang].contact)
</script>

<template>
  <div class="space-y-4">
    <h2 class="text-2xl font-semibold mb-2">
      {{ t.title }}
    </h2>

    <p class="text-slate-700 dark:text-slate-300">
      {{ t.desc }}
    </p>

    <ul class="space-y-2 text-sm text-slate-700 dark:text-slate-300">
      <li>
        <span class="font-semibold">{{ t.email }}:</span>
        <a href="mailto:fatih@example.com" class="text-sky-600 hover:underline">
          fatihatardevv@outlook.com
        </a>
      </li>
      <li>
        <span class="font-semibold">{{ t.github }}:</span>
        <a
          href="https://github.com/username"
          target="_blank"
          class="text-sky-600 hover:underline"
        >
          github.com/devfatihatar
        </a>
      </li>
      <li>
        <span class="font-semibold">{{ t.linkedin }}:</span>
        <a><span class="text-slate-500 text-xs">www.linkedin.com/in/fatih-atar-8632a71a9/</span></a>
      </li>
    </ul>
  </div>
</template>
