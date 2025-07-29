<script setup lang="ts">
useSeoMeta({
  title: 'Blog - Wakin',
  description: '分享欲来的时候，就写点什么。',
})
</script>

<template>
  <AppHeader />

  <main class="mx-auto flex w-full max-w-5xl bg-white pb-16">
    <NuxtPage />
  </main>
</template>

<style lang="postcss">
body {
  @apply bg-slate-200 text-gray-600;
}
</style>
