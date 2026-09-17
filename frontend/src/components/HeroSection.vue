<script setup lang="ts">
import { ref } from 'vue'

const searchQuery = ref('')
</script>

<template>
  <section class="hero">
    MCPhone 应用商店

    <h1>发现适合你的APP</h1>

    <p>
      这里汇集由社区开发者上传的 MCPhone 脚本APP。
      应用在开放下载前都会经过审核，主要以ZIP的格式提供。 将ZIP放到/app文件夹里即可安装。
    </p>
    <form class="search-form" @submit.prevent>
      <input v-model="searchQuery" type="search" placeholder="搜索应用、功能或标签" />

      <button type="submit">搜索</button>
    </form>

    <p v-if="searchQuery">正在搜索：{{ searchQuery }}</p>
  </section>
</template>

<style scoped>
.hero {
  max-width: 900px;
  margin: 0 auto;
  padding: 80px 20px;
}

h1 {
  font-size: 48px;
}

p {
  max-width: 600px;
  color: #666;
  line-height: 1.7;
}

.search-form {
  display: flex;
  gap: 12px;
  max-width: 600px;
  margin-top: 24px;
}
.search-form input {
  flex: 1;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 8px;
}
.search-form button {
  padding: 12px 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  cursor: pointer;
}
</style>
