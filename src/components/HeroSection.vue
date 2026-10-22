<script setup>
import { ref, computed, watch, onMounted } from 'vue'
import { useI18n } from 'vue-i18n'

const { t, locale } = useI18n()
const displayedText = ref('')
const typingSpeed = 150
const erasingSpeed = 80
const pauseDuration = 2000

const targetText = computed(() =>
  locale.value === 'km' ? 'ទាង តេលា.' : 'Teang Tela.'
)

let timeoutId = null

const startTypingLoop = () => {
  if (timeoutId) clearTimeout(timeoutId)
  displayedText.value = ''
  let charIndex = 0
  let isDeleting = false

  const type = () => {
    const current = targetText.value
    if (isDeleting) {
      if (charIndex > 0) {
        charIndex--
        displayedText.value = current.substring(0, charIndex)
        timeoutId = setTimeout(type, erasingSpeed)
      } else {
        isDeleting = false
        timeoutId = setTimeout(type, 500)
      }
    } else {
      if (charIndex < current.length) {
        charIndex++
        displayedText.value = current.substring(0, charIndex)
        timeoutId = setTimeout(type, typingSpeed)
      } else {
        isDeleting = true
        timeoutId = setTimeout(type, pauseDuration)
      }
    }
  }

  type()
}

// Restart animation when language switches
watch(locale, () => startTypingLoop())

onMounted(() => startTypingLoop())
</script>

<template>
  <section id="home" class="relative pt-32 pb-20 lg:pt-48 lg:pb-32 overflow-hidden bg-[#0a0a0a] text-white">
    <!-- Background Effects -->
    <!-- Constellation pattern (using brand color for grid dots) -->
    <div class="absolute inset-0 z-0 opacity-20"
         style="background-image: radial-gradient(#123764 1px, transparent 1px); background-size: 30px 30px;">
    </div>
    <!-- Ambient Glows -->
    <div class="absolute top-0 right-0 w-[600px] h-[600px] bg-devfin-600/10 rounded-full blur-[120px]"></div>
    <div class="absolute bottom-0 left-0 w-[600px] h-[600px] bg-blue-500/10 rounded-full blur-[120px]"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <div class="grid lg:grid-cols-2 gap-12 lg:gap-8 items-center">
        
        <!-- Left Content -->
        <div class="text-left" v-scroll-reveal>
          <!-- Badge -->
          <div class="inline-flex items-center px-3 py-1.5 rounded-full bg-devfin-600/10 border border-devfin-600/20 text-blue-200 text-xs font-semibold mb-8 tracking-wide">
            <span class="flex h-2 w-2 rounded-full bg-devfin-500 mr-2 animate-pulse"></span> {{ t('hero.badge') }}
          </div>

          <h1 class="text-4xl md:text-6xl font-extrabold tracking-tight mb-4 leading-[1.15] min-h-[3.5rem] md:min-h-[4.5rem]">
            {{ t('hero.welcome') }}
            <span class="text-transparent bg-clip-text bg-gradient-to-r from-blue-500 to-blue-400">{{ displayedText }}</span>
            <span class="text-blue-500 animate-pulse font-light">|</span>
          </h1>
          
          <p class="text-xl md:text-3xl font-medium text-slate-200 mb-6 tracking-wide">
            {{ t('hero.slogan.part1') }} <span class="text-blue-500">{{ t('hero.slogan.part2') }}</span>
          </p>

          <p class="text-lg text-slate-400 mb-8 max-w-lg leading-relaxed">
            {{ t('hero.desc') }}
          </p>
          
          <div class="flex flex-col sm:flex-row gap-4 mb-12">
            <a href="#projects" class="inline-flex justify-center items-center px-8 py-3.5 rounded-lg font-bold bg-blue-600 text-white hover:bg-blue-500 transition-all shadow-lg shadow-devfin-600/20 hover:-translate-y-0.5">
              {{ t('hero.workBtn') }} <i class="fas fa-arrow-right ml-2"></i>
            </a>
            <a href="/cv/teangtelacv.pdf" download="Teang_Tela_CV.pdf" class="inline-flex justify-center items-center px-8 py-3.5 rounded-lg font-bold border border-slate-700 bg-slate-800/50 text-white hover:bg-slate-800 transition-all hover:-translate-y-0.5">
              {{ t('hero.serviceBtn') }} <i class="fas fa-download ml-2 text-sm"></i>
            </a>
          </div>

          <!-- Social Links -->
          <div class="flex items-center gap-4">
            <a
              href="https://github.com/TLAR2411"
              target="_blank"
              rel="noopener"
              class="w-10 h-10 rounded-full bg-slate-800 border border-slate-700 flex items-center justify-center text-slate-400 hover:text-white hover:bg-slate-700 hover:border-slate-600 transition-all hover:-translate-y-1"
            >
              <i class="fab fa-github"></i>
            </a>
            <a
              href="https://t.me/Y_NotMe"
              target="_blank"
              rel="noopener"
              class="w-10 h-10 rounded-full bg-slate-800 border border-slate-700 flex items-center justify-center text-slate-400 hover:text-white hover:bg-blue-600 hover:border-blue-600 transition-all hover:-translate-y-1"
            >
              <i class="fab fa-telegram"></i>
            </a>
            <a
              href="mailto:telateang@gmail.com"
              class="w-10 h-10 rounded-full bg-slate-800 border border-slate-700 flex items-center justify-center text-slate-400 hover:text-white hover:bg-slate-700 hover:border-slate-600 transition-all hover:-translate-y-1"
            >
              <i class="fas fa-envelope"></i>
            </a>
            <div class="text-sm ml-2">
              <p class="text-white font-semibold flex items-center gap-2">
                <span class="w-2 h-2 rounded-full bg-green-400 animate-pulse inline-block"></span>
                {{ t('hero.socialProof.count') }}
              </p>
              <p class="text-slate-500 text-xs">{{ t('hero.socialProof.status') }}</p>
            </div>
          </div>
        </div>

        <!-- Right Content (Terminal) -->
        <div class="relative" v-scroll-reveal="{ delay: 200 }">
           <!-- Terminal Window -->
           <div class="rounded-xl overflow-hidden bg-[#161616] border border-slate-800 shadow-2xl shadow-devfin-600/20 backdrop-blur-sm bg-opacity-90">
              <!-- Window Bar -->
              <div class="bg-[#1a1a1a] px-4 py-3 flex items-center justify-between border-b border-slate-800">
                 <div class="flex space-x-2">
                    <div class="w-3 h-3 rounded-full bg-red-500/80"></div>
                    <div class="w-3 h-3 rounded-full bg-yellow-500/80"></div>
                    <div class="w-3 h-3 rounded-full bg-green-500/80"></div>
                 </div>
                 <div class="text-xs text-slate-500 font-mono">tela@portfolio — -zsh</div>
                 <div class="w-10"></div> <!-- Spacer -->
              </div>
              
              <!-- Terminal Content -->
            <div
              class="p-6 font-mono text-sm leading-relaxed min-h-[320px] font-medium"
              style="font-family: 'Fira Code', monospace"
            >
              <div class="mb-4">
                <span class="text-green-400">tela</span><span class="text-slate-500">@portfolio</span><span class="text-slate-400">:~$</span> whoami
              </div>
              <div class="mb-4 text-slate-300">
                Full Stack Developer<br />
                <span class="text-blue-400">PHP · Laravel · Vue.js · MySQL</span>
              </div>

              <div class="mb-4">
                <span class="text-green-400">tela</span><span class="text-slate-500">@portfolio</span><span class="text-slate-400">:~$</span> cat skills.txt
              </div>
              <div class="mb-4 text-slate-300">
                <span class="text-yellow-400">Backend:</span> PHP, Laravel, REST API<br />
                <span class="text-yellow-400">Frontend:</span> Vue.js, JavaScript, HTML/CSS<br />
                <span class="text-yellow-400">Database:</span> MySQL, SQL Server
              </div>

              <div class="mb-2">
                <span class="text-green-400">tela</span><span class="text-slate-500">@portfolio</span><span class="text-slate-400">:~$</span> git status<span class="animate-pulse text-blue-500">_</span>
              </div>

              <div
                class="mt-8 p-3 bg-green-500/10 border border-green-500/20 rounded text-green-400 text-xs"
              >
                ✓ Open to new opportunities.
              </div>
            </div>
           </div>
           
           <!-- Decorative Elements behind terminal -->
           <div class="absolute -z-10 top-1/2 right-[-50px] w-24 h-24 bg-devfin-600/20 rounded-full blur-2xl"></div>
        </div>

      </div>
    </div>
  </section>
</template>