<template>
  <div class="demo-box">
    <div class="show">
      <slot />
    </div>
    <div class="meta">
      <div class="title">{{ title }}</div>
      <div class="desc">
        <p>{{ desc }}</p>
      </div>
    </div>
  </div>
</template>

<script lang="tsx">
import { defineComponent, ref } from 'vue';
interface PreCode {
  source: string;
  highlight: string;
}


export default defineComponent({
  name: 'DemoBox',
  props: {
    title: {
      type: String,
      default: ''
    },
    desc: {
      type: String,
      default: ''
    },
    codeType: {
      type: String,
      default: ''
    },
    href: {
      type: String,
      default: ''
    },
  }
});
</script>

<style scoped>
.demo-box {
  display: inline-block;
  width: 100%;
  margin-bottom: 16px;
  border: 1px solid var(--border-color);
  border-radius: 2px;
  transition: border-color 0.2s ease-in-out;
}

.demo-box:target {
  border-color: var(--primary-color);
}

.demo-box .show {
  padding: 20px 14px;
  border-bottom: 1px solid var(--border-color);
  max-height: 300px;
  overflow-y: auto;
}

.demo-box .meta {
  position: relative;
  border-radius: 0 0 2px 2px;
}

.demo-box .meta .title {
  position: absolute;
  top: -14px;
  margin-left: 16px;
  padding: 1px 8px;
  background-color: var(--white-color);
  border-radius: 2px 2px 0 0;
}

.demo-box .meta .desc {
  padding: 18px 24px 12px;
}

.demo-box .meta .actions {
  padding: 12px 0;
  border-top: 1px dashed var(--dash-border-color);
  opacity: 0.7;
  text-align: center;
  transition: opacity 0.3s;
  user-select: none;
}

.demo-box .meta .actions:hover {
  opacity: 1;
}

.demo-box .meta .actions .act {
  margin-right: 8px;
}

.demo-box .highlight-wrap {
  border-radius: 0 0 2px 2px;
}

.demo-box .highlight-wrap .highlight {
  padding: 16px 32px;
}
</style>
