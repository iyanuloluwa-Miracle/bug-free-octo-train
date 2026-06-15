<template>
  <section id="projects" class="max-w-2xl mx-auto px-6 py-16 border-t border-[#e5e7eb] dark:border-[#1f1f1f]">
    <h2 class="text-xs font-black uppercase tracking-widest text-[#6b7280] dark:text-[#9ca3af] mb-10">
      Projects
    </h2>

    <div class="space-y-12">
      <article v-for="project in projects" :key="project.name" class="group">
        <div class="flex items-start justify-between mb-2">
          <h3 class="text-base font-extrabold text-[#111111] dark:text-[#f5f5f5]">
            {{ project.name }}
          </h3>
          <a
            v-if="project.link"
            :href="project.link"
            target="_blank"
            rel="noopener noreferrer"
            class="text-xs font-bold text-[#6b7280] dark:text-[#9ca3af] hover:text-[#111111] dark:hover:text-[#f5f5f5] transition-colors shrink-0 ml-4 mt-0.5"
          >
            View →
          </a>
        </div>
        <p class="text-sm font-semibold text-[#6b7280] dark:text-[#9ca3af] mb-3">
          {{ project.description }}
        </p>
        <ul class="space-y-1">
          <li
            v-for="feature in project.features"
            :key="feature"
            class="text-sm font-semibold text-[#374151] dark:text-[#d1d5db] flex gap-2"
          >
            <span class="text-[#9ca3af] shrink-0">—</span>
            {{ feature }}
          </li>
        </ul>
      </article>
    </div>
  </section>
</template>

<script setup lang="ts">
const projects = [
  {
    name: 'Vidcipe',
    description: 'AI-powered SaaS that extracts structured, cookable recipes from videos across YouTube, TikTok, Instagram, Facebook, and Pinterest — in under 30 seconds.',
    link: 'http://vidcipe.xyz/',
    features: [
      'Built a multi-platform video ingestion pipeline spanning 5 major platforms',
      'AI-driven ingredient parsing with dynamic portion scaling for any serving size',
      'Recipe translation, print/export, and shareable link generation',
      '50K+ recipes extracted · 2,000+ active cooks · 4.9★ user rating',
    ],
  },
  {
    name: 'Texteo',
    description: 'AI content generation platform that turns any topic or URL into platform-optimised posts for LinkedIn, Twitter/X, and Instagram — in seconds.',
    link: 'https://texteo.site',
    features: [
      'Full SaaS stack: auth, Lemon Squeezy billing, searchable content history',
      'Multi-tone engine (professional, casual, marketing, viral) with AI image generation',
      'URL-to-post pipeline that repurposes articles into social content automatically',
      '10K+ posts generated monthly across 17,000+ registered creators',
    ],
  },
  {
    name: 'Bible Study Challenge',
    description: 'A free spiritual growth platform with daily scripture delivery, end-to-end encrypted journals, a sermon library, and community faith groups.',
    link: 'https://www.biblestudychallenge.online',
    features: [
      'Encrypted personal journal for private prayers and daily reflections',
      'Personalised daily verse delivery and curated sermon and book library',
      'Community spaces for devotional sharing and faith group accountability',
      'Offline-first — all downloaded content accessible without an internet connection',
    ],
  },
  {
    name: 'RCCG City of God',
    description: 'Official digital presence for RCCG City of God parish in Stirling, UK — built to inform, engage, and connect congregation members online.',
    link: 'https://www.rccgcogs.com',
    features: [
      'Designed and deployed a full church website for a UK-based RCCG parish',
      'Clean, accessible layout serving service schedules and community resources',
      'Mobile-responsive design built for a broad, multi-generational congregation',
      'Primary digital touchpoint for one of Scotland\'s active RCCG communities',
    ],
  },
]
</script>
