# Vue Reactivity Explained

Vue's reactivity system is one of its core features, allowing your application to automatically update the UI when the underlying data changes. This guide will explain how Vue's reactivity works and how to use it effectively in your applications.

## Table of Contents

1. [Introduction to Reactivity](#introduction-to-reactivity)
2. [Reactive Data](#reactive-data)
3. [Computed Properties](#computed-properties)
4. [Watchers](#watchers)
5. [Best Practices](#best-practices)

## Introduction to Reactivity

Vue's reactivity system is based on the observer pattern. When you create a Vue instance or component, Vue walks through all of its properties and converts them into getter/setters using Object.defineProperty. This allows Vue to track when these properties are accessed or modified.

## Reactive Data

### Creating Reactive Objects

Vue automatically makes the data in your components reactive. Here's how you can create reactive objects:

```javascript
import { reactive } from 'vue'

const state = reactive({
  count: 0,
  message: 'Hello, Vue!'
})
```

The `reactive` function creates a reactive copy of the object. Any changes to `state` will now trigger updates in your component.

### Limitations

It's important to note that Vue 2's reactivity system has some limitations:

1. It cannot detect property addition or deletion on objects.
2. It cannot detect direct index-based mutations on arrays.

To overcome these limitations, Vue provides special methods like `Vue.set` and `Vue.delete`.

```javascript
import Vue from 'vue'

const obj = {
  foo: 'bar'
}

// Adding a new property
Vue.set(obj, 'newProp', 123)

// Deleting a property
Vue.delete(obj, 'foo')
```

## Computed Properties

Computed properties are cached, reactive data properties. They only re-evaluate when one of their reactive dependencies changes.

```javascript
import { reactive, computed } from 'vue'

const state = reactive({
  count: 0
})

const doubleCount = computed(() => state.count * 2)

console.log(doubleCount.value) // 0
state.count++
console.log(doubleCount.value) // 2
```

Computed properties are great for complex logic that you don't want to repeat in your template.

## Watchers

Watchers allow you to observe changes on a specific data property and perform side effects in response.

```javascript
import { ref, watch } from 'vue'

const count = ref(0)

watch(count, (newValue, oldValue) => {
  console.log(`Count changed from ${oldValue} to ${newValue}`)
})

count.value++
// Console: "Count changed from 0 to 1"
```

Watchers are useful when you want to perform asynchronous or expensive operations in response to changing data.

## Best Practices

1. Use computed properties for complex calculations that depend on reactive data.
2. Use watchers for side effects like API calls or DOM manipulation.
3. Avoid mutating reactive data in computed properties.
4. Remember to use `Vue.set` or `Vue.delete` when adding or removing properties from reactive objects.
5. When possible, declare all your reactive properties upfront in the `data` option of your component.

By understanding and effectively using Vue's reactivity system, you can create more efficient and maintainable applications. The automatic tracking of dependencies and updates allows you to focus on your application logic rather than manually managing DOM updates.