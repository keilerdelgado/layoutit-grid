<template>
  <div :class="['code-sidebar', { active: currentView === 'code' }]">
    <a
      class="btn-github"
      rel="noopener"
      target="_blank"
      aria-label="View source on GitHub"
      href="https://github.com/Leniolabs/layoutit-grid"
    >
      <IconGithub />
    </a>
    <slot name="body" />
    <BrandBanner />
  </div>
</template>

<script setup>
import { currentView } from '../../store.js'
</script>

<style scoped lang="postcss">
.code-sidebar {
  //overflow: auto;
  text-align: left;
  color: var(--color-gray-lightest);
  padding: 105px 15px;
  height: 100vh;
  transition: transform 0.2s ease-in;
  position: relative;
  @media (max-width: 769px) {
    transform: translateX(100%);
    width: 100%;
    background: var(--color-gray-darkest);
    position: fixed;
    right: 0;
    bottom: 0;
    top: 48px;
    height: calc(100vh - 48px);
    &.active {
      transform: translateX(0em);
    }
  }
}

.btn-github {
  position: fixed;
  top: 0;
  right: 0;
  opacity: 0.8;
  transition: opacity 0.1s linear;
  &:hover {
    opacity: 0.9;
  }
}
</style>
