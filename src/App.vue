<script setup>
import { ref, onMounted, watch } from 'vue'
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
import About from './components/About.vue'
import Skills from './components/Skills.vue'
import Projects from './components/Projects.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue' 

const isDark = ref(false)
const currentLang = ref('tr')

onMounted(() => {
  const savedTheme = localStorage.getItem('theme')
  if (savedTheme === 'dark') {
    isDark.value = true
  }

  const savedLang = localStorage.getItem('lang')
  if (savedLang === 'en' || savedLang === 'tr') {
    currentLang.value = savedLang
  }
})

watch(isDark, (val) => {
  localStorage.setItem('theme', val ? 'dark' : 'light')
})

watch(currentLang, (val) => {
  localStorage.setItem('lang', val)
})
</script>

<template>
  <div :class="{ dark: isDark }">
    <div
      class="min-h-screen bg-slate-50 text-slate-900 dark:bg-slate-900 dark:text-slate-50 transition-colors"
    >
      <Navbar
        :isDark="isDark"
        :currentLang="currentLang"
        @toggle-dark="isDark = !isDark"
        @change-lang="currentLang = $event"
      />

      <main class="max-w-5xl mx-auto px-4 space-y-16 md:space-y-20">

        <!-- HERO (zaten bloblu) -->
        <section id="home" class="pt-10 md:pt-16">
          <Hero :currentLang="currentLang" />
        </section>

        <!-- ABOUT -->
        <section id="about" class="scroll-mt-28 md:scroll-mt-32">
          <div class="relative overflow-hidden">
            <!-- arka plan blobu -->
            <div
              class="pointer-events-none absolute -top-32 -left-32 
                     w-[420px] h-[420px] 
                     bg-emerald-400/20 dark:bg-emerald-300/15 
                     rounded-[50%_50%_60%_40%/40%_60%_50%_50%] 
                     blur-[200px]"
            ></div>

            <!-- içerik kartı -->
            <div
              class="relative p-6 md:p-8 rounded-2xl border 
                     bg-white/75 dark:bg-slate-900/80 
                     border-slate-200 dark:border-slate-700 
                     shadow-sm backdrop-blur"
            >
              <About :currentLang="currentLang" />
            </div>
          </div>
        </section>

        <!-- SKILLS -->
        <section id="skills" class="scroll-mt-28 md:scroll-mt-32">
          <div class="relative overflow-hidden">
            <div
              class="pointer-events-none absolute -top-24 -right-24 
                     w-[380px] h-[380px] 
                     bg-sky-400/20 dark:bg-sky-300/15 
                     rounded-[40%_60%_70%_30%/30%_40%_60%_70%] 
                     blur-[190px]"
            ></div>

            <div
              class="relative p-6 md:p-8 rounded-2xl border 
                     bg-white/75 dark:bg-slate-900/80 
                     border-slate-200 dark:border-slate-700 
                     shadow-sm backdrop-blur"
            >
              <Skills :currentLang="currentLang" />
            </div>
          </div>
        </section>

        <!-- PROJECTS -->
        <section id="projects" class="scroll-mt-28 md:scroll-mt-32">
          <div class="relative overflow-hidden">
            <div
              class="pointer-events-none absolute -bottom-32 -left-24 
                     w-[460px] h-[460px] 
                     bg-purple-500/20 dark:bg-purple-400/15 
                     rounded-[60%_40%_50%_50%/50%_60%_40%_50%] 
                     blur-[210px]"
            ></div>

            <div
              class="relative p-6 md:p-8 rounded-2xl border 
                     bg-white/75 dark:bg-slate-900/80 
                     border-slate-200 dark:border-slate-700 
                     shadow-sm backdrop-blur"
            >
              <Projects :currentLang="currentLang" />
            </div>
          </div>
        </section>

        <!-- CONTACT -->
        <section id="contact" class="scroll-mt-28 md:scroll-mt-32">
          <div class="relative overflow-hidden">
            <div
              class="pointer-events-none absolute -top-28 -right-20 
                     w-[360px] h-[360px] 
                     bg-pink-400/18 dark:bg-pink-300/14 
                     rounded-[55%_45%_60%_40%/40%_60%_45%_55%] 
                     blur-[190px]"
            ></div>

            <div
              class="relative p-6 md:p-8 rounded-2xl border 
                     bg-white/75 dark:bg-slate-900/80 
                     border-slate-200 dark:border-slate-700 
                     shadow-sm backdrop-blur"
            >
              <Contact :currentLang="currentLang" />
            </div>
          </div>
        </section>
        <Footer :currentLang="currentLang" />

      </main>
    </div>
  </div>
</template>