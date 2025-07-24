<script setup lang="ts">
const route = useRoute()

const { data: posts } = await useAsyncData('content', () =>
  queryCollection('content').all(),
)

const PAGE_SIZE = 10
const currentPage = computed(() => {
  const page = Number(route.params.page || 1)
  return isNaN(page) ? 1 : page
})

const totalPages = computed(() => {
  if (!posts.value) return 0
  return Math.ceil(posts.value.length / PAGE_SIZE)
})

const pagedPosts = computed(() => {
  const start = (currentPage.value - 1) * PAGE_SIZE
  return posts.value?.slice(start, start + PAGE_SIZE) || []
})
</script>

<template>
  <div class="-mt-6 flex w-full items-start justify-between gap-4">
    <div class="flex-auto">
      <template v-if="pagedPosts.length">
        <section v-for="(post, index) in pagedPosts" :key="post.id">
          <Article
            :theme="index === 0 ? 'primary' : 'secondary'"
            :title="post.title"
            :desc="post.description"
            :createdAt="post.createdAt"
            :link="post.path"
          >
          </Article>
        </section>
      </template>

      <div v-else class="flex h-96 w-full items-center justify-center">
        <p>似乎被你找到了一片荒芜之地</p>
      </div>

      <ol
        v-if="totalPages > 1"
        class="flex items-center divide-x divide-dashed p-5 text-gray-500 [&_li]:cursor-pointer [&_li]:px-3 [&_li]:py-1 [&_li]:text-center"
        aria-label="分页导航"
      >
        <li>
          <NuxtLink
            :to="currentPage === 2 ? '/' : `/${currentPage - 1}`"
            class="text-gray-500 hover:text-gray-800 hover:underline"
            :class="currentPage === 1 ? 'pointer-events-none opacity-70' : ''"
          >
            Previous
          </NuxtLink>
        </li>
        <li v-for="page in totalPages" :key="page">
          <NuxtLink
            :to="page === 1 ? '/' : `/${page}`"
            class="text-gray-500 hover:text-gray-800 hover:underline"
            :class="
              currentPage === page ? 'pointer-events-none opacity-70' : ''
            "
          >
            {{ page }}
          </NuxtLink>
        </li>
        <li>
          <NuxtLink
            :to="`/${currentPage + 1}`"
            class="text-gray-500 hover:text-gray-800 hover:underline"
            :class="
              currentPage === totalPages ? 'pointer-events-none opacity-70' : ''
            "
          >
            Next
          </NuxtLink>
        </li>
      </ol>
    </div>

    <AppAside class="hidden lg:block" />
  </div>
</template>
