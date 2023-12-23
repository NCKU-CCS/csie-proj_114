# Alpine.js

- Don't need bundle or build tooling
- simple - 15 attributes, 6 properties, and 2 methods.
- lightweight - cdn
- Vue reactivity system
- extensions / plugins / components
  - https://alpinejs.dev/components / https://www.alpinetoolbox.com/ / https://js.hyperui.dev/

https://www.codemotion.com/magazine/frontend/ten-reasons-why-i-think-alpine-js-can-do-magic/
https://medium.com/@jogarcia/alpinejs-for-the-vuejs-developer-5b39fd21c2c1

```
<script src="//unpkg.com/alpinejs" defer></script>
 
<div x-data="{ open: false }">
    <button @click="open = true">Expand</button>
 
    <span x-show="open">
        Content...
    </span>
</div>
```

## compare to other frameworks

- vs React:
- vs Vue:
- vs htmx:
- vs astrojs/nextjs:
- old school is back / TALL stack


### vs React

```
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<h1>Hello, world!</h1>);
```

### vs Vue

- 重新認識 Vue.js 008 天絕對看不完的 Vue.js 3.0 指南 https://book.vue.tw/
- 簡化版 vue, petite-vue

```
<script setup>
import { ref } from 'vue'

const msg = ref('Hello World!')
</script>

<template>
  <h1>{{ msg }}</h1>
  <input v-model="msg" />
</template>
```

### vs htmx


### vs astrojs



