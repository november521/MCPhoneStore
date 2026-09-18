<script setup lang="ts">
import { useRoute } from 'vue-router'
import { apps } from '../data/apps'

const route = useRoute()
const appId = Number(route.params.id)
const app = apps.find((item) => item.id === appId)
</script>

<template>
  <main class="app-detail">
    <RouterLink to="/" class="back-link"> ←返回应用列表 </RouterLink>

    <section v-if="app" class="detail-content">
      <div class="detail-main">
        <span class="category">{{ app.category }}</span>

        <h1>{{ app.name }}</h1>

        <p class="summary">{{ app.summary }}</p>

        <h2>应用介绍</h2>

        <p>{{ app.description }}</p>

        <h2>安装方法</h2>

        <p>下载应用.zip文件后，将.zip放入 MCPhone 的 /app 文件夹即可自动安装。</p>
      </div>

      <aside class="app-meta">
        <h2>应用信息</h2>

        <p>版本：{{ app.version }}</p>
        <p>分类：{{ app.category }}</p>
        <p>作者：{{ app.author }}</p>
        <p>更新时间：{{ app.updatedAt }}</p>
      </aside>
    </section>

    <section v-else class="empty-state">
      <h1>应用不存在</h1>

      <p>你访问的应用不存在，可能已经被删除或者地址有误。</p>

      <RouterLink to="/"> 返回应用列表 </RouterLink>
    </section>
  </main>
</template>

<style scoped>
.app-detail {
  max-width: 900px;
  margin: 0 auto;
  padding: 48px 20px;
}

.back-link {
  display: inline-block;
  margin-bottom: 24px;
}

.detail-content {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 32px;
}
.detail-main h1 {
  font-size: 48px;
  margin-bottom: 16px;
}

.summary {
  color: #666;
  line-height: 1.7;
}

.category {
  color: #666;
}

.detail-main p {
  line-height: 1.7;
}

.app-meta {
  border: 1px solid #ddd;
  border-radius: 12px;
  padding: 20px;
}
.empty-state {
  padding: 80px 0;
  text-align: center;
}

@media (max-width: 700px) {
  .detail-content {
    grid-template-columns: 1fr;
  }

  .detail-main h1 {
    font-size: 36px;
  }
}
</style>
