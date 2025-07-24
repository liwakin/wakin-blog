<script lang="ts" setup>
const props = defineProps<{
  id: string
}>()
</script>

<template>
  <h2
    class="my-0 -ml-16 -mr-6 whitespace-pre-wrap break-words rounded-l-full bg-teal-600 p-2 px-16 text-2xl font-normal lg:-ml-16 lg:-mr-8"
  >
    <NuxtLink
      :to="`#${props.id}`"
      class="cursor-pointer text-gray-50 no-underline hover:underline"
    >
      {{ props.id }}
    </NuxtLink>
  </h2>
</template>
