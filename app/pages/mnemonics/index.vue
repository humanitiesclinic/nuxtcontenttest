<script setup lang="ts">
const { data: mnemonics } = await useAsyncData('mnemonics-list', () => {
  return queryCollection('mnemonics').order('_id', 'ASC').select('title', 'path', '_id', '_path').all()
})
</script>

<template>
  <div>
    <h1>Mnemonics</h1>
    <ul>
      <li v-for="mnemonic in mnemonics" :key="mnemonic._id">
        <NuxtLink :to="mnemonic._path">{{ mnemonic.title || mnemonic._path }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>
