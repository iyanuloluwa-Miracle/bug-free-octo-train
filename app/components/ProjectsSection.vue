<template>
  <section id="projects" class="max-w-2xl mx-auto px-6 py-16 border-t border-[#e5e7eb] dark:border-[#1f1f1f]">
    <h2 class="text-xs font-bold uppercase tracking-widest text-[#6b7280] dark:text-[#9ca3af] mb-10">
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
            class="text-xs text-[#6b7280] dark:text-[#9ca3af] hover:text-[#111111] dark:hover:text-[#f5f5f5] transition-colors shrink-0 ml-4 mt-0.5"
          >
            View →
          </a>
        </div>
        <p class="text-sm font-medium text-[#6b7280] dark:text-[#9ca3af] mb-3">
          {{ project.description }}
        </p>
        <ul class="space-y-1">
          <li
            v-for="feature in project.features"
            :key="feature"
            class="text-sm text-[#374151] dark:text-[#d1d5db] flex gap-2"
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
    name: 'Project Alpha',
    description: 'A banner creation tool with built-in design tools and powerful customization options.',
    link: '#',
    features: [
      'Drag-and-drop canvas editor',
      '100+ customizable templates',
      'Team dashboard and sharing',
      'Export to multiple formats',
    ],
  },
  {
    name: 'Project Beta',
    description: 'A platform that enables seamless global money transfers using just a phone number.',
    link: '#',
    features: [
      'Instant cross-border transfers',
      'End-to-end encryption',
      'Multi-currency support',
      'Real-time transaction tracking',
    ],
  },
  {
    name: 'Project Gamma',
    description: 'An AI-powered developer productivity tool that streamlines code review and documentation.',
    link: '#',
    features: [
      'Automated code review suggestions',
      'Inline documentation generation',
      'IDE extension support',
      'Team workflow integrations',
    ],
  },
  {
    name: 'Project Delta',
    description: 'A decentralized identity and reputation system for AI agents and autonomous systems.',
    link: '#',
    features: [
      'Cryptographic identity verification',
      'Decentralized reputation scoring',
      'Open-source and auditable',
      'Compatible with major AI frameworks',
    ],
  },
]
</script>
