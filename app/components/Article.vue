<script setup lang="ts">
const props = defineProps<{
  theme?: 'primary' | 'secondary'
  image?: string
  title: string
  desc: string
  createdAt?: number | string
  link?: string
}>()
</script>

<template>
  <article class="w-full">
    <AppCard v-bind="props">
      <template #content>
        <p class="my-5">
          {{ props.desc }}
        </p>

        <NuxtLink
          v-if="props.link"
          :to="props.link"
          class="my-5 block cursor-pointer text-blue-500 hover:underline"
        >
          继续阅读…
        </NuxtLink>
      </template>
    </AppCard>
  </article>
</template>
