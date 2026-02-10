# Vue Begginer's crash course

## Level 1 - Environment and base structure

> _M. SÁNCHEZ:_
>
> The right way from the beginning

This level's goal is to fully understand how a Vue app is born, what each file does what and why the strcture it's how it is. After this level Vue won't be a black-box anymore.

---

### 1. Why Vue 3 + Vite?

Vue 3:

- Modern API.
- Better performance.
- More TS support.
- Native composition API.

Vue 2 it's **not the right** way for fresh projects.

Vite (a bundler). Vite it's not Vue, Vite it's a tool that:

- Setups development server.
- Compile projects.
- Build to production.

Why Vite?

- Instant development server.
- Real HMR (Hot Module Replacement).
- Anonymous setting.
- Current Vue standard ecosystem.

Vue **recommends Vite officially**.

---

### 2. Project creation (what really happens)

Typical command:

`npm create vue@latest`

This command:

1. Download's official template.
2. Setup Vue.
3. Prepare Vue 3.
4. Sets a **opinione but flexible base**.

No magic here, just scaffolding.

---

### 3. Folder structure (critic lecture)

Typical base structure:

- Project/
  - index.html
  - package.json
  - vite.config.js
  - src/
    - main.js
    - App.vue
    - assets/

Let's get over it file by file.

---

### 4. index.html (way more important than you think)

`<div id='app'></div>`

Here it is where Vue **gets mounted** (id = app)

Key concept:

- Vue doesn't generates the initial HTML.
- Vue it's mounted over an existing container.

This is key for:

- SPA (Single Page Applications)
- SSR (Server Side Rendering)
- Integrations

---

### 5. main.js (the real entry point)

Typical code sample:

```JS
import { createApp } from 'vue'
import App from './App.vue'

createApp(App).mount(#app)

```

What this mean:

- createApp(App), creates a Vue application.
- App, root component.
- .mount(#app), connencts Vue with the real DOM.

Everything that gets through the app **lives under** `App.vue`

---

### 6. App.vue (root component)

Minimum sample:

```JS
<template>
    <h1>Hello Vue</h1>
</template>

<script>
    export default {
        name: 'App'
    }
</script>
```

Important concept:

- App.vue
  - Should not contain complex logic.
  - Act's like a root layout.
  - Orchestrates the components.

If `App.vue` gets giant, something it's wrong.

---

### 7. Single File Components (SFC)

A `.vue` is an SFC. Advantages:

- Cohesion.
- Clear scope.
- Encapsulated styles.
- Breve maintenance.

Vue **prefers cohesion over artifitial separation.**

---

### 8. Complete boot flow (mental)

Visualized like:

`index.html` -> `main.js` -> `createApp(App)` -> `App.vue` -> `Child components`

Understanding this flow, means **understanding every Vue App**.

---

### 9. What not to touch yet (common temptations)

- DONT setup Webpack
- DONT install 20 dependencies
- DONT implement Tailwind yet
- DONT think of router nor store

Understand **the base**, first.

---

**Final thoughts** over level one / 1 - Environment and base structure: I already know the following, with clearance:

- Vite it's not equal to Vue.
- index.html starts the app.
- App.vue is the root.
- Everything is a component.
- No arbitrary structure.

---

> 🐦‍⬛ _RVN:_
>
> Happy hacking 🚀

---
