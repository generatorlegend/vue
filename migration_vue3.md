# Migrating from Vue 2 to Vue 3

## Introduction

Vue 3 brings significant improvements and new features to the Vue.js framework. This guide will help you migrate your Vue 2 applications to Vue 3 by highlighting key differences, introducing new features, and providing best practices for updating your existing code.

## Key Changes

### Composition API

Vue 3 introduces the Composition API, a new way to organize component logic. While the Options API is still supported, the Composition API offers better TypeScript integration and more flexible code organization.

Example:

```javascript
import { ref, computed, onMounted } from 'vue'

export default {
  setup() {
    const count = ref(0)
    const doubleCount = computed(() => count.value * 2)

    onMounted(() => {
      console.log('Component mounted')
    })

    function increment() {
      count.value++
    }

    return {
      count,
      doubleCount,
      increment
    }
  }
}
```

### Reactive System Changes

Vue 3 uses a proxy-based reactivity system, which offers better performance and more intuitive behavior.

- `ref` is used for primitive values
- `reactive` is used for objects

Example:

```javascript
import { ref, reactive } from 'vue'

const count = ref(0)
const state = reactive({
  user: {
    name: 'John Doe',
    age: 30
  }
})
```

### Multiple Root Elements

Vue 3 components can now have multiple root elements:

```vue
<template>
  <header>...</header>
  <main>...</main>
  <footer>...</footer>
</template>
```

### Teleport Component

Vue 3 introduces the `<Teleport>` component for rendering content outside the component's DOM tree:

```vue
<template>
  <div>
    <Teleport to="body">
      <modal-component />
    </Teleport>
  </div>
</template>
```

## Migration Steps

1. Update dependencies:
   - Replace `vue` with the latest Vue 3 version
   - Update `vue-router` and `vuex` to their Vue 3 compatible versions

2. Update the main app file:
   ```javascript
   import { createApp } from 'vue'
   import App from './App.vue'

   const app = createApp(App)
   app.mount('#app')
   ```

3. Review and update components:
   - Replace `beforeDestroy` with `beforeUnmount`
   - Update `v-model` usage (now uses `modelValue` prop and `update:modelValue` event)
   - Refactor mixins to use the Composition API

4. Update event handling:
   - `$on`, `$off`, and `$once` instance methods have been removed
   - Use an external event bus library or implement your own

5. Review and update your Vuex store:
   - Use `createStore` instead of `new Vuex.Store`

6. Update your router:
   - Use `createRouter` instead of `new VueRouter`

7. Review and update your templates:
   - `v-bind="$attrs"` now includes both attribute and listener bindings
   - Update any usage of filters (removed in Vue 3)

8. Test thoroughly and fix any remaining issues

## Best Practices

- Gradually migrate components to the Composition API
- Use the new `<script setup>` syntax for simpler component definitions
- Leverage TypeScript for improved type checking and developer experience
- Use the Vue 3 DevTools for debugging and performance optimization

## Conclusion

Migrating to Vue 3 requires some effort but offers significant benefits in terms of performance, maintainability, and developer experience. Take advantage of the new features and improvements to enhance your Vue.js applications.

For more detailed information on specific migration topics, refer to the official Vue 3 migration guide.