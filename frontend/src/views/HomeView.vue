<script setup lang="ts">
import { computed, ref } from 'vue'
import HeroSection from '../components/HeroSection.vue'
import AppCard from '../components/AppCard.vue'
import { apps } from '../data/apps'

const searchQuery = ref('')
const filteredApps = computed(() => {
  const keyword = searchQuery.value.trim().toLowerCase()

  if (!keyword) {
    return apps
  }

  return apps.filter((app) => {
    const searchableText = `${app.name} ${app.summary} ${app.category}`.toLowerCase()
    return searchableText.includes(keyword)
  })
})
</script>

<template>
  <main>
    <HeroSection @search="searchQuery = $event" />
    <section class="app-list">
      <h2>发现应用</h2>

      <div class="app-grid">
        <AppCard v-for="app in filteredApps" :key="app.id" :app="app" />
      </div>
      <p v-if="filteredApps.length === 0" class="empty-message">
        没有找到相关应用，请尝试其他关键词。
      </p>
    </section>
  </main>
</template>

<style scoped>
.app-list {
  max-width: 900px;
  margin: 0 auto;
  padding: 0 20px;
}

.app-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(220px, 1fr));
  gap: 16px;
}

@media (max-width: 700px) {
  .app-grid {
    grid-template-columns: 1fr;
  }
}

.empty-message {
  color: #666;
  padding: 32px 0;
  text-align: center;
}
</style>
