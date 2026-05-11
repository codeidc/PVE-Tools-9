<script setup>
import { useData } from 'vitepress'
import SponsorWall from './SponsorWall.vue'

const { frontmatter } = useData()
</script>

<template>
  <div v-if="frontmatter.my_features" class="home-content-container">
    <div class="main-content">
      <div class="features-grid">
        <div v-for="feature in frontmatter.my_features" :key="feature.title" class="feature-card">
          <div class="feature-icon" :class="feature.iconClass"></div>
          <h2 class="feature-title">{{ feature.title }}</h2>
          <p class="feature-details">{{ feature.details }}</p>
        </div>
      </div>
    </div>

    <div class="sponsor-sidebar">
      <SponsorWall />
    </div>
  </div>
</template>

<style scoped>
.home-content-container {
  display: flex;
  flex-direction: row;
  gap: 32px;
  max-width: 1152px;
  margin: 0 auto;
  padding: 48px 24px;
}

.main-content {
  flex: 2;
  min-width: 0;
}

.sponsor-sidebar {
  flex: 1;
  min-width: 0;
}

/* 功能卡片网格 */
.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 16px;
}

.feature-card {
  background-color: var(--vp-c-bg-soft);
  padding: 24px;
  border-radius: 12px;
  border: 1px solid var(--vp-c-bg-soft);
  transition: border-color 0.25s, background-color 0.25s;
  height: 100%;
}

.feature-card:hover {
  border-color: var(--vp-c-brand);
}

.feature-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 48px;
  height: 48px;
  margin-bottom: 20px;
  border-radius: 8px;
  background-color: var(--vp-c-default-soft);
  transition: all 0.25s;
  color: var(--custom-icon-color);
}

.feature-card:hover .feature-icon {
  color: var(--vp-c-brand);
}

.feature-icon::before {
  content: '';
  width: 24px;
  height: 24px;
  background-color: currentColor;
  -webkit-mask-size: contain;
  -webkit-mask-repeat: no-repeat;
  -webkit-mask-position: center;
  mask-size: contain;
  mask-repeat: no-repeat;
  mask-position: center;
}

.icon-rocket::before {
  -webkit-mask-image: url('/icons/rocket-launch-outline.svg');
  mask-image: url('/icons/rocket-launch-outline.svg');
}
.icon-sparkles::before {
  -webkit-mask-image: url('/icons/sparkles.svg');
  mask-image: url('/icons/sparkles.svg');
}
.icon-harddrive::before {
  -webkit-mask-image: url('/icons/harddisk.svg');
  mask-image: url('/icons/harddisk.svg');
}
.icon-gpu::before {
  -webkit-mask-image: url('/icons/video-card.svg');
  mask-image: url('/icons/video-card.svg');
}
.icon-clock::before {
  -webkit-mask-image: url('/icons/clock-outline.svg');
  mask-image: url('/icons/clock-outline.svg');
}
.icon-more::before {
  -webkit-mask-image: url('/icons/dots-horizontal.svg');
  mask-image: url('/icons/dots-horizontal.svg');
}

.feature-title {
  font-size: 1.15rem;
  font-weight: 600;
  margin-bottom: 8px;
  line-height: 1.4;
  background: none;
  -webkit-text-fill-color: initial;
}

.feature-details {
  font-size: 0.9rem;
  color: var(--vp-c-text-2);
  line-height: 1.6;
}

/* 响应式 */
@media (max-width: 960px) {
  .home-content-container {
    flex-direction: column;
    padding: 24px;
  }
}
</style>
