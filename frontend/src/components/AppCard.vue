<script setup lang="ts">
interface AppInfo {
  id: number
  name: string
  summary: string
  version: string
  category: string
}

defineProps<{
  app: AppInfo
}>()
</script>

<template>
  <article class="app-card">
    <h3>{{ app.name }}</h3>

    <span>{{ app.category }}</span>

    <p>{{ app.summary }}</p>

    <span>版本:{{ app.version }}</span>
  </article>
</template>

<style scoped>
.app-card {
  background: #fff;
  border: 1px solid #ddd;
  border-radius: 12px;
  padding: 16px;
}
</style>
