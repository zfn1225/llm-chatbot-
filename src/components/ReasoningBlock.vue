<template>
  <div v-if="reasoningContent" class="reasoning-block">
    <div class="reasoning-toggle" @click="toggle">
      <img :src="thinkingIcon" alt="thinking" />
      <span>深度思考</span>
      <el-icon class="toggle-icon" :class="{ 'is-expanded': expanded }">
        <ArrowDown />
      </el-icon>
    </div>
    <div v-if="expanded" class="reasoning markdown-body" v-html="renderedReasoning"></div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { ArrowDown } from '@element-plus/icons-vue'
import thinkingIcon from '@/assets/photo/深度思考.png'
import { renderMarkdown } from '@/utils/markdown'

const props = defineProps({
  reasoningContent: {
    type: String,
    required: true
  }
})

const expanded = ref(true)
const toggle = () => (expanded.value = !expanded.value)
const renderedReasoning = computed(() => renderMarkdown(props.reasoningContent))
</script>

<style scoped>
.reasoning-toggle {
  display: flex;
  align-items: center;
  gap: 4px;
  padding: 4px 8px;
  margin-left: 16px;
  margin-bottom: 8px;
  cursor: pointer;
  width: fit-content;
  border-radius: 4px;
  background-color: #eef4ff;
  transition: background-color 0.2s;
}
.reasoning-toggle img {
  width: 14px;
  height: 14px;
}
.reasoning-toggle span {
  font-size: 13px;
  color: #3f7af1;
}
.toggle-icon {
  font-size: 12px;
  color: #3f7af1;
  transition: transform 0.2s;
}
.toggle-icon.is-expanded {
  transform: rotate(180deg);
}
.reasoning {
  margin-bottom: 8px;
  margin-left: 16px;
  padding: 0 16px;
  background-color: #fff;
  border-left: 3px solid #dfe2e5;
  color: #8b8b8b;
  font-size: 14px;
  line-height: 1.6;
}
</style>
