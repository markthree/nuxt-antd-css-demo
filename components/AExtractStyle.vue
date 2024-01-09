<script lang="ts" setup>
import { createCache, extractStyle } from "ant-design-vue"

const cache = createCache()

const app = useNuxtApp()

// ssr 时实时提取样式
// ssg 时预渲染提取样式
app.hook('app:rendered', () => {
  useHead({
    style: [extractStyle(cache, true)]
  })
})
</script>

<template>
  <a-style-provider :cache="cache">
    <slot />
  </a-style-provider>
</template>
