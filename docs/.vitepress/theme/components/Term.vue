<template>
  <span class="term">
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
        class="term-content-block"
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
.term {
  position: relative;
}

.term-block {
  /* 术语样式 */
  color: var(--vp-c-brand);
  cursor: pointer;
  display: inline-block;
}

.term-content-block {
  /* view & layout */
  position: absolute;
  z-index: var(--vp-z-index-layout-top);
  transition: opacity 0.2s;
  /* view-other */
  max-width: 90vw;
  width: max-content;
  margin-top: 24px;
  margin-bottom: 24px;
  /* border */
  border: 1px solid var(--vp-c-divider);
  background-color: var(--vp-c-bg-soft);
  border-radius: 8px;
  padding: 3px 20px 3px 20px;
  box-shadow: 0 4px 4px rgba(63, 53, 70, 0.32);
  color: var(--vp-c-text-2);
}
</style>
