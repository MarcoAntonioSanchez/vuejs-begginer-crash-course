# Vue Begginer's crash course

## Level 5 - Professional arquitecture and composables

> _M. SÁNCHEZ:_
>
> From a visual component to a Vue software arquitecture.

Level's goals:

Separate's:

- User interface (UI).
- State.
- Business logic.
- Infrastructure.

For the projec to:

- Scale.
- Be legible.
- Be testeable.
- Have no dependency to hugh components.

---

### 1. The tipycal problem (WON'T)

Most common error sample, about a `TodoApp.vue`:

- Handles state.
- Uses localStorage to save.
- Validates form.
- Filters tasks.
- Renders list.
- Controlls UI.

Works... but this is a time bomb. In a real project this will get unmaintenable.

---

### 2. Solution: Layers (backend mindset in the frontend)

Let's divide responsibilites:

`UI` (components) -> `Orquestation` (views / containers) -> `Reusable logic` (composables) -> `Infrastructure` (services) -> `Pured utilities` (utils)

Vue works better when it's used like this.

---

### 3. New folder structure

From now on, the Todo project should evolve like this:

- src/
  - components/
    - ui/
    - todo/
  - composables/
    - useTodos.js
  - services/
    - storage.service.js
  - utils/
    - filters.js
  - views/
    - TodoView.vue
  - App.vue

Not decoration only, each folder represents an arquitectonic layer.

---

### 4. What is a composable?

> _M. SÁNCHEZ:_
>
> A composable is: a function that encapsulates reactivity state + reusable logic.

Start's with: `use`. e.g.

```JS
export function useTodos() {
    const todos = ref([])

    function addTodo(text) {
        todos.value.push({
            id: Date.now(),
            text,
            done: false
        })
    }

    return { todos, addTodo }
}
```

A composable won't depend on the UI. That's the power.

---

### 5. Critic diffrence

**Component**: Render's interface.

**Composable**: Contains behavior.

The composable lives despite the UI changes.

---

### 6. Services - Infrastructure

Heres relies all the _external_

- localStorage.
- API.
- fetch.
- backend.

e.g.

```JS
export function saveTodos(todos) {
    localStorage.setItem('todos', JSON.stringify(todos))
}
```

Why it separates? Because tomorrow can be changed on:

- API REST.
- IndexedDB.
- Firebase.

And this wat, the UI won't even notice.

---

### 7. Utils - Pure functions

It doesn't have state nor Vue:

```JS
export function filterComplete(todos) {
  return todos.filter(t => t.done)
}
```

This is pure JavaScript.

---

### 8. Real flow (now)

Your Vue app should start looking like this:

Component UI -> use's composable -> composable use's service -> service access storage

Now this do count as arquitecture.

---

### 9. Immediatly benefits

After this i could:

- Reuse logic between pages.
- Change UI without breaking logic.
- Test without DOM.
- Ease backend migration.
- Implement `Pinia` without refactoring everything.

This is the diffrence between a demo project and a professional project.

---

**Final thoughts** over level five / 5 - Professional arquitecture and composables:

If this is all cleared, i just crossed the barrier of:

- Components = UI.
- Composables = reactive logic.
- Services = infrastructure.
- Utils = pure functions.
- Real separation of concerns.

---

> 🐦‍⬛ _RVN:_
>
> Happy hacking 🚀
