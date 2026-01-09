<template>
  <span class="term-with-tooltip">
    <!-- 术语部分 -->
    <span
      class="term-block"
      @mouseenter="isHovered = true"
      @mouseleave="isHovered = false"
    >
      <slot></slot>
    </span>

    <transition>
      <span
        v-if="isHovered"
        class="content-block"
        @mouseenter="isHovered = true"
        @mouseleave="isHovered = false"
      >
        <slot name="tip"></slot>
      </span>
    </transition>
  </span>
</template>

<script setup lang="ts">
import { ref } from "vue";

const isHovered = ref(false);
</script>

<style scoped>
.term-with-tooltip {
  position: relative;
  display: inline-flex;
  flex-direction: column;
}

.term-block {
  /* 术语样式 */
  color: var(--vp-c-brand);
  cursor: pointer;
  display: inline-block;
}

.content-block {
  position: absolute !important;
  width: max-content !important;
  transition: opacity 0.2s;

  bottom: 75%;
  border: 1px solid var(--vp-c-divider);
  background-color: var(--vp-c-bg-soft);
  border-radius: 8px;
  padding: 3px 20px 3px 20px;
  color: var(--vp-c-text-2);
  max-width: 90vw;
  z-index: var(--vp-z-index-layout-top);
  box-shadow: 0 4px 4px rgba(63, 53, 70, 0.32);
  margin-bottom: 8px;
}
</style>
