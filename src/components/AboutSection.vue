<script setup>
import { useI18n } from "vue-i18n";
const { t } = useI18n();
const skills = [
  "PHP",
  "Laravel",
  "Vue.js",
  "TypeScript",
  "Vuetify",
  "MySQL",
  "MongoDB",
  "PostgreSQL",
  "Firebase",
  "Supabase",
  "REST API",
  "Git",
];
</script>

<template>
  <section
    id="about"
    class="py-24 bg-[#111111] relative overflow-hidden border-t border-slate-800"
  >
    <!-- Background Glows -->
    <div
      class="absolute top-0 right-0 w-96 h-96 bg-blue-600/5 rounded-full blur-[120px]"
    ></div>
    <div
      class="absolute bottom-0 left-0 w-96 h-96 bg-blue-500/5 rounded-full blur-[120px]"
    ></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <div class="grid lg:grid-cols-2 gap-16 items-center">
        <!-- Left: Photo -->
        <div
          v-scroll-reveal
          class="flex justify-center lg:justify-end order-2 lg:order-1"
        >
          <div class="relative">
            <!-- Photo Card -->
            <div
              class="w-100 h-[400px] rounded-3xl overflow-hidden border border-slate-700 shadow-2xl shadow-blue-600/10"
            >
              <img
                src="../assets/images/tela.jpg"
                alt="Teang Tela"
                class="w-full h-full object-cover object-top"
              />
              <div
                class="absolute inset-0 bg-gradient-to-t from-black/30 to-transparent"
              ></div>
            </div>
            <!-- Floating Badge -->
            <div
              class="absolute -bottom-5 -right-5 bg-slate-900 border border-blue-500/30 rounded-2xl px-5 py-4 shadow-xl shadow-black/40"
            >
              <p class="text-blue-400 text-2xl font-extrabold leading-none">
                2+
              </p>
              <p class="text-slate-400 text-xs mt-1">Years Coding</p>
            </div>
            <!-- Decorative ring -->
            <div
              class="absolute -z-10 -top-4 -left-4 w-full h-full rounded-3xl border border-blue-500/10"
            ></div>
          </div>
        </div>

        <!-- Right: Content -->
        <div v-scroll-reveal="{ delay: 200 }" class="order-1 lg:order-2">
          <span
            class="text-xs font-bold tracking-wider text-blue-100 uppercase bg-blue-500/10 border border-blue-500/20 px-4 py-1.5 rounded-full inline-block"
          >
            {{ t("about.badge") }}
          </span>

          <h2
            class="mt-6 text-4xl md:text-5xl font-extrabold text-white tracking-tight"
          >
            {{ t("about.title") }}
          </h2>

          <p class="mt-6 text-lg text-slate-400 leading-relaxed">
            {{ t("about.bio") }}
          </p>

          <!-- Quick Info -->
          <div class="grid grid-cols-2 gap-4 mt-8 mb-8">
            <div class="bg-[#1a1a1a] rounded-xl p-4 border border-slate-800">
              <p class="text-slate-500 text-xs uppercase tracking-wider mb-1">
                {{ t("about.locationLabel") }}
              </p>
              <p class="text-white font-semibold">{{ t("about.location") }}</p>
            </div>
            <div class="bg-[#1a1a1a] rounded-xl p-4 border border-slate-800">
              <p class="text-slate-500 text-xs uppercase tracking-wider mb-1">
                {{ t("about.statusLabel") }}
              </p>
              <p class="text-green-400 font-semibold flex items-center gap-2">
                <span
                  class="w-2 h-2 rounded-full bg-green-400 animate-pulse inline-block"
                ></span>
                {{ t("about.status") }}
              </p>
            </div>
          </div>

          <!-- Skill Tags -->
          <div class="flex flex-wrap gap-2">
            <span
              v-for="skill in skills"
              :key="skill"
              class="px-3 py-1.5 rounded-lg text-xs font-bold border bg-slate-800/50 text-slate-300 border-slate-700 hover:border-blue-500/50 hover:text-blue-300 transition-colors cursor-default"
            >
              {{ skill }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
