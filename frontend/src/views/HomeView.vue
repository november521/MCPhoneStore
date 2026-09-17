<script setup lang="ts">
import HeroSection from '../components/HeroSection.vue'
import AppCard from '../components/AppCard.vue'
import { apps } from '../data/apps'
</script>

<template>
  <main>
    <HeroSection />
    <section class="app-list">
      <h2>发现应用</h2>

      <div class="app-grid">
        <AppCard v-for="app in apps" :key="app.id" :app="app" />
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

@media (max-width: 700px) {
  .app-grid {
    grid-template-columns: 1fr;
  }
}
</style>
