<script setup lang="ts">
const props = defineProps<{
  theme?: 'primary' | 'secondary'
  image?: string
  title: string
  createdAt?: number | string
  link?: string
  lineClampLimit?: boolean
}>()
</script>

<template>
  <div class="w-full">
    <div
      class="-ml-10 rounded-l-full p-2 px-16 text-gray-50 lg:-ml-8"
      :class="[props.theme === 'primary' ? 'bg-orange-400' : 'bg-teal-600']"
    >
      <h1
        class="whitespace-pre-wrap break-words text-2xl"
        :class="lineClampLimit === false ? '' : 'line-clamp-1'"
      >
        <NuxtLink
          v-if="props.link"
          :to="props.link"
          class="cursor-pointer hover:underline"
        >
          {{ props.title }}
        </NuxtLink>

        <span v-else>{{ props.title }}</span>
      </h1>
    </div>

    <div v-if="props.createdAt" class="bg-yellow-200 px-6 py-1 lg:px-8">
      发表于 {{ new Date(props.createdAt).toLocaleDateString() }}
    </div>

    <div class="my-5 px-6 lg:px-8">
      <slot name="content"></slot>
    </div>
  </div>
</template>
