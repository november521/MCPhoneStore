<script setup lang="ts">
import { useRoute } from 'vue-router'
import { apps } from '../data/apps'

const route = useRoute()
const appId = Number(route.params.id)
const app = apps.find((item) => item.id === appId)
</script>

<template>
  <main class="detail-page">
    <div class="detail-container">
      <RouterLink to="/" class="back-link">
        <span aria-hidden="true">←</span>
        返回应用列表
      </RouterLink>

      <template v-if="app">
        <header class="detail-hero">
          <div
            class="detail-icon"
            :class="{
              'icon-utility': app.category === '实用工具',
              'icon-economy': app.category === '经济工具',
              'icon-other': app.category !== '实用工具' && app.category !== '经济工具',
            }"
            aria-hidden="true"
          >
            {{ app.name.charAt(0) }}
          </div>

          <div class="detail-heading">
            <span class="category-tag">
              {{ app.category }}
            </span>

            <h1>{{ app.name }}</h1>

            <p class="detail-summary">
              {{ app.summary }}
            </p>
          </div>
        </header>

        <div class="detail-layout">
          <div class="detail-main">
            <section class="content-card">
              <h2>应用介绍</h2>

              <p>
                {{ app.description }}
              </p>
            </section>

            <section class="content-card">
              <h2>安装方法</h2>

              <p>
                下载应用
                <code>.zip</code>
                文件后，将文件放入 MCPhone 的
                <code>/app</code>
                文件夹即可自动安装。
              </p>
            </section>
          </div>

          <aside class="info-card">
            <h2>应用信息</h2>

            <dl>
              <div>
                <dt>版本</dt>
                <dd>v{{ app.version }}</dd>
              </div>

              <div>
                <dt>作者</dt>
                <dd>{{ app.author }}</dd>
              </div>

              <div>
                <dt>分类</dt>
                <dd>{{ app.category }}</dd>
              </div>

              <div>
                <dt>更新时间</dt>
                <dd>{{ app.updatedAt }}</dd>
              </div>
            </dl>
          </aside>
        </div>
      </template>

      <section v-else class="not-found">
        <div class="not-found-icon" aria-hidden="true">?</div>

        <h1>应用不存在</h1>

        <p>你访问的应用不存在， 可能已经被删除或者地址有误。</p>

        <RouterLink to="/" class="primary-link"> 返回应用商店 </RouterLink>
      </section>
    </div>
  </main>
</template>

<style scoped>
.detail-page {
  min-height: calc(100vh - 72px);
}

.detail-container {
  max-width: var(--content-width);

  margin: 0 auto;
  padding: 42px 24px 80px;
}

.back-link {
  display: inline-flex;
  align-items: center;

  gap: 7px;

  margin-bottom: 34px;

  color: var(--color-text-secondary);

  text-decoration: none;

  font-size: 14px;
  font-weight: 600;

  transition:
    color 180ms ease,
    transform 180ms ease;
}

.back-link:hover {
  color: var(--color-brand-dark);

  transform: translateX(-2px);
}

.back-link:focus-visible {
  outline: 3px solid rgba(47, 125, 74, 0.28);
  outline-offset: 4px;

  border-radius: 6px;
}

.detail-hero {
  display: flex;
  align-items: center;

  gap: 24px;

  margin-bottom: 36px;
}

.detail-icon {
  display: grid;

  flex-shrink: 0;
  place-items: center;

  width: 82px;
  height: 82px;

  border-radius: 20px;

  color: #fff;

  font-size: 34px;
  font-weight: 800;

  box-shadow: var(--shadow-card);
}

.icon-utility {
  background: var(--color-brand);
}

.icon-economy {
  background: #b98925;
}

.icon-other {
  background: #667069;
}

.category-tag {
  display: inline-block;

  margin-bottom: 10px;
  padding: 5px 9px;

  border-radius: 999px;

  background: var(--color-brand-soft);
  color: var(--color-brand-dark);

  font-size: 12px;
  font-weight: 700;
}

.detail-hero h1 {
  margin: 0 0 8px;

  font-size: clamp(34px, 5vw, 52px);

  line-height: 1.1;
  letter-spacing: -0.035em;
}

.detail-summary {
  max-width: 680px;

  margin: 0;

  color: var(--color-text-secondary);

  font-size: 16px;
  line-height: 1.7;
}

.detail-layout {
  display: grid;

  grid-template-columns:
    minmax(0, 2fr)
    minmax(260px, 1fr);

  align-items: start;

  gap: 24px;
}

.detail-main {
  display: grid;

  gap: 18px;
}

.content-card,
.info-card {
  border: 1px solid var(--color-border);
  border-radius: var(--radius-card);

  background: var(--color-surface);

  box-shadow: var(--shadow-card);
}

.content-card {
  padding: 28px;
}

.content-card h2,
.info-card h2 {
  margin: 0 0 18px;

  color: var(--color-text);

  font-size: 19px;
}

.content-card p {
  margin: 0;

  color: var(--color-text-secondary);

  line-height: 1.8;
}

.content-card code {
  padding: 3px 7px;

  border-radius: 6px;

  background: var(--color-brand-soft);
  color: var(--color-brand-dark);

  font-family: 'SFMono-Regular', Consolas, monospace;

  font-size: 0.92em;
}

.info-card {
  position: sticky;
  top: 96px;

  padding: 24px;
}

.info-card dl {
  margin: 0;
}

.info-card dl div {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;

  gap: 20px;

  padding: 13px 0;

  border-bottom: 1px solid #edf1ee;
}

.info-card dl div:last-child {
  border-bottom: 0;
}

.info-card dt {
  color: var(--color-text-secondary);

  font-size: 13px;
}

.info-card dd {
  margin: 0;

  color: var(--color-text);

  font-size: 13px;
  font-weight: 700;

  text-align: right;
}

.not-found {
  display: flex;
  align-items: center;
  flex-direction: column;

  max-width: 620px;

  margin: 60px auto 0;
  padding: 64px 28px;

  border: 1px solid var(--color-border);
  border-radius: 24px;

  background: var(--color-surface);

  text-align: center;

  box-shadow: var(--shadow-card);
}

.not-found-icon {
  display: grid;
  place-items: center;

  width: 68px;
  height: 68px;

  margin-bottom: 22px;

  border-radius: 18px;

  background: var(--color-brand-soft);
  color: var(--color-brand-dark);

  font-size: 30px;
  font-weight: 800;
}

.not-found h1 {
  margin: 0 0 10px;

  font-size: 30px;
}

.not-found p {
  max-width: 420px;

  margin: 0 0 26px;

  color: var(--color-text-secondary);

  line-height: 1.7;
}

.primary-link {
  display: inline-flex;
  align-items: center;
  justify-content: center;

  min-height: 46px;

  padding: 0 20px;

  border-radius: var(--radius-control);

  background: var(--color-brand);
  color: #fff;

  text-decoration: none;
  font-weight: 700;

  transition:
    background 180ms ease,
    transform 180ms ease;
}

.primary-link:hover {
  background: var(--color-brand-dark);
}

.primary-link:focus-visible {
  outline: 3px solid rgba(47, 125, 74, 0.28);
  outline-offset: 3px;
}

.primary-link:active {
  transform: scale(0.97);
}

@media (max-width: 700px) {
  .detail-container {
    padding: 28px 16px 60px;
  }

  .detail-hero {
    align-items: flex-start;
    flex-direction: column;

    gap: 18px;
  }

  .detail-icon {
    width: 70px;
    height: 70px;

    border-radius: 18px;

    font-size: 28px;
  }

  .detail-layout {
    grid-template-columns: 1fr;
  }

  .info-card {
    position: static;
  }
}
</style>
