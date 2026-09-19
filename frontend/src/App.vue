<script setup lang="ts">
import { RouterLink, RouterView, useRoute } from 'vue-router'

const route = useRoute()
</script>

<template>
  <div class="site-shell">
    <header class="site-header">
      <div class="nav-container">
        <RouterLink class="brand" to="/" aria-label="MCPhone Store 首页">
          <span class="brand-mark" aria-hidden="true">M</span>

          <span class="brand-name">MCPhone Store</span>
        </RouterLink>

        <nav class="main-nav" aria-label="主导航">
          <RouterLink
            to="/"
            :class="{ 'is-active': route.name === 'home' || route.name === 'app-detail' }"
          >
            发现应用
          </RouterLink>
          <RouterLink to="/about">关于商店</RouterLink>
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
  backdrop-filter: blur(16px) saturate(1.15);
}

.nav-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  height: 68px;
  margin: 0 auto;
  padding: 0 32px;
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
  display: grid;
  place-items: center;

  width: 32px;
  height: 32px;

  background: var(--color-brand);
  color: white;

  border-radius: 9px;
  box-shadow: 0 4px 12px rgb(77 107 254 / 22%);
}

.main-nav {
  display: flex;
  align-items: center;
  gap: 8px;
}

.main-nav a {
  padding: 8px 12px;

  color: var(--color-text-secondary);
  text-decoration: none;

  font-size: 14px;
  font-weight: 500;

  border-radius: 9px;

  transition:
    color 180ms ease,
    background-color 160ms ease,
    transform 180ms ease;
}

.main-nav a:hover {
  background: #f1f5f2;
  color: var(--color-text);
}

.brand:focus-visible,
.main-nav a:focus-visible {
  outline: 3px solid rgba(77, 107, 254, 0.28);
  outline-offset: 3px;
}

.main-nav a:active {
  transform: scale(0.97);
}

.main-nav a.is-active,
.main-nav a.router-link-exact-active {
  color: var(--color-brand-dark);
  background: var(--color-brand-soft);
}

@media (max-width: 640px) {
  .brand-mark {
    width: 34px;
    height: 34px;
  }

  .brand-name {
    font-size: 15px;
  }

  .nav-container {
    height: 64px;
    padding: 0 16px;
  }
}
</style>
