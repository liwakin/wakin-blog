<script setup lang="ts">
import { SOCIAL_LINKS, EMAILS, ABOUT_ME } from '~/constants'
</script>

<template>
  <aside class="w-64 shrink-0 px-4">
    <div class="space-y-4 bg-white p-2">
      <NuxtImg
        src="/avatar.jpg"
        class="aspect-square w-full object-cover"
        :alt="`${ABOUT_ME.name}'s Avatar`"
        loading="lazy"
        decoding="async"
      />

      <div class="">{{ ABOUT_ME.introduction }}</div>

      <div class="space-y-3">
        <h1 class="border-b border-dashed text-base">链接</h1>
        <ul class="grid grid-cols-2 gap-x-4 gap-y-2 px-1">
          <li v-for="socialLink in SOCIAL_LINKS" :key="socialLink.name">
            <NuxtLink
              class="inline-flex items-center gap-2 text-blue-500 hover:underline"
              :to="socialLink.link"
            >
              <NuxtImg
                :src="socialLink.icon"
                class="size-4"
                :alt="`${socialLink.name} Logo`"
              />
              {{ socialLink.name }}
            </NuxtLink>
          </li>
        </ul>
      </div>

      <div class="space-y-3">
        <h1 class="border-b border-dashed text-base">联系我</h1>

        <p class="">
          随时可以给我发送
          <NuxtLink
            class="text-blue-500 hover:underline"
            :to="`mailto:${EMAILS.qq}`"
          >
            电子邮件
          </NuxtLink>
        </p>
      </div>
    </div>
  </aside>
</template>
