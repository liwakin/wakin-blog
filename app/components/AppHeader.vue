<script setup lang="ts">
import { ABOUT_ME } from '~/constants'

const route = useRoute()
</script>

<template>
  <header class="h-44 w-full bg-gray-800">
    <div
      class="mx-auto flex h-full w-full max-w-5xl items-end justify-between pb-6"
    >
      <NuxtLink
        class="flex w-64 cursor-pointer items-center rounded-tl-md rounded-tr-md bg-teal-600 px-6 py-2 text-gray-100 hover:underline lg:px-8"
        to="/"
      >
        {{ ABOUT_ME.name }}'s wrote...
      </NuxtLink>

      <NuxtLink
        v-if="route.path !== '/who'"
        class="flex cursor-pointer items-center px-4 py-2 text-white hover:underline lg:hidden"
        to="/who"
      >
        谁?
      </NuxtLink>
    </div>
  </header>
</template>
