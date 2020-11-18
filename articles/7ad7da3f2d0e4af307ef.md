---
title: "Vue3にもなったしemitは使わないでPropで関数を子コンポーネントに渡す"
emoji: "🚀"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [Vue.js,JavaScript,TypeScript,Zenn]
published: false
---

### Parent
```ts
<template>
  <Child
    :click="clickEventHandler"
  />
</template>

<script lang="ts">
import { defineComponent, reactive, computed } from "vue"
import Child from '@/components/Child.vue'

export default defineComponent({
  components: { Child },
  setup() {
    return {
      clickEventHandler: () => console.log('Click!')
    }
  }
})
</script>

```

### Child
```ts
<template>
  <button @click="click">
    Click!
  </button>
</template>

<script lang="ts">
import { defineComponent, SetupContext } from 'vue'

export default defineComponent({
  props: {
    click: {
      type: Function,
      required: true
    }
  },
})
</script>
```
