---
title: Alpine.js - old school is coming back...
author: Shawn Wang
theme:
  name: dark
  override:
    default:
      colors:
        foreground: "beeeff"
    footer:
      style: template
      center: "NCKU-CCS"
      right: "🚀 {current_slide} / {total_slides}"
      # Optional!
---

# Alpine.js - Your new, lightweight, JavaScript framework.

<!-- column_layout: [1, 1] -->

<!-- column: 0 -->

```html
<script src="alpine.js" defer>
</script>
<div x-data="{ open: false }">
    <button @click="open = true">
      Expand
    </button>
 
    <span x-show="open">
        Content...
    </span>
</div>
```

<!-- column: 1 -->

<!-- pause -->
- Don't need to bundle or build tooling
<!-- pause -->
  -  `defer`: parallel downloading & executed after the page has finished parsing.
<!-- pause -->

- simple - js version TailwindCSS
<!-- pause -->
  - 18 directives / attributes
  - 9 magics / properties
  - 3 globals / methods.
<!-- pause -->
- lightweight - cdn 43k/16k(gz)
<!-- pause -->
- Vue reactivity system
- extensions / plugins / components

<!-- reset_layout -->



<!--end_slide-->

## Doc & Components

Doc:
- [Alpine](https://alpinejs.dev/start-here)
- [Alpine.js 繁體中文文件](https://hackmd.io/@monkenWu/S14j-NqsU) 中文文件v2
- [10_reasons](https://www.codemotion.com/magazine/frontend/ten-reasons-why-i-think-alpine-js-can-do-magic/)
- [from_vue](https://medium.com/@jogarcia/alpinejs-for-the-vuejs-developer-5b39fd21c2c1)

---

Components:
- [Alpine UI Components](https://alpinejs.dev/components) 
- [Toolbox](https://www.alpinetoolbox.com/)
- [HyperUI](https://js.hyperui.dev/)


<!-- end_slide -->

### x-data - defines reactive data for that component to reference.

<!-- column_layout: [1, 1] -->

<!-- column: 0 -->

```html
<div x-data="{
    foo: 'bar',
    open: false,
    get isOpen() { return this.open },
    toggle() {
      this.open = ! this.open
    }
  }">
  <span x-text="foo"></span>
  <div x-data="{ bar: 'baz' }">
    <span x-text="foo"></span>
    <div x-data="{ foo: 'bob' }">
      <span x-text="foo"></span>
    </div>
  </div>
  <button @click="toggle()">Toggle</button>
  <div x-show="isOpen">
    Content...
  </div>
</div>
```
<!-- column: 1 -->

- Scope - available to all element children (even nested)
  - Single-element components
- Methods
  - x-data is evaluated as a normal JavaScript object
  - Getters
    - ```get isOpen() { return this.open }```
- Data-less components
  - ```<div x-data>```



<!--end_slide-->






## compare to other frameworks

- vs React - (-) JSX (-) VDOM (-) SPA
- vs Vue - (-) VDOM (-) SPA
  - (=) template-wise (=) MPA (=) Reactivity
  - (*) component scope
- vs htmx(*) - (-) make HTTP requests/response (=) MPA
- vs astrojs(*)/nextjs - (-) SSG/SSR (=) MPA


<!--end_slide-->

### vs React

```
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<h1>Hello, world!</h1>);

function MyButton() {
  return (
    <button>I'm a button</button>
  );
}
```

<!-- column_layout: [1, 1] -->

<!-- column: 0 -->

```
<div>
  {isLoggedIn ? (
    <AdminPanel />
  ) : (
    <LoginForm />
  )}
</div>
```
<!-- column: 1 -->
- JSX

<!-- reset_layout -->

<!--end_slide-->

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

<!--end_slide-->

### vs htmx

```  
  <script src="https://unpkg.com/htmx.org@1.9.10"></script>
  <!-- have a button POST a click via AJAX -->
  <button hx-post="/clicked" hx-swap="outerHTML">
    Click Me
  </button>
```

- to AJAX, CSS Transitions, WebSockets and Server Sent Events directly in HTML, using attributes
- simplicity and power of hypertext

<!--end_slide-->

### vs astrojs

<!-- column_layout: [1, 1] -->

<!-- column: 0 -->
- Component Islands
- Zero JavaScript - Input JS Output Html
- Highly customizable
- UI- agnostic (meaning it is interoperable with a lot of UI frameworks)
- Server-first API (SSR/SSG)
  - Server Side Rendering
  - Static Site Generator
- Edge ready

<!-- column: 1 -->
```
---
const pageTitle = "About Me";
---  
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>{pageTitle}</title>
  </head>
  <body>
   ...
  </body>
</html>
```

<!-- reset_layout -->

<!--end_slide-->


old school is coming back...
<!-- pause -->
TALL stack - Tailwind CSS / AlpineJS / Laravel / Livewire

