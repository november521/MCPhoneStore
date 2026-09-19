<script setup lang="ts">
import { ref } from 'vue'

const searchQuery = ref('')
const emit = defineEmits<{
  search: [query: string]
}>()

function submitSearch() {
  emit('search', searchQuery.value.trim())
}
</script>

<template>
  <section class="hero">
    <div class="hero-panel">
      <div class="hero-content">
        <span class="hero-badge"> MCPhone 应用商店 </span>
        <h1>
          发现适合你的
          <span>MCPhone APP</span>
        </h1>

        <p class="hero-description">
          探索由社区开发者制作并经过审核的脚本 App， 为你的 MCPhone 添加更多实用能力与有趣体验。
        </p>

        <form class="search-form" @submit.prevent="submitSearch">
          <label for="app-search" class="sr-only">搜索应用</label>

          <input
            id="app-search"
            v-model="searchQuery"
            type="search"
            placeholder="搜索应用、功能或标签"
          />

          <button type="submit">搜索</button>
        </form>
      </div>

    </div>
  </section>
</template>

<style scoped>
.hero {
  max-width: var(--content-width);
  margin: 0 auto;
  padding: 48px 24px 38px;
}

.hero-panel {
  position: relative;
  padding: 42px 48px;
  border: 1px solid var(--color-border);
  border-radius: 18px;
  background:
    linear-gradient(120deg, rgb(255 255 255 / 96%), rgb(245 247 255 / 92%)),
    var(--color-surface);
  box-shadow: 0 10px 30px rgb(44 57 119 / 4%);
}

.hero-content {
  position: relative;
  z-index: 2;

  max-width: 680px;
}

.hero-badge {
  display: inline-flex;

  padding: 7px 11px;

  border: 1px solid #d7defe;
  border-radius: 999px;

  background: rgba(255, 255, 255, 0.72);
  color: var(--color-brand-dark);

  font-size: 13px;
  font-weight: 700;
  letter-spacing: 0.02em;
}

h1 {
  max-width: 680px;

  margin: 16px 0 12px;

  color: var(--color-text);

  font-size: clamp(34px, 4vw, 48px);
  line-height: 1.14;
  letter-spacing: -0.04em;
}

h1 span {
  color: var(--color-brand);
}

.hero-description {
  max-width: 620px;

  margin: 0;

  color: var(--color-text-secondary);

  font-size: 15px;
  line-height: 1.7;
}

.search-form {
  display: flex;
  align-items: center;
  gap: 12px;
  max-width: 600px;
  margin-top: 24px;
  padding: 5px;
  border: 1px solid var(--color-border);
  border-radius: 11px;
  background: white;
  box-shadow:
    0 2px 4px rgba(23, 32, 26, 0.04),
    0 10px 28px rgba(23, 32, 26, 0.07);
  transition:
    border-color 180ms ease,
    box-shadow 180ms ease;
}

.search-form:focus-within {
  border-color: var(--color-brand);
  box-shadow:
    0 0 0 4px rgba(77, 107, 254, 0.12),
    0 10px 28px rgba(23, 32, 26, 0.07);
}

.search-form input {
  flex: 1;

  min-width: 0;
  min-height: 42px;

  padding: 0 14px;

  border: 0;
  outline: none;

  background: transparent;
  color: var(--color-text);

  font-size: 15px;
}

.search-form input::placeholder {
  color: #949d97;
}

.search-form button {
  min-height: 42px;

  padding: 0 22px;

  border: 0;
  border-radius: 7px;

  background: var(--color-brand);
  color: white;

  font-weight: 700;

  transition:
    background 180ms ease,
    transform 180ms ease;
}

.search-form button:hover {
  background: var(--color-brand-dark);
}

.search-form button:focus-visible {
  outline: 3px solid rgba(77, 107, 254, 0.3);
  outline-offset: 2px;
}
.search-form button:active {
  transform: scale(0.97);
}

.install-hint {
  margin: 18px 0 0;

  color: var(--color-text-secondary);

  font-size: 13px;
}

.install-hint code {
  padding: 3px 6px;

  border-radius: 6px;

  background: rgba(77, 107, 254, 0.1);
  color: var(--color-brand-dark);

  font-family: 'SFMono-Regular', Consolas, monospace;
}


@media (max-width: 700px) {
  .hero {
    padding: 24px 16px 28px;
  }

  .hero-panel {
    padding: 30px 24px;
    border-radius: 14px;
  }

  h1 {
    font-size: 34px;
  }

  .hero-description {
    font-size: 15px;
  }

  .search-form {
    align-items: stretch;
    flex-direction: column;
    margin-top: 24px;
    padding: 8px;
  }

  .search-form button {
    width: 100%;
  }


}
</style>
