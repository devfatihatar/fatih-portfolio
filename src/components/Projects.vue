<script setup>
import { computed } from "vue";
import { texts } from "../i18n";

const props = defineProps({
  currentLang: {
    type: String,
    default: "tr",
  },
});

const t = computed(() => texts[props.currentLang].projects);
</script>

<template>
  <div>
    <h2 class="text-2xl font-semibold mb-4">{{ t.title }}</h2>

    <div class="grid md:grid-cols-2 gap-4">
      <!-- Futrez -->
      <article
        class="p-4 rounded-xl border bg-white/60 dark:bg-slate-800/60 border-slate-200 dark:border-slate-700 hover:-translate-y-1 hover:shadow-lg transition"
      >
        <h3 class="font-semibold mb-1">{{ t.futrez.title }}</h3>
        <p class="text-sm text-slate-700 dark:text-slate-300 mb-2">
          {{ t.futrez.desc }}
        </p>
        <p class="text-xs text-slate-500 mb-2">
          {{ t.futrez.tech }}
        </p>
        <a href="#" class="text-xs text-sky-600 hover:underline"> GitHub </a>
      </article>

      <!-- CV Website -->
      <article
        class="p-4 rounded-xl border bg-white/60 dark:bg-slate-800/60 border-slate-200 dark:border-slate-700 hover:-translate-y-1 hover:shadow-lg transition"
      >
        <h3 class="font-semibold mb-1">{{ t.cvsite.title }}</h3>
        <p class="text-sm text-slate-700 dark:text-slate-300 mb-2">
          {{ t.cvsite.desc }}
        </p>
        <p class="text-xs text-slate-500 mb-2">
          {{ t.cvsite.tech }}
        </p>
        <a href="#" class="text-xs text-sky-600 hover:underline"> GitHub </a>
      </article>

      <!-- Fatih Bilişim -->
      <article
        class="p-4 rounded-xl border bg-white/60 dark:bg-slate-800/60 border-slate-200 dark:border-slate-700 hover:-translate-y-1 hover:shadow-lg transition"
      >
        <h3 class="font-semibold mb-1">{{ t.fatihb.title }}</h3>
        <p class="text-sm text-slate-700 dark:text-slate-300 mb-2">
          {{ t.fatihb.desc }}
        </p>
        <p class="text-xs text-slate-500 mb-2">
          {{ t.fatihb.tech }}
        </p>
        <a href="#" class="text-xs text-sky-600 hover:underline"> GitHub </a>
      </article>
      <!-- TechStock -->
      <article
        class="p-4 rounded-xl border bg-white/60 dark:bg-slate-800/60 border-slate-200 dark:border-slate-700 hover:-translate-y-1 hover:shadow-lg transition"
      >
        <h3 class="font-semibold mb-1">{{ t.techstock.title }}</h3>
        <p class="text-sm text-slate-700 dark:text-slate-300 mb-2">
          {{ t.techstock.desc }}
        </p>
        <p class="text-xs text-slate-500 mb-2">
          {{ t.techstock.tech }}
        </p>
        <a href="#" class="text-xs text-sky-600 hover:underline"> GitHub </a>
      </article>
    </div>
  </div>
</template>
