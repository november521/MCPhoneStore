<script setup lang="ts">
import HeroSection from '../components/HeroSection.vue'
const apps = [
  {
    id: 1,
    name: '计算器',
    summary: '添加一个计算器',
    version: '1.0.0',
    category: '实用工具',
  },
  {
    id: 2,
    name: '死亡榜',
    summary: '添加一个死亡榜',
    version: '1.0.0',
    category: '实用工具',
  },
  {
    id: 3,
    name: '钱包',
    summary: '查看自己的小钱钱',
    version: '1.0.0',
    category: '经济工具',
  },
]
</script>

<template>
  <main>
    <HeroSection />
    <section class="app-list">
      <h2>发现应用</h2>

      <div class="app-grid">
        <article v-for="app in apps" :key="app.id" class="app-card">
          <h3>{{ app.name }}</h3>

          <span>{{ app.category }}</span>

          <p>{{ app.summary }}</p>

          <span>版本:{{ app.version }}</span>
        </article>
      </div>
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
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 16px;
}

.app-card {
  background: #fff;
  border: 1px solid #ddd;
  border-radius: 12px;
  padding: 16px;
}

@media (max-width: 700px) {
  .app-grid {
    grid-template-columns: 1fr;
  }
}
</style>
