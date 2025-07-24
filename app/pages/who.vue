<script setup lang="ts">
import { SOCIAL_LINKS, EMAILS, ABOUT_ME } from '~/constants'
</script>

<template>
  <div class="-mt-6 w-full">
    <AppCard theme="primary" title="谁 ?">
      <template #content> {{ ABOUT_ME.introduction }} </template>
    </AppCard>

    <AppCard title="链接">
      <template #content>
        <ul class="flex flex-wrap gap-x-6 gap-y-4 px-1">
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
      </template>
    </AppCard>

    <AppCard title="联系我">
      <template #content>
        随时可以给我发送
        <NuxtLink
          class="text-blue-500 hover:underline"
          :to="`mailto:${EMAILS.qq}`"
        >
          电子邮件
        </NuxtLink>
      </template>
    </AppCard>
  </div>
</template>
