<template>
  <div v-if="files && files.length > 0" class="files-container">
    <div v-for="file in files" :key="file.url" class="file-item">
      <!-- 图片预览 -->
      <div v-if="file.type === 'image'" class="image-preview">
        <img :src="file.url" :alt="file.name" />
      </div>
      <!-- 文件预览 -->
      <div v-else class="file-preview">
        <el-icon><Document /></el-icon>
        <span class="file-name">{{ file.name }}</span>
        <span class="file-size">{{ (file.size / 1024).toFixed(1) }}KB</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { Document } from '@element-plus/icons-vue'
import { defineProps } from 'vue'

const props = defineProps({
  files: {
    type: Array,
    required: true,
    validator: (arr) => arr.every(f => typeof f.url === 'string' && typeof f.name === 'string' && typeof f.size === 'number' && typeof f.type === 'string')
  }
})
</script>

<style scoped>
.files-container {
  margin-bottom: 8px;
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}
.file-item .image-preview {
  max-width: 200px;
  border-radius: 8px;
  overflow: hidden;
}
.file-item .image-preview img {
  display: block;
  max-width: 100%;
  height: auto;
}
.file-item .file-preview {
  padding: 8px;
  background-color: #f4f4f5;
  border-radius: 8px;
  display: flex;
  align-items: center;
  gap: 8px;
}
.file-item .file-name {
  max-width: 120px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
.file-item .file-size {
  color: #909399;
  font-size: 12px;
}
</style>
