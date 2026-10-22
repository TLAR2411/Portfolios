<script setup>
import { ref, computed } from "vue";
import { useI18n } from "vue-i18n";

const props = defineProps({
  isLightMode: Boolean,
});
const emit = defineEmits(["toggle-theme"]);
const { locale, t } = useI18n();
const isMobileMenuOpen = ref(false);

const menuItems = computed(() => [
  { name: t("nav.home"), href: "#home" },
  { name: t("nav.about"), href: "#about" },
  { name: t("nav.skills"), href: "#services" },
  { name: t("nav.work"), href: "#projects" },
]);

const toggleMenu = () => (isMobileMenuOpen.value = !isMobileMenuOpen.value);
const closeMenu = () => (isMobileMenuOpen.value = false);
const switchLang = () => {
  locale.value = locale.value === "en" ? "km" : "en";
};
const toggleTheme = () => emit("toggle-theme");
</script>

<template>
  <nav
    :class="[
      'fixed w-full z-50 backdrop-blur-md border-b transition-all duration-300',
      props.isLightMode
        ? 'bg-white/95 border-slate-200 shadow-sm'
        : 'bg-[#0a0a0a]/95 border-slate-800',
    ]"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-16">
        <!-- Logo -->
        <a href="#home" class="flex-shrink-0 flex items-center gap-2">
          <img
            :src="props.isLightMode ? '/logo.png' : '/logo-transparent.png'"
            alt="Teang Tela"
            :class="['h-10 w-10 object-contain', props.isLightMode ? 'rounded-lg' : '']"
          />
          <span
            :class="[
              'font-bold text-xl tracking-tight',
              props.isLightMode ? 'text-slate-900' : 'text-white',
            ]"
            >Tela.</span
          >
        </a>

        <!-- Desktop Menu -->
        <div class="hidden md:flex space-x-8 items-center">
          <a
            v-for="item in menuItems"
            :key="item.name"
            :href="item.href"
            :class="[
              'font-medium transition text-sm uppercase tracking-wide',
              props.isLightMode
                ? 'text-slate-500 hover:text-slate-900'
                : 'text-slate-400 hover:text-white',
            ]"
          >
            {{ item.name }}
          </a>
        </div>

        <!-- Right Side Actions -->
        <div class="hidden md:flex space-x-3 items-center">
          <!-- Language Switcher -->
          <button
            @click="switchLang"
            :class="[
              'font-bold text-xs uppercase rounded px-2 py-1 transition border',
              props.isLightMode
                ? 'text-slate-500 border-slate-300 hover:text-slate-900 hover:border-slate-400'
                : 'text-slate-400 border-slate-700 hover:text-white',
            ]"
          >
            {{ locale === "en" ? "EN" : "KM" }}
          </button>

          <!-- Theme Toggle -->
          <button
            @click="toggleTheme"
            :aria-label="
              props.isLightMode ? 'Switch to dark mode' : 'Switch to light mode'
            "
            :class="[
              'font-bold text-xs uppercase rounded px-2 py-1 transition border',
              props.isLightMode
                ? 'text-slate-500 border-slate-300 hover:text-slate-900 hover:border-slate-400'
                : 'text-slate-400 border-slate-700 hover:text-white',
            ]"
          >
            <i
              class="fas"
              :class="props.isLightMode ? 'fa-moon' : 'fa-sun'"
            ></i>
          </button>

          <!-- Contact Button -->
          <a
            href="mailto:telateang@gmail.com"
            class="bg-blue-600 hover:bg-blue-500 text-white px-5 py-2 rounded-full font-bold transition text-sm flex items-center gap-2"
          >
            {{ t("nav.contact") }}
          </a>
        </div>

        <!-- Mobile Buttons -->
        <div class="md:hidden flex items-center gap-3">
          <button
            @click="switchLang"
            :class="[
              'font-bold text-xs uppercase rounded px-2 py-1 transition border',
              props.isLightMode
                ? 'text-slate-500 border-slate-300'
                : 'text-slate-400 border-slate-700',
            ]"
          >
            {{ locale === "en" ? "EN" : "KM" }}
          </button>

          <button
            @click="toggleTheme"
            :aria-label="
              props.isLightMode ? 'Switch to dark mode' : 'Switch to light mode'
            "
            :class="[
              'font-bold text-xs uppercase rounded px-2 py-1 transition border',
              props.isLightMode
                ? 'text-slate-500 border-slate-300'
                : 'text-slate-400 border-slate-700',
            ]"
          >
            <i
              class="fas"
              :class="props.isLightMode ? 'fa-moon' : 'fa-sun'"
            ></i>
          </button>

          <button
            @click="toggleMenu"
            :class="[
              'focus:outline-none transition',
              props.isLightMode
                ? 'text-slate-600 hover:text-slate-900'
                : 'text-slate-400 hover:text-white',
            ]"
          >
            <i
              class="fas"
              :class="isMobileMenuOpen ? 'fa-times' : 'fa-bars'"
            ></i>
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Menu Panel -->
    <div
      v-show="isMobileMenuOpen"
      :class="[
        'md:hidden border-t absolute w-full',
        props.isLightMode
          ? 'bg-white border-slate-200 shadow-sm'
          : 'bg-[#111111] border-slate-800 shadow-xl',
      ]"
    >
      <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
        <a
          v-for="item in menuItems"
          :key="item.name"
          :href="item.href"
          @click="closeMenu"
          :class="[
            'block px-3 py-2 rounded-md text-base font-medium transition',
            props.isLightMode
              ? 'text-slate-600 hover:text-slate-900 hover:bg-slate-100'
              : 'text-slate-300 hover:text-white hover:bg-slate-800',
          ]"
        >
          {{ item.name }}
        </a>
      </div>
    </div>
  </nav>
</template>
