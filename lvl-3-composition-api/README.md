# Vue Begginer's crash course

## Level 3 - Composition API

> _M. SÁNCHEZ:_
>
> Here, memorizes stop and understanding beggins.

This level's goal is to fully understand the following:

- Why the API composition exists.
- How does it really works.
- Modern reactivity mindset.
- When to use `ref`, `reactive`, `computed`, `watch`.
- How everything connects to the template.

---

### 1. Why does the API composition exist?

Before (API Options):

```JS
export default {
    data(),
    methods: {},
    computed: {},
    watch: {},
}
```

Problems here on big projects:

- Relationed logic separated in diffrent blocks.
- Reusable logic gets complicated.
- Gigant components.

API composition groups logic per functionallity, not per type.

---

### 2. `setup()` - the new center

In Vue 3 everything starts here:

```JS
export default {
    setup() {
        // logics lives here
    }
}
```

But the real modern, resides in the use of:

```JS
<script setup>
</script>
```

`script setup` is officially sintetic sugar with recomendation

Use this from now on.

---

### 3. Real reactivity: `ref()`

The reactive basic unit

```JS
import { ref } from 'vue'

const count = ref(0)
```

Important concept:

`ref()` returns a reactive object with a `.value` property

Internally:

```JS
{
    value: 0
}
```

In JS:

`count.value++`

In template:

`{{ count }}`

In template `.value` it's NOT needed.

How to know when to use `ref()`?

- Numbers.
- Strings.
- Booleans.
- Simple values.

> _M. SÁNCHEZ:_
>
> If primitive -> ref.

---

### 4. Reactive objects: `reactive()`

```JS
import { reactive } from 'vue'

const state = reactive({
    name: 'Raven',
    level: 3,
})
```

`.value` doesn't exist here.

`state.level++`

How to know when to use `reactive`?

- Complex objects.
- Forms.
- Grouped structures.

> _M. SÁNCHEZ:_
>
> 80% of the times `ref` is used, even for arrays.

Yes, **even with arrays**:

`const todos = ref([])`

---

### 5. `computed()` - derive status

This is getting elegant:

```JS
import { computed } from 'vue'

const completeCount = computed(() =>
    todos.value.filter(t => t.done).length
)
```

Characteristics:

- Gets calculated automatically.
- Result gets cached.
- Is reactive.

Do never put heavy logic in the template. Use `computed`.

---

### 6. `watch()` - reaction to changes

When logic needs to be runned over changes?

```JS
import { watch } from 'vue'

watch(count, (newVal, oldVal) => {
    console.log('Change:', newVal)
})
```

Use it when:

- Saving on localStorage.
- API calls.
- Running side effects.

> _M. SÁNCHEZ:_
>
> If you can use `computed`, don't use `watch`.

---

### 7. Life's cycle (lifecycle hooks)

In API composition:

```JS
import { onMounted } from 'vue'

onMounted(() => {
    console.log('Mounted component')
})
```

Common hooks:

- `onMounted`
- `onUpdate`
- `onUnmounted`

Use it when necessary only.

---

### 8. The right mindset with API composition

The modern pattern now is:

- `ref` / reactive -> state
- `computed` -> devirated state
- _methods_ -> regular functions
- `watch` -> side effects
- `<template>` -> state's projection

No more artifitial separation.

---

### 9. Minimum modern sample

```JS
<script setup>
    import { ref, computed } from 'vue'

    const count = ref(0)

    function increment() {
        count.value++
    }

    const double = computed(() => count.value * 2)
</script>

<template>
    <p>Count: {{ count }}</p>
    <p>Double: {{ double }}</p>
    <button @click="increment">+</button>
</template>
```

This is pro modern Vue. Key diffrence:

- Options API

  > Where do i put this?

- Composition API
  > What logic belongs together? This difference changes everything.

---

**Final thoughts** over level three / 3 - Composition API:

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
