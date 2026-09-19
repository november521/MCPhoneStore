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
    <section class="app-list" aria-labelledby="app-list-title">
      <div class="section-heading">
        <div>
          <p class="eyebrow">应用目录</p>
          <h2 id="app-list-title">发现应用</h2>
        </div>
        <p class="app-count">共 {{ filteredApps.length }} 款应用</p>
      </div>

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
  max-width: var(--content-width);
  margin: 0 auto;
  padding: 0 24px 80px;
}

.section-heading {
  display: flex;
  align-items: end;
  justify-content: space-between;
  gap: 24px;
  margin-bottom: 24px;
}

.eyebrow {
  margin-bottom: 6px;
  color: var(--color-brand);
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 0.08em;
}

h2 {
  font-size: 28px;
  line-height: 1.2;
  letter-spacing: -0.035em;
}

.app-count {
  color: var(--color-text-secondary);
  font-size: 13px;
}

.app-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(220px, 1fr));
  gap: 16px;
}

@media (max-width: 700px) {
  .app-list {
    padding: 0 16px 56px;
  }

  .section-heading {
    align-items: flex-start;
    flex-direction: column;
    gap: 8px;
    margin-bottom: 18px;
  }

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
