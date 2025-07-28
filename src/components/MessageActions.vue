<template>
  <div class="message-actions">
    <button
      v-if="isLastAssistantMessage"
      class="action-btn"
      @click="$emit('regenerate')"
      data-tooltip="重新生成"
    >
      <img :src="regenerateIcon" alt="regenerate" />
    </button>
    <button class="action-btn" @click="$emit('copy')" data-tooltip="复制">
      <img :src="isCopied ? successIcon : copyIcon" alt="copy" />
    </button>
    <button class="action-btn" @click="$emit('like')" data-tooltip="喜欢">
      <img :src="isLiked ? likeActiveIcon : likeIcon" alt="like" />
    </button>
    <button class="action-btn" @click="$emit('dislike')" data-tooltip="不喜欢">
      <img :src="isDisliked ? dislikeActiveIcon : dislikeIcon" alt="dislike" />
    </button>
    <span v-if="completionTokens" class="tokens-info">
      tokens: {{ completionTokens }}, speed: {{ speed }} tokens/s
    </span>
  </div>
</template>

<script setup>
import { defineProps } from 'vue'
import regenerateIcon from '@/assets/photo/重新生成.png'
import copyIcon from '@/assets/photo/复制.png'
import successIcon from '@/assets/photo/成功.png'
import likeIcon from '@/assets/photo/赞.png'
import likeActiveIcon from '@/assets/photo/赞2.png'
import dislikeIcon from '@/assets/photo/踩.png'
import dislikeActiveIcon from '@/assets/photo/踩2.png'

const props = defineProps({
  isLastAssistantMessage: { type: Boolean, default: false },
  isCopied: { type: Boolean, default: false },
  isLiked: { type: Boolean, default: false },
  isDisliked: { type: Boolean, default: false },
  completionTokens: { type: [Number, String], default: '' },
  speed: { type: [Number, String], default: '' }
})
</script>

<style scoped>
.message-actions {
  display: flex;
  gap: 0.5rem;
  margin-top: 0.5rem;
  padding-left: 1rem;
}
.action-btn {
  width: 1.5rem;
  height: 1.5rem;
  padding: 0;
  border: none;
  background: none;
  cursor: pointer;
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;
  position: relative;
}
.action-btn img {
  width: 1rem;
  height: 1rem;
  opacity: 1;
  transition: filter 0.2s;
}
.action-btn:hover {
  background-color: rgba(0, 0, 0, 0.05);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
}
.action-btn:hover img {
  filter: brightness(0.4);
}
.action-btn img[src*='2'] {
  filter: none;
}
.tokens-info {
  display: flex;
  gap: 0.5rem;
  color: var(--text-color-secondary);
  font-size: 0.75rem;
  background-color: #f3f4f6;
  padding: 0.25rem 0.5rem;
  border-radius: 0.25rem;
}
</style>
