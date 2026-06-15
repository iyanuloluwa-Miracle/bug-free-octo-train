<template>
  <footer id="contact" class="max-w-2xl mx-auto px-6 py-16 border-t border-[#e5e7eb] dark:border-[#1f1f1f]">
    <h2 class="text-xs font-black uppercase tracking-widest text-[#6b7280] dark:text-[#9ca3af] mb-8">
      Contact
    </h2>

    <p class="text-base font-semibold leading-relaxed text-[#374151] dark:text-[#d1d5db] mb-8 max-w-md">
      I'm currently open to new opportunities. Whether you have a project in mind or just want to say hello — my inbox is always open.
    </p>

    <a
      href="mailto:iyanudina@gmail.com"
      class="text-sm font-bold text-[#111111] dark:text-[#f5f5f5] hover:text-[#6b7280] dark:hover:text-[#9ca3af] transition-colors underline underline-offset-4"
    >
      iyanudina@gmail.com
    </a>

    <div class="flex items-center gap-5 mt-10">
      <a
        href="https://github.com/iyanuloluwa-Miracle"
        target="_blank"
        rel="noopener noreferrer"
        class="text-sm font-bold text-[#6b7280] dark:text-[#9ca3af] hover:text-[#111111] dark:hover:text-[#f5f5f5] transition-colors"
      >
        GitHub
      </a>
      <span class="text-[#d1d5db] dark:text-[#374151]">·</span>
      <a
        href="#"
        target="_blank"
        rel="noopener noreferrer"
        class="text-sm font-bold text-[#6b7280] dark:text-[#9ca3af] hover:text-[#111111] dark:hover:text-[#f5f5f5] transition-colors"
      >
        LinkedIn
      </a>
      <span class="text-[#d1d5db] dark:text-[#374151]">·</span>
      <a
        href="#"
        target="_blank"
        rel="noopener noreferrer"
        class="text-sm font-bold text-[#6b7280] dark:text-[#9ca3af] hover:text-[#111111] dark:hover:text-[#f5f5f5] transition-colors"
      >
        X / Twitter
      </a>
    </div>

    <p class="mt-12 text-xs font-semibold text-[#9ca3af] dark:text-[#6b7280]">
      © {{ new Date().getFullYear() }} Iyanuloluwa Miracle
    </p>
  </footer>
</template>
