<template>
  <section id="contributions" class="max-w-2xl mx-auto px-6 py-16 border-t border-[#e5e7eb] dark:border-[#1f1f1f]">
    <h2 class="text-xs font-black uppercase tracking-widest text-[#6b7280] dark:text-[#9ca3af] mb-8">
      GitHub Contributions
    </h2>

    <div class="border border-[#e5e7eb] dark:border-[#2d333b] rounded-lg p-4 overflow-x-auto">
      <div v-if="pending" class="h-[120px] flex items-center justify-center">
        <span class="text-sm font-semibold text-[#9ca3af]">Loading...</span>
      </div>

      <div v-else-if="error" class="h-[120px] flex items-center justify-center">
        <span class="text-sm font-semibold text-[#9ca3af]">Could not load contributions.</span>
      </div>

      <template v-else>
        <!-- Month labels -->
        <div class="relative h-4 mb-2">
          <span
            v-for="label in monthLabels"
            :key="`${label.month}-${label.col}`"
            class="absolute text-xs font-semibold text-[#6b7280] dark:text-[#9ca3af]"
            :style="{ left: `${label.col * CELL_SIZE}px` }"
          >
            {{ label.month }}
          </span>
        </div>

        <!-- Contribution grid -->
        <div class="flex gap-[3px]">
          <div
            v-for="(week, wi) in weeks"
            :key="wi"
            class="flex flex-col gap-[3px]"
          >
            <div
              v-for="(day, di) in week"
              :key="di"
              class="w-[10px] h-[10px] rounded-[2px]"
              :style="{ backgroundColor: cellColor(day?.level ?? 0) }"
              :title="day ? `${day.date}: ${day.count} contribution${day.count !== 1 ? 's' : ''}` : undefined"
            />
          </div>
        </div>

        <!-- Footer -->
        <div class="flex items-center justify-between mt-3 flex-wrap gap-2">
          <span class="text-xs font-semibold text-[#6b7280] dark:text-[#9ca3af]">
            {{ totalContributions.toLocaleString() }} contributions in the last year
          </span>
          <div class="flex items-center gap-1">
            <span class="text-xs font-semibold text-[#6b7280] dark:text-[#9ca3af] mr-1">Less</span>
            <div
              v-for="level in 5"
              :key="level"
              class="w-[10px] h-[10px] rounded-[2px]"
              :style="{ backgroundColor: cellColor(level - 1) }"
            />
            <span class="text-xs font-semibold text-[#6b7280] dark:text-[#9ca3af] ml-1">More</span>
          </div>
        </div>
      </template>
    </div>
  </section>
</template>

<script setup lang="ts">
const CELL_SIZE = 13 // 10px cell + 3px gap

interface Contribution {
  date: string
  count: number
  level: number
}

interface ContributionResponse {
  total: Record<string, number>
  contributions: Contribution[]
}

const colorMode = useColorMode()

const lightColors = ['#ebedf0', '#9be9a8', '#40c463', '#30a14e', '#216e39']
const darkColors = ['#2d333b', '#0e4429', '#006d32', '#26a641', '#39d353']

function cellColor(level: number): string {
  const colors = colorMode.value === 'dark' ? darkColors : lightColors
  return colors[Math.min(level, 4)] ?? colors[0]
}

const { data, pending, error } = useFetch<ContributionResponse>(
  'https://github-contributions-api.jogruber.de/v4/iyanuloluwa-Miracle?y=last',
  { server: false }
)

const weeks = computed(() => {
  const contributions = data.value?.contributions
  if (!contributions?.length) return []

  const result: (Contribution | null)[][] = []
  let week: (Contribution | null)[] = []

  const firstDate = new Date(contributions[0].date + 'T00:00:00')
  for (let i = 0; i < firstDate.getDay(); i++) week.push(null)

  for (const contrib of contributions) {
    week.push(contrib)
    if (week.length === 7) {
      result.push([...week])
      week = []
    }
  }

  if (week.length > 0) {
    while (week.length < 7) week.push(null)
    result.push(week)
  }

  return result
})

const monthLabels = computed(() => {
  const MONTHS = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
  const labels: { month: string; col: number }[] = []
  let lastMonth = -1

  weeks.value.forEach((week, colIndex) => {
    const firstDay = week.find(d => d !== null)
    if (!firstDay) return
    const month = new Date(firstDay.date + 'T00:00:00').getMonth()
    if (month !== lastMonth) {
      labels.push({ month: MONTHS[month], col: colIndex })
      lastMonth = month
    }
  })

  return labels
})

const totalContributions = computed(() => data.value?.total?.['lastYear'] ?? 0)
</script>
