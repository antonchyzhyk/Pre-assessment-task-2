<template>
  <div class="p-5">
    <div class="max-w-[600px] p-5 flex flex-col gap-2 border border-gray-300 rounded-lg">
      <p class="text-xl font-bold text-gray-900">Senior Big Data Engineer (GCP)</p>

      <p class="text-sm text-gray-700">
        location: Poland; Bulgaria * Be a part of the team of data-focused
        engineers dedicated to continuous learning, improvement.
      </p>

      <div class="flex flex-col gap-1">
        <AppSeparatedList
          :items="singleSeparatedItem"
          class="text-sm text-gray-700"
        />

        <AppSeparatedList
          :items="twoSeparatedItems"
          class="text-sm text-gray-700"
        />

        <AppSeparatedList
          :items="jobSeparatedList"
          class="text-sm text-orange-900"
        />

        <AppSeparatedList
          :items="jobSeparatedList"
          separator="|"
          class="text-sm text-green-900"
        />

        <AppSeparatedList
          :items="jobSeparatedList"
          class="text-sm text-gray-700"
        >
          <template #separator>
            <span class="text-bold text-orange-500">/</span>
          </template>
        </AppSeparatedList>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
const jobData = {
  count: 12,
  location: ['Warszawa', 'Poland'],
  salary: '123123',
  timestamp: '2024-07-07T07:07:07.123Z'
}

const singleSeparatedItem = [`Count: ${jobData.count}`]

const twoSeparatedItems = [jobData.location.join(', '), formatSalary(jobData.salary)]

const jobSeparatedList = [
  `Count: ${jobData.count}`,
  jobData.location.join(', '),
  formatSalary(jobData.salary),
  formatRelativeTime(jobData.timestamp)
]

function formatSalary (value: string) {
  const num = parseFloat(value)
  return `$${num}`
}

function formatRelativeTime (timestamp: string): string {
  const date = new Date(timestamp)
  const now = new Date()

  const diffMs = now.getTime() - date.getTime()
  const diffHours = Math.floor(diffMs / (1000 * 60 * 60))
  const diffDays = Math.floor(diffHours / 24)

  if (diffDays > 0) return `${diffDays} day${diffDays > 1 ? 's' : ''} ago`
  if (diffHours > 0) return `${diffHours} hour${diffHours > 1 ? 's' : ''} ago`
  return 'Just now'
}
</script>
