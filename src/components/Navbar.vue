<script setup>
import { ref } from 'vue'
import { texts } from '../i18n'

const props = defineProps({
  isDark: {
    type: Boolean,
    default: false,
  },
  currentLang: {
    type: String,
    default: 'tr',
  },
})

const emit = defineEmits(['toggle-dark', 'change-lang'])

const isLangOpen = ref(false)
const isMenuOpen = ref(false)

const setLang = (lang) => {
  emit('change-lang', lang)
  isLangOpen.value = false
}
</script>

<template>
  <header
    class="border-b bg-white/80 dark:bg-slate-900/80 backdrop-blur sticky top-0 z-20 border-slate-200 dark:border-slate-700"
  >
    <nav class="max-w-5xl mx-auto px-4 py-3 flex items-center justify-between">
      <!-- Logo -->
      <div class="font-semibold text-lg">
        Fatih <span class="text-sky-600">Atar</span>
      </div>

      <!-- Desktop Menüsü -->
      <ul class="hidden md:flex gap-6 text-sm">
        <li>
          <a href="#home" class="hover:text-sky-600">
            {{ texts[props.currentLang].navbar.home }}
          </a>
        </li>
        <li>
          <a href="#about" class="hover:text-sky-600">
            {{ texts[props.currentLang].navbar.about }}
          </a>
        </li>
        <li>
          <a href="#skills" class="hover:text-sky-600">
            {{ texts[props.currentLang].navbar.skills }}
          </a>
        </li>
        <li>
          <a href="#projects" class="hover:text-sky-600">
            {{ texts[props.currentLang].navbar.projects }}
          </a>
        </li>
        <li>
          <a href="#contact" class="hover:text-sky-600">
            {{ texts[props.currentLang].navbar.contact }}
          </a>
        </li>
      </ul>

      <!-- Sağ taraf: Dark + Dil + Mobile Menü -->
      <div class="flex items-center gap-2 text-xs relative">
        <!-- Dark Mode Butonu (her ekranda) -->
        <button
          @click="emit('toggle-dark')"
          class="border px-3 py-1 rounded-full text-xs hidden sm:flex items-center gap-1 hover:border-sky-500 hover:text-sky-500 transition"
        >
          <span v-if="props.isDark">🌙</span>
          <span v-else>☀️</span>
          <span>{{ props.isDark ? 'Dark' : 'Light' }}</span>
        </button>

        <!-- Dil Dropdown (desktop + tablet) -->
        <div class="relative hidden sm:block">
          <button
            @click="isLangOpen = !isLangOpen"
            class="border px-3 py-1 rounded-full text-xs flex items-center gap-1 hover:border-sky-500 hover:text-sky-500 transition bg-white/70 dark:bg-slate-800/70"
          >
            🌐
            <span class="uppercase">{{ props.currentLang }}</span>
          </button>

          <div
            v-if="isLangOpen"
            class="absolute right-0 mt-2 w-28 rounded-lg border bg-white dark:bg-slate-800 border-slate-200 dark:border-slate-700 shadow-lg text-xs overflow-hidden"
          >
            <button
              @click="setLang('tr')"
              class="w-full text-left px-3 py-2 hover:bg-slate-100 dark:hover:bg-slate-700"
            >
              🇹🇷 Türkçe
            </button>
            <button
              @click="setLang('en')"
              class="w-full text-left px-3 py-2 hover:bg-slate-100 dark:hover:bg-slate-700"
            >
              🇬🇧 English
            </button>
          </div>
        </div>

        <!-- Sadece mobilde: küçük ikonlu topbar -->
        <button
          @click="isMenuOpen = !isMenuOpen"
          class="flex sm:hidden items-center gap-2 border px-3 py-1 rounded-full text-xs hover:border-sky-500 hover:text-sky-500 transition"
        >
          <span v-if="props.isDark">🌙</span>
          <span v-else>☀️</span>
          <span>☰</span>
        </button>
      </div>
    </nav>

    <!-- Mobile Menü (sm altında) -->
    <transition name="fade">
      <div
        v-if="isMenuOpen"
        class="sm:hidden border-t border-slate-200 dark:border-slate-700 bg-white dark:bg-slate-900"
      >
        <div class="max-w-5xl mx-auto px-4 py-3 space-y-3 text-sm">
          <!-- Dark + Dil ayarları -->
          <div class="flex items-center justify-between">
            <button
              @click="emit('toggle-dark')"
              class="border px-3 py-1 rounded-full text-xs flex items-center gap-1 hover:border-sky-500 hover:text-sky-500 transition"
            >
              <span v-if="props.isDark">🌙</span>
              <span v-else>☀️</span>
              <span>{{ props.isDark ? 'Dark' : 'Light' }}</span>
            </button>

            <div class="relative">
              <button
                @click="isLangOpen = !isLangOpen"
                class="border px-3 py-1 rounded-full text-xs flex items-center gap-1 hover:border-sky-500 hover:text-sky-500 transition bg-white/70 dark:bg-slate-800/70"
              >
                🌐
                <span class="uppercase">{{ props.currentLang }}</span>
              </button>

              <div
                v-if="isLangOpen"
                class="absolute right-0 mt-2 w-28 rounded-lg border bg-white dark:bg-slate-800 border-slate-200 dark:border-slate-700 shadow-lg text-xs overflow-hidden"
              >
                <button
                  @click="setLang('tr')"
                  class="w-full text-left px-3 py-2 hover:bg-slate-100 dark:hover:bg-slate-700"
                >
                  🇹🇷 Türkçe
                </button>
                <button
                  @click="setLang('en')"
                  class="w-full text-left px-3 py-2 hover:bg-slate-100 dark:hover:bg-slate-700"
                >
                  🇬🇧 English
                </button>
              </div>
            </div>
          </div>

          <!-- Mobile linkler -->
          <div class="flex flex-col gap-2 pt-2">
            <a
              href="#home"
              class="py-1 hover:text-sky-600"
              @click="isMenuOpen = false"
            >
              {{ texts[props.currentLang].navbar.home }}
            </a>
            <a
              href="#about"
              class="py-1 hover:text-sky-600"
              @click="isMenuOpen = false"
            >
              {{ texts[props.currentLang].navbar.about }}
            </a>
            <a
              href="#skills"
              class="py-1 hover:text-sky-600"
              @click="isMenuOpen = false"
            >
              {{ texts[props.currentLang].navbar.skills }}
            </a>
            <a
              href="#projects"
              class="py-1 hover:text-sky-600"
              @click="isMenuOpen = false"
            >
              {{ texts[props.currentLang].navbar.projects }}
            </a>
            <a
              href="#contact"
              class="py-1 hover:text-sky-600"
              @click="isMenuOpen = false"
            >
              {{ texts[props.currentLang].navbar.contact }}
            </a>
          </div>
        </div>
      </div>
    </transition>
  </header>
</template>

