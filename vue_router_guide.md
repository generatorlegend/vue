# Vue Router Guide

Vue Router is the official routing library for Vue.js applications. It enables the creation of single-page applications (SPAs) by mapping components to routes and handling navigation between them.

## Table of Contents

1. [Installation](#installation)
2. [Basic Setup](#basic-setup)
3. [Route Configuration](#route-configuration)
4. [Navigation](#navigation)
5. [Navigation Guards](#navigation-guards)
6. [Lazy Loading Routes](#lazy-loading-routes)

## Installation

To install Vue Router, you can use npm or yarn:

```bash
npm install vue-router
```

or

```bash
yarn add vue-router
```

## Basic Setup

To use Vue Router in your Vue.js application, you need to create a router instance and pass it to your Vue instance:

```javascript
import Vue from 'vue'
import VueRouter from 'vue-router'
import Home from './components/Home.vue'
import About from './components/About.vue'

Vue.use(VueRouter)

const router = new VueRouter({
  routes: [
    { path: '/', component: Home },
    { path: '/about', component: About }
  ]
})

new Vue({
  router,
  render: h => h(App)
}).$mount('#app')
```

## Route Configuration

Routes are defined as an array of objects, each specifying a path and its corresponding component:

```javascript
const routes = [
  { path: '/', component: Home },
  { path: '/about', component: About },
  { path: '/user/:id', component: User },
  { path: '*', component: NotFound }
]
```

You can also define nested routes using the `children` property:

```javascript
const routes = [
  {
    path: '/user/:id',
    component: User,
    children: [
      { path: 'profile', component: UserProfile },
      { path: 'posts', component: UserPosts }
    ]
  }
]
```

## Navigation

Vue Router provides several ways to navigate between routes:

1. Declarative: Using `<router-link>` component
   ```html
   <router-link to="/about">About</router-link>
   ```

2. Programmatic: Using `$router.push()` method
   ```javascript
   this.$router.push('/about')
   ```

## Navigation Guards

Navigation guards are hooks that allow you to control the navigation flow. There are three types of navigation guards:

1. Global guards
2. Per-route guards
3. In-component guards

Example of a global before guard:

```javascript
router.beforeEach((to, from, next) => {
  if (to.matched.some(record => record.meta.requiresAuth)) {
    if (!auth.loggedIn()) {
      next({
        path: '/login',
        query: { redirect: to.fullPath }
      })
    } else {
      next()
    }
  } else {
    next()
  }
})
```

## Lazy Loading Routes

For better performance, you can lazy-load route components. This means the component will only be loaded when the route is visited:

```javascript
const User = () => import('./components/User.vue')

const router = new VueRouter({
  routes: [
    { path: '/user/:id', component: User }
  ]
})
```

This approach uses dynamic imports and webpack code-splitting to create separate chunks for each route component.

---

For more detailed information and advanced usage, please refer to the [official Vue Router documentation](https://router.vuejs.org/).