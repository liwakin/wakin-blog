<script lang="ts" setup>
const props = defineProps<{
  id: string
}>()
</script>

<template>
  <div
    class="-ml-16 -mr-6 rounded-l-full bg-teal-600 p-2 px-16 lg:-ml-16 lg:-mr-8"
  >
    <h2 class="my-0 whitespace-pre-wrap break-words text-2xl font-normal">
      <NuxtLink
        :to="`#${props.id}`"
        class="cursor-pointer text-gray-50 no-underline hover:underline"
      >
        {{ props.id }}
      </NuxtLink>
    </h2>
  </div>
</template>
