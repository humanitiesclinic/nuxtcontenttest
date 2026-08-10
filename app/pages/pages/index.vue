<script setup lang="ts">
const { data: pages } = await useAsyncData('pages-list', () => {
  return queryCollection('pages').order('_id', 'ASC').select('title', 'path', '_id', '_path').all()
})
</script>

<template>
  <div>
    <h1>Pages</h1>
    <ul>
      <li v-for="page in pages" :key="page._id">
        <NuxtLink :to="page._path">{{ page.title || page._path }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>
