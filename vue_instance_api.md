# Vue Instance API

## Overview

The Vue instance is the core of every Vue application. It serves as the root component and provides access to various properties and methods that allow you to control your application's behavior. This document covers the essential parts of the Vue instance API, including lifecycle hooks, data, methods, computed properties, and watch options.

## Creating a Vue Instance

To create a new Vue instance, use the `Vue` constructor:

```javascript
const vm = new Vue({
  // options
})
```

## Instance Properties and Methods

### Data

The `data` option is used to define reactive properties on the Vue instance. These properties are accessible via `this` inside the instance's methods and computed properties.

```javascript
const vm = new Vue({
  data: {
    message: 'Hello, Vue!'
  }
})

console.log(vm.message) // 'Hello, Vue!'
```

### Methods

The `methods` option allows you to define methods that can be called from your Vue instance. These methods can be used in directive expressions, or called from other instance methods.

```javascript
const vm = new Vue({
  data: {
    count: 0
  },
  methods: {
    increment() {
      this.count++
    }
  }
})

vm.increment()
console.log(vm.count) // 1
```

### Computed Properties

Computed properties are cached, reactive data properties for your Vue instance. They only re-evaluate when one of their reactive dependencies changes.

```javascript
const vm = new Vue({
  data: {
    firstName: 'John',
    lastName: 'Doe'
  },
  computed: {
    fullName() {
      return `${this.firstName} ${this.lastName}`
    }
  }
})

console.log(vm.fullName) // 'John Doe'
```

### Watch

The `watch` option allows you to watch for changes in your data and react accordingly. This is useful for performing asynchronous operations in response to changing data.

```javascript
const vm = new Vue({
  data: {
    question: ''
  },
  watch: {
    question(newQuestion, oldQuestion) {
      this.getAnswer()
    }
  },
  methods: {
    getAnswer() {
      // Perform some asynchronous operation
    }
  }
})
```

## Lifecycle Hooks

Vue instances go through a series of initialization steps when they are created. During this process, they also run functions called lifecycle hooks, giving users the opportunity to add their own code at specific stages.

Here are the main lifecycle hooks:

- `beforeCreate`: Called synchronously immediately after the instance has been initialized, before data observation and event/watcher setup.
- `created`: Called synchronously after the instance is created. At this stage, the instance has finished processing the options which means the following have been set up: data observation, computed properties, methods, watch/event callbacks. However, the mounting phase has not been started, and the `$el` property will not be available yet.
- `beforeMount`: Called right before the mounting begins: the `render` function is about to be called for the first time.
- `mounted`: Called after the instance has been mounted, where `el` is replaced by the newly created `vm.$el`.
- `beforeUpdate`: Called when data changes, before the DOM is patched.
- `updated`: Called after a data change causes the virtual DOM to be re-rendered and patched.
- `beforeDestroy`: Called right before a Vue instance is destroyed. At this stage the instance is still fully functional.
- `destroyed`: Called after a Vue instance has been destroyed. When this hook is called, all directives of the Vue instance have been unbound, all event listeners have been removed, and all child Vue instances have also been destroyed.

Example usage:

```javascript
const vm = new Vue({
  data: {
    message: 'Hello, Vue!'
  },
  created() {
    console.log('Instance created!')
  },
  mounted() {
    console.log('Instance mounted!')
  }
})
```

## Instance Properties

Vue instances expose several useful properties and methods. These can be accessed within your component's methods, computed properties, and lifecycle hooks.

- `$data`: The data object that the Vue instance is observing.
- `$props`: The props the component received.
- `$el`: The root DOM element that the Vue instance is managing.
- `$options`: The instantiation options used for the current Vue instance.
- `$parent`: The parent instance, if the current instance has one.
- `$root`: The root Vue instance of the component tree.
- `$slots`: Used to access content distributed by slots.
- `$refs`: An object of DOM elements and component instances, registered with `ref` attributes.

Example:

```javascript
const vm = new Vue({
  el: '#app',
  data: {
    message: 'Hello'
  },
  mounted() {
    console.log(this.$data.message) // 'Hello'
    console.log(this.$el) // The root DOM element
  }
})
```

## Conclusion

The Vue instance API provides a powerful and flexible way to build interactive web applications. By understanding and effectively using lifecycle hooks, data, methods, computed properties, and watch options, you can create complex and reactive user interfaces with ease.

Remember to consult the official Vue.js documentation for more detailed information and advanced usage of the Vue instance API.