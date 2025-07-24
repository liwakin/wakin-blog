<script lang="ts" setup>
import ArticleH2 from '~/components/ArticleH2.vue'

const route = useRoute()
const { data: page } = await useAsyncData(route.path, () => {
  return queryCollection('content').path(route.path).first()
})
</script>

<template>
  <template v-if="page">
    <div class="-mt-6 w-full bg-inherit">
      <AppCard
        theme="primary"
        :title="page.title"
        :createdAt="page.createdAt"
        :line-clamp-limit="false"
      >
        <template #content>
          <ContentRenderer
            :value="page"
            class="prose max-w-full"
            :components="{
              h2: ArticleH2,
            }"
          />
        </template>
      </AppCard>
    </div>
  </template>
  <template v-else>
    <div class="-mt-6 flex w-full flex-col gap-4 bg-inherit pt-10 text-center">
      <h1>{{ route.path }} - Not Found</h1>
      <p>哎呀! 找不到你要的内容。</p>
      <NuxtLink to="/" class="text-blue-500 hover:underline">返回首页</NuxtLink>
    </div>
  </template>
</template>
