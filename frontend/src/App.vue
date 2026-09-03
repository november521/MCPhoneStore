<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div class="site-shell">
    <header class="site-header">
      <div class="nav-container">
        <RouterLink class="brand" to="/" aria-label="Notes 首页">
          <span class="brand-mark" aria-hidden="true"></span>
          <span>Notes</span>
        </RouterLink>

        <nav class="main-nav" aria-label="主导航">
          <RouterLink to="/">首页</RouterLink>
          <RouterLink to="/about">关于</RouterLink>
        </nav>
      </div>
    </header>

    <RouterView />
  </div>
</template>

<style scoped>
.site-shell {
  min-height: 100vh;
}

.site-header {
  position: sticky;
  top: 0;
  z-index: 10;
  border-bottom: 1px solid var(--color-border);
  background: rgb(255 255 255 / 88%);
  backdrop-filter: blur(16px);
}

.nav-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: min(100% - 48px, var(--content-width));
  height: 72px;
  margin: 0 auto;
}

.brand {
  display: inline-flex;
  gap: 10px;
  align-items: center;
  font-size: 17px;
  font-weight: 600;
  letter-spacing: -0.02em;
}

.brand-mark {
  width: 24px;
  height: 24px;
  background: var(--color-text);
  border-radius: 7px;
}

.main-nav {
  display: flex;
  align-items: center;
  gap: 8px;
}

.main-nav a {
  padding: 8px 12px;
  color: var(--color-text-secondary);
  font-size: 14px;
  border-radius: 8px;
  transition:
    color 160ms ease,
    background-color 160ms ease;
}

.main-nav a:hover,
.main-nav a.router-link-exact-active {
  color: var(--color-text);
  background: var(--color-surface);
}

@media (max-width: 640px) {
  .nav-container {
    width: min(100% - 32px, var(--content-width));
    height: 64px;
  }
}
</style>
