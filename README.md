# Vue Begginer's crash course

## Level 2 - Inside Vue

> _M. SÁNCHEZ:_
>
> Template, directives and reactive render

This level's goal is to fully understand how Vue transforms state in UI, how "reads" the template and how components works without touching (by hand) the DOM. Also, this level is foundational: if gets dominated, the rest feels natural.

---

### 1. The template is not the regular HTML

Looks similar, but `<template>` is:

- Declarative.
- Reactive.
- Vue controlled.

The template is a **function of the state.**

Mindset: UI = f(state)

Dev decides _what_ should be shown. Vue decides _how_ to do it.

---

### 2. Interpolation `{{  }}`

Works to show data:

`<p>{{ title }}</p>`

Important rules:

- Inside, resides JavaScript.
- Expressions only.
- Gets evaluated once the state changes.

GOOD practice:

```JS
{{ count + 1 }}
{{ isDone ? 'Done' : 'Pending' }}

```

BAD practice:

```
{{ if (x) {...} }}
{{ let a = 5 }}
```

---

### 3. Directives: Instructions to Vue

Directives tell Vue how a node should be treated.

`v-bind` (binding attributes):

`<img v-bind:src="imageUrl" />`

Shortcut:

`<img :src="imageUrl">`

Mindset:

> _M. SÁNCHEZ:_
>
> This attribute depends on the state

Do not _set_ attributes manually. Let them react.

`v-on` (events)

`<button v-on:click="increment">+</button>`

Shortcut:

`<button @click="increment">+</button>`

Vue listens to the event and runs **logic**, not the DOM.

---

### 4. Conditional render

```JS
v-if

<p v-if="isLogged">Bienvenido</p>
```

- The element exists or not
- Its created and destroyed

`v-else` / `v-else-if`

```JS
<p v-if="loading">Loading...</p>
<p v-else>Ready</p>
```

```JS
v-show

<p v-show="isLogged">Bienvenido</p>
```

- Exist since always.
- The only change is `display: none`.

Practical rule:

- Frequent changes, use v-show.
- Occasional changes, use v-if.

---

### 5. Lists with `v-for` (very important)

```JS
<li v-for="todo in todos" :key="todo.id">
    {{ todo.text }}
</li>
```

The `:key` it's not optative. Vue uses the key for:

- Node's identification.
- Render's optimization.
- Good to Avoid visual bugs.

DON'T:

`:key="index"`

INSTEAD, DO:

`:key="todo.id"`

---

### 6. State and methods (base concept)

Without entering to the composition API, key concept is:

- State: reactive data.
- Methods: functions that change the state.

Event -> Method -> State changes -> Vue updates the UI.

DONT'S:

- DOM Manipulation.
- "Forced" updates.

---

### 7. Vue re-renders... everything?

Short answer **no**, but Vue do:

- Detects whats changed.
- Compares virtual DOM.
- Updates **necessary's only**.

And this is why:

- No worrys for premature performance issues.
- Gain focus over arquitecture.

---

### 8. Common anti-patterns (avoid them from now on)

Heavy logic on the template:

`{{ calculateTotal(items, tax, discount) }}`

Use of Vue as jQuery:

`document.querySelector(...)`

Ambiguous states:

`status = 1 // que es 1?`

Clearance gets the best out of Vue.

---

**Final thoughts** over level two / 2 - Inside Vue:

- Template is declarative.
- `{{  }}` just for expressions.
- `v-bind` connects state -> attributes.
- `v-on` connects events -> logic.
- `v-if` and `v-for` controlls -> render.
- UI reacts to state not to the DOM.

---

> 🐦‍⬛ _RVN:_
>
> Happy hacking 🚀

---
