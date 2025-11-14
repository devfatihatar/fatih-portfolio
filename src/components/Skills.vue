<script setup>
import { computed } from "vue";
import { texts } from "../i18n";

const props = defineProps({
  currentLang: {
    type: String,
    default: "tr",
  },
});

const t = computed(() => texts[props.currentLang].skills);
</script>

<template>
  <div>
    <h2 class="text-2xl font-semibold mb-4">{{ t.title }}</h2>

    <div class="grid md:grid-cols-3 gap-4 text-sm">
      <div
        class="p-4 rounded-xl border bg-white/60 dark:bg-slate-800/60 border-slate-200 dark:border-slate-700 hover:-translate-y-1 hover:shadow-lg transition"
      >
        <h3 class="font-semibold mb-2">{{ t.frontend }}</h3>
        <ul class="space-y-1 text-slate-700 dark:text-slate-300">
          <li>HTML / CSS</li>
          <li>JavaScript (ES6+)</li>
          <li>Vue.js (temel / orta)</li>
          <li>React (başlangıç)</li>
          <li>TypeScript (öğreniyorum)</li>
        </ul>
      </div>

      <div
        class="p-4 rounded-xl border bg-white/60 dark:bg-slate-800/60 border-slate-200 dark:border-slate-700 hover:-translate-y-1 hover:shadow-lg transition"
      >
        <h3 class="font-semibold mb-2">{{ t.backend }}</h3>
        <ul class="space-y-1 text-slate-700 dark:text-slate-300">
          <li>.NET C# (temel)</li>
          <li>PHP / MySQL (temel)</li>
          <li>Veri tabanı mantığı</li>
        </ul>
      </div>

      <div
        class="p-4 rounded-xl border bg-white/60 dark:bg-slate-800/60 border-slate-200 dark:border-slate-700 hover:-translate-y-1 hover:shadow-lg transition"
      >
        <h3 class="font-semibold mb-2">{{ t.tools }}</h3>
        <ul class="space-y-1 text-slate-700 dark:text-slate-300">
          <li>Git & GitHub</li>
          <li>VS Code</li>
        </ul>
      </div>
    </div>
  </div>
</template>
