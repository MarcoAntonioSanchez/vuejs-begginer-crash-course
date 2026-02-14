# Vue Begginer's crash course

## Level 4 - Real componentization and communication

> _M. SÁNCHEZ:_
>
> Here, crafting "components" stops and system design beggins.

Level's goals:

- Think in components as responsibilities units.
- Understanding **unidirectional data flow**.
- Mastering:
  - `props`.
  - `emit`.
- Avoid unnecessary couplings.
- Consolidates a frontend arquitect mindset.

---

### 1. The absolute Vue rule: One-Way data flow

The right Vue flow is:

Father -> `props` -> Son
Son -> `emit` -> Father

Never the way arround. If this gets broken, then:

- Clearance gets broken.
- Maintenance gets broken.
- Scaffold gets broken.

Vue forces you to a clean arquitecture.

---

### 2. What is a component? (for real)

A component is not:

> "A .vue file".

A component is:

> A visual responsibility unit + encapsulated logic.

There's always room for questions like:

- What does it do?
- What writes?
- What communicates?
- What shouldn't happen?

If it know's too much -> it's wrongly desing.

---

### 3. `props` - decent communication

In the father:

`<TodoItem :todo="todo" />`

In the son:

```HTML
<script setup>
    defineProps({
        todo: Object
    })
</script>
```

Important concepts:

- `props` are **readonly**.
- Dont mod them.
- Respect the data controlled by the father.

If props are modified directly -> bad design.

---

### 4. `emit` - ASC communcation

The son DOESN'T mod the global state. The son communicates intention.

In the son:

```HTML
<script setup>
const emit = defineEmits(['toggle'])

function handleClick() {
  emit('toggle')
}
</script>

```

In the father:

```JS
<TodoItem
  :todo="todo"
  @toggle="toggleTodo(todo.id)"
/>

```

The right mindset. The son says:

> "Hey father, something change"

The father says:

> "I handle the state"

This is clear arquitecture.

---

### 5. The right design for a To-Do (arquitectural vision)

Future structure should look like this:

- App
  - TodoContainer
    - TodoForm
    - TodoList
      - TodoItem
    - TodoFilters

Responsibilities:

- `TodoForm` -> creates chores only.
- `TodoList` -> renderize list.
- `TodoItem` -> representation.
- `TodoFilters` -> change view.
- `TodoContainer` -> handles state

The state lives the highest possible.

---

### 6. Single Responsibility Principle (SRP)

Bad design:

- TodoList.vue
  - handles state
  - saves in localStorage
  - make validations
  - filters
  - render

Good design:

- State inside container
- Presentation inside sons
- Reusable logic inside _composables_ (further on)

---

### 7. Typed props (pro mindset)

Although TypeScript won't be in for now, get this into your mindset:

```JS
defineProps({
  todo: {
    type: Object,
    required: true
  }
})
```

This is:

- Documented
- Protected
- Bugs prevented

---

### 8. Common errors on this level (must avoid them)

- Son modifies props (DON'T).
- Son imports the state from the father (DON'T).
- Too many props = Signs a bad design (DON'T).
- Bad names on events. e.g. `clickEventDataChangeThing` (DON'T).

Cleared and convetioned names (DO):

- `add` (BETTER).
- `remove` (BETTER).
- `toggle` (BETTER).
- `update` (BETTER).

---

### 9. Senior mindset (very importnat)

When you find your self designing components, aks your self:

- Is this component reusable?
- It is coupled to a specific context?
- It's prepared for isoleted testing?

If the answer to the three of them is **YES**, this is the way.

---

**Final thoughts** over level four / 4 - Real componentization and communication:

Proof that the dev mindset it's evolving in a good way with this level, will be:

- Flow it's unidirectional.
- Props go down.
- Emits go up.
- State lives up on the top.
- Components have a clear responsibilitie.
- Won't brake at encapsulation.

---

> 🐦‍⬛ _RVN:_
>
> Happy hacking 🚀
