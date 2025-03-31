# Getting Started with Vue.js

Vue.js is a progressive JavaScript framework for building user interfaces. This guide will help you get started with Vue.js, covering installation, basic usage, and introducing core concepts.

## Installation

There are several ways to install Vue.js:

### 1. Using CDN

The easiest way to start using Vue.js is to include it via a CDN:

```html
<script src="https://cdn.jsdelivr.net/npm/vue@2.6.14/dist/vue.js"></script>
```

For production, use the minified version:

```html
<script src="https://cdn.jsdelivr.net/npm/vue@2.6.14"></script>
```

### 2. Using npm

For larger projects, we recommend using npm:

```bash
npm install vue
```

### 3. Using Vue CLI

For a full-featured build setup, use the official Vue CLI:

```bash
npm install -g @vue/cli
vue create my-project
cd my-project
npm run serve
```

## Basic Usage

Here's a simple example of using Vue.js:

```html
<div id="app">
  {{ message }}
</div>

<script>
new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
</script>
```

This will display "Hello Vue!" on the page.

## Core Concepts

### 1. Components

Components are reusable Vue instances with a name. Here's a basic component:

```javascript
Vue.component('my-component', {
  template: '<div>A custom component!</div>'
})
```

### 2. Directives

Directives are special attributes with the `v-` prefix. For example:

```html
<p v-if="seen">Now you see me</p>
```

### 3. Reactivity

Vue's reactivity system automatically updates the DOM when data changes:

```javascript
var vm = new Vue({
  data: {
    message: 'Hello'
  }
})

// Changing `message` will update the DOM
vm.message = 'Hello World!'
```

## Next Steps

This guide covers the basics of Vue.js. To dive deeper, explore:

- The Vue.js [official documentation](https://v2.vuejs.org/v2/guide/)
- Vue Router for [Single-Page Applications](https://router.vuejs.org/)
- Vuex for [state management](https://vuex.vuejs.org/)

Happy coding with Vue.js!