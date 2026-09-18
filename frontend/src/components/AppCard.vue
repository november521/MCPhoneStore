<script setup lang="ts">
import type { AppInfo } from '../types/app'

defineProps<{
  app: AppInfo
}>()
</script>

<template>
  <article class="app-card">
    <RouterLink :to="`/apps/${app.id}`" class="card-link" :aria-label="`查看 ${app.name} 详情`">
      <div
        class="app-icon"
        :class="{
          'icon-utility': app.category === '实用工具',
          'icon-economy': app.category === '经济工具',
          'icon-other': app.category !== '实用工具' && app.category !== '经济工具',
        }"
        aria-hidden="true"
      >
        {{ app.name.charAt(0) }}
      </div>

      <div class="card-title-row">
        <h3>{{ app.name }}</h3>

        <span class="category-tag">{{ app.category }}</span>
      </div>

      <p class="summary">{{ app.summary }}</p>

      <div class="card-footer">
        <span class="version"> v{{ app.version }} </span>

        <span class="detail-action">
          查看详情
          <span aria-hidden="true">-></span>
        </span>
      </div>
    </RouterLink>
  </article>
</template>

<style scoped>
.app-card {
  min-width: 0;
  height: 100%;
}

.card-link {
  display: flex;
  flex-direction: column;

  height: 100%;
  padding: 22px;

  border: 1px solid var(--color-border);
  border-radius: var(--radius-card);

  background: var(--color-surface);
  color: var(--color-text);

  text-decoration: none;

  box-shadow: var(--shadow-card);

  transition:
    transform 180ms ease,
    border-color 180ms ease,
    box-shadow 180ms ease;
}

.card-link:hover {
  transform: translateY(-2px);

  border-color: var(--color-border-brand);

  box-shadow: var(--shadow-card-hover);
}

.card-link:focus-visible {
  outline: 3px solid rgba(47, 125, 74, 0.28);
  outline-offset: 3px;

  border-color: var(--color-border);
}

.card-link:active {
  transform: translateY(-1px);
}

.app-icon {
  display: grid;
  place-items: center;

  width: 80px;
  height: 80px;

  margin-bottom: 22px;

  border-radius: 14px;

  color: #fff;

  font-size: 22px;
  font-weight: 80;
}

.icon-utility {
  background: var(--color-brand);
}

.icon-economy {
  background: #9a6b13;
}

.icon-other {
  background: #949d97;
}

.card-title-row {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;

  gap: 12px;
}

.card-title-row h3 {
  margin: 0;

  font-size: 20px;
  line-height: 1.3;
}

.category-tag {
  flex-shrink: 0;

  padding: 5px 8px;

  border-radius: 999px;

  background: var(--color-brand-soft);
  color: var(--color-brand-dark);

  font-size: 11px;
  font-weight: 700;
}

.summary {
  flex: 1;

  margin: 14px 0 26px;

  color: var(--color-text-secondary);

  font-size: 14px;
  line-height: 1.7;
}

.card-footer {
  display: flex;
  align-items: center;
  justify-content: space-between;

  gap: 16px;

  padding-top: 16px;

  border-top: 1px solid #edf1ee;
}

.version {
  color: var(--color-text-secondary);

  font-size: 12px;
}

.detail-action {
  color: var(--color-brand-dark);

  font-size: 13px;
  font-weight: 700;
}

.card-link:hover .detail-action {
  color: var(--color-brand);
}



</style>
