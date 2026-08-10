<script setup lang="ts">
const { data: articles } = await useAsyncData('articles-list', () => {
  return queryCollection('articles').find()
})
</script>

<template>
  <div>
    <h1>Articles</h1>
    <ul>
      <li v-for="article in articles" :key="article._id">
        <NuxtLink :to="article._path">{{ article.title || article._path }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>
