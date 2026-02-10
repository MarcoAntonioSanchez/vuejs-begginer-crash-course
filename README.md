# Vue Begginer's crash course from OpanAI's chatGPT

## Level 0 - Fundamental's before getting into vue code

> _M. SÁNCHEZ:_
>
> Prepare a new mindset before writing any single line of code

---

### 1. What problem does Vue solve?

> _M. SÁNCHEZ:_
>
> Before Vue i just have **HTML** _(sructure)_, **CSS** _(styles)_ and **JS** _(logic)_ with UI state's handled by hand by my self. As the UI grows the code gets larger and larger, complicating states with a lot of files and a lot of conditions, wich require updates made by hand resulting on fragile code very hard to mantain.

Vue exists to solve **sync between state and UI**.

---

### 2. What is Vue really?

> _M. SÁNCHEZ:_
>
> A progressive framework. Meaning that can be used with the basics only and scale up to: **SPA** _(Single Page Application)_, **Routing** _(/subpage)_, **State management** _(active = null)_, **SSR** _(Server Side Rendering)_ and **Complex Apps / projects** _(professional level development)_.

**Vue won't force you** to all of these previously mentioned from day 1

---

### 3. What is SPA and why Vue fits well with it?

> _M. SÁNCHEZ:_
>
> **SPA** stands for: _Single Page Application_. This means: A single HTML document, changing content without a page refresh and, last but not least, the state resides in memory _(JS)_.

- **Classic flow**: User -> Change's state -> UI gets updated.
- **Without Vue**: The dev must do all this job _(classic flow)_ by hand.
- **With Vue**: State changes and Vue handles the UI for me _(dev)_.

---

### 4. Key concept: State

> _M. SÁNCHEZ:_
>
> If **i understand this** _(state as key concept)_... i **understand Vue**.

State = data representing the UI.

Mental sample (To-do):

```JS
todos = [
    { text: 'Learn Vue', done: false},
    { text: 'Make a commit', done: true}
]
```

**UI** is just a projection of the **State**. Vue lives to answer this single question: _If state changes... What should change on screen?_

---

### 5. Reactivity (Vue's super power)

What is reactivity?

> _M. SÁNCHEZ:_
>
> It's the capacity of: Detecting changes in data and react to it, automatically.

In Vue:

- Value changes.
- Vue detects it.
- Vue updates ONLY the necessary on the DOM.

Important:

- Vue DON'T re-render the whole page.
- Uses a virtual DOM.

---

### 6. Virtual DOM (smoke free)

Simple idea:

1. Vue have a virtual representation of the UI.
2. Changes state.
3. Vue compares: Before and After.
4. Only apply's the minimun changes to the real DOM.

Result:

- Performance.
- Declarative code.
- human-error reduction.

---

### 7. Declarative VS Imperative

Imperative (vanilla JS):

```JS
if (isLogged) {
    showMenu();
} else {
    hideMenu();
}
```

Declarative (Vue):

```JS
<Menu v-if="isLogged" />
```

I declare **what** happens... Vue decides **how** it's done.

---

### 8. Components (think in 'pieces')

Vue forces devs (for good) to think of:

- Small, Reusable and Isolated components
- With clear responsibillities

Mental sample (Todo SPA project):

- App
  - TodoForm
  - TodoList
    - TodoItem
  - Filters

This is **not a technical detail**... It's a **way of think of**.

---

### 9. What Vue does NOT do

Vue does **NOT**:

- Handles DB.
- Fetch for you.
- Decide arquitecture.
- And it doesn't save you from bad decisions either.

Vue **amplifies**:

- Good practices, leads to best results.
- Bad practices, leads to a quicker mess.

---

Final thoughts over level cero / 0 - Fundamentals: I should remember the following:

- Vue sync's state < - > UI (bidirectionally).
- UI it's a function of the state.
- Reactivity it's the core.
- Components are the base.
- Declarative > imperative.
- Vue it's not magic, it's arquitecture.

If tomorrow is added:

- "Backend".
- "Users".
- "Roles".

What should change?

- "The UI? The state?"
- "Or both?"

Vue it's mented to answer very well to this type of questions...

---

> 🐦‍⬛ _RVN:_
>
> Happy hacking 🚀

---
