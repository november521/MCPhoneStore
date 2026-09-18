<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div class="site-shell">
    <header class="site-header">
      <div class="nav-container">
        <RouterLink class="brand" to="/" aria-label="MCPhone Store 首页">
          <span class="brand-mark" aria-hidden="true"> M </span>

          <span class="brand-name" aria-hidden="true"> MCPhone Stroe </span>
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
  display: grid;
  place-items: center;

  width: 32px;
  height: 32px;

  background: var(--color-brand);
  color: white;

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
  text-decoration: none;

  font-size: 14px;
  font-weight: 600;

  border-radius: 9px;

  transition:
    color 180ms ease,
    background-color 160ms ease,
    transform 180ms ease;
}

.nav-link:hover {
  background: #f1f5f2;
  color: var(--color-text);
}

.nav-link.is-active {
  background: var(--color-brand-soft);
  color: var(--color-brand-dark);
}

.brand:focus-visible,
.nav-link:focus-visible {
  outline: 3px solid rgba(77, 107, 254, 0.28);
  outline-offset: 3px;
}

.nav-link:active {
  transform: scale(0.97);
}

.main-nav a.router-link-exact-active {
  color: var(--color-text);
  background: var(--color-surface);
}

@media (max-width: 640px) {
  .header-inner {
    min-height: 62px;
    padding: 0 16px;
  }

  .brand-mark {
    width: 34px;
    height: 34px;
  }

  .brand-name {
    font-size: 15px;
  }

  .nav-link {
    padding: 8px 10px;
  }

  .nav-container {
    width: min(100% - 32px, var(--content-width));
    height: 64px;
  }
}
</style>
