<template>
  <!-- Dark Theme Footer -->
  <footer class="bg-[#0a0a0a] text-slate-400 py-12 border-t border-slate-800">
    <div
      class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 grid grid-cols-1 md:grid-cols-4 gap-8"
    >
      <!-- Brand Column -->
      <div class="col-span-1 md:col-span-2">
        <div class="flex items-center gap-3 mb-4">
          <div class="w-10 h-10 rounded-lg bg-blue-600 flex items-center justify-center font-extrabold text-white text-sm shadow-lg shadow-blue-600/30">TT</div>
          <span class="text-2xl font-bold text-white">Teang Tela.</span>
        </div>
        <p class="text-slate-500 max-w-sm leading-relaxed">
          Full Stack Developer passionate about building web applications and systems that make daily work easier.
        </p>
      </div>

      <!-- Quick Links -->
      <div>
        <h4 class="text-white font-bold mb-6 uppercase text-xs tracking-widest">
          Quick Links
        </h4>
        <ul class="space-y-3 text-sm">
          <li><a href="#home" class="hover:text-blue-400 transition-colors duration-300">Home</a></li>
          <li><a href="#about" class="hover:text-blue-400 transition-colors duration-300">About</a></li>
          <li><a href="#services" class="hover:text-blue-400 transition-colors duration-300">Skills</a></li>
          <li><a href="#projects" class="hover:text-blue-400 transition-colors duration-300">Projects</a></li>
        </ul>
      </div>

      <!-- Connect Column -->
      <div>
        <h4 class="text-white font-bold mb-6 uppercase text-xs tracking-widest">
          Connect
        </h4>
        <div class="flex space-x-4 mb-6">
          <a
            href="https://github.com/TLAR2411"
            target="_blank"
            rel="noopener"
            class="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center text-slate-400 hover:bg-blue-600 hover:text-white transition-all duration-300 hover:-translate-y-1"
          >
            <i class="fab fa-github"></i>
          </a>
          <a
            href="https://t.me/Y_NotMe"
            target="_blank"
            rel="noopener"
            class="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center text-slate-400 hover:bg-blue-600 hover:text-white transition-all duration-300 hover:-translate-y-1"
          >
            <i class="fab fa-telegram"></i>
          </a>
          <a
            href="mailto:telateang@gmail.com"
            class="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center text-slate-400 hover:bg-blue-600 hover:text-white transition-all duration-300 hover:-translate-y-1"
          >
            <i class="fas fa-envelope"></i>
          </a>
        </div>
      </div>
    </div>

    <!-- Copyright -->
    <div
      class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 mt-16 pt-8 border-t border-slate-800/50 text-center text-xs text-slate-600"
    >
      &copy; 2025 Teang Tela. All rights reserved.
    </div>
  </footer>
</template>
