<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import NavBar from "./components/NavBar.vue";
import HeroSection from "./components/HeroSection.vue";
import AboutSection from "./components/AboutSection.vue";
import ServicesSection from "./components/ServicesSection.vue";
import ProjectsSection from "./components/ProjectsSection.vue";
import TechStackSection from "./components/TechStackSection.vue";
import FooterSection from "./components/FooterSection.vue";

// Global Mouse Tracking Logic
const mouseX = ref(0);
const mouseY = ref(0);
const isLightMode = ref(false);

const setTheme = (lightMode) => {
  isLightMode.value = lightMode;
  localStorage.setItem("devfin-theme", lightMode ? "light" : "dark");
  document.documentElement.classList.toggle("light-theme", lightMode);
};

const toggleTheme = () => setTheme(!isLightMode.value);

const handleMouseMove = (event) => {
  mouseX.value = event.clientX;
  mouseY.value = event.clientY;
};

onMounted(() => {
  window.addEventListener("mousemove", handleMouseMove);
  setTheme(localStorage.getItem("devfin-theme") === "light");
});

onUnmounted(() => {
  window.removeEventListener("mousemove", handleMouseMove);
});
</script>

<template>
  <div
    class="font-sans text-slate-800 bg-[#0a0a0a] scroll-smooth relative transition-colors duration-300"
    :class="{ 'light-theme': isLightMode }"
  >
    <!-- Global Spotlight/Scope Light -->
    <!-- Fixed position ensures it covers the whole screen while scrolling -->
    <div
      class="pointer-events-none fixed inset-0 z-50 transition-opacity duration-300"
      :style="`background: radial-gradient(600px circle at ${mouseX}px ${mouseY}px, rgba(59, 130, 246, 0.07), transparent 80%);`"
    ></div>

    <NavBar :is-light-mode="isLightMode" @toggle-theme="toggleTheme" />
    <HeroSection />
    <AboutSection />
    <ServicesSection />
    <ProjectsSection />
    <TechStackSection />
    <FooterSection />
  </div>
</template>
