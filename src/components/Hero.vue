<script setup>
import { computed } from "vue";
import { texts } from "../i18n";

const props = defineProps({
  currentLang: {
    type: String,
    default: "tr",
  },
});

const t = computed(() => texts[props.currentLang].hero);
</script>

<template>
  <!-- Dış sarmal: arka plan şekilleri için relative -->
  <section class="relative overflow-hidden">
    <!-- Blur / gradient şekiller (arka plan) -->
    <div
      class="pointer-events-none absolute -top-40 -right-32 w-[500px] h-[500px] bg-sky-500/30 dark:bg-sky-400/20 rounded-[40%_60%_70%_30%/30%_40%_60%_70%] blur-[200px]"
    ></div>

    <div
      class="pointer-events-none absolute bottom-[-180px] -left-40 w-[550px] h-[550px] bg-purple-500/25 dark:bg-purple-400/15 rounded-[60%_30%_50%_40%/40%_60%_30%_60%] blur-[220px]"
    ></div>

    <!-- İçerik -->
    <div
      class="relative flex flex-col md:flex-row items-center gap-10 py-10 md:py-20"
    >
      <!-- Sol: Metin alanı -->
      <div
        class="flex-1 space-y-4 p-6 md:p-8 ml-4 md:ml-10 rounded-2xl border bg-white/70 dark:bg-slate-900/70 border-slate-200 dark:border-slate-700 shadow-sm backdrop-blur"
      >
        <p class="text-xs uppercase tracking-[0.25em] text-sky-600">
          {{ t.badge }}
        </p>

        <h1 class="text-3xl md:text-4xl lg:text-5xl font-bold leading-tight">
          {{ t.title }}
          <span class="text-sky-600">{{ t.name }}</span
          >.
        </h1>

        <p
          class="text-slate-600 dark:text-slate-300 max-w-xl text-sm md:text-base"
        >
          {{ t.description }}
        </p>

        <!-- Butonlar -->
        <div class="flex flex-wrap gap-3 mt-4">
          <a
            href="#projects"
            class="px-4 py-2 rounded-full bg-sky-600 text-white text-sm hover:bg-sky-700 transition"
          >
            {{ t.btnProjects }}
          </a>
          <a
            href="#contact"
            class="px-4 py-2 rounded-full border text-sm hover:border-sky-600 hover:text-sky-600 transition"
          >
            {{ t.btnContact }}
          </a>
          <a
            href="/cv-fatih-atar.pdf"
            download
            class="px-4 py-2 rounded-full border text-sm hover:border-emerald-600 hover:text-emerald-600 transition"
          >
            {{ t.btnDownload }}
          </a>
        </div>

        <!-- Küçük ekstra info satırı -->
        <div class="pt-2 text-xs md:text-sm text-slate-500 dark:text-slate-400">
          <span class="inline-flex items-center gap-2">
            <span class="w-2 h-2 rounded-full bg-emerald-500"></span>
            <span>
              {{
                props.currentLang === "tr"
                  ? "Yeni teknolojileri öğrenmeye ve gerçek projelerde sorumluluk almaya hazırım."
                  : "Ready to learn new technologies and take responsibility in real-world projects."
              }}
            </span>
          </span>
        </div>
      </div>

      <!-- Sağ: Görsel / avatar alanı -->
      <div class="flex-1 flex justify-center md:justify-end pr-6 md:pr-12">
        <div class="relative">
          <!-- Dairesel arka plan -->
          <div
            class="w-48 h-48 md:w-64 md:h-64 rounded-full bg-gradient-to-tr from-sky-500 via-indigo-500 to-purple-500 opacity-80 dark:opacity-70 shadow-xl gradient-rotate"
          ></div>

          <!-- Profil fotoğrafı (istersen ekle) -->
          <div
            class="absolute inset-3 rounded-full border-4 border-white dark:border-slate-900 overflow-hidden"
          >
            <img
              src="../../public/fatihfoto.jpg"
              alt="Fatih Atar"
              class="w-full h-full object-cover"
            />
            <span class="text-3xl md:text-4xl font-bold text-white"> F </span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
