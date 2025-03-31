# Vue CLI Usage Guide

## Introduction

Vue CLI is a powerful tool for setting up and managing Vue.js projects. This guide will walk you through the process of using Vue CLI to create, develop, and customize your Vue.js applications.

## Installation

Before you can use Vue CLI, you need to install it globally on your system. Open your terminal and run the following command:

```bash
npm install -g @vue/cli
```

## Creating a New Project

To create a new Vue.js project, use the following command:

```bash
vue create my-project
```

Replace `my-project` with your desired project name. Vue CLI will prompt you to choose a preset or manually select features for your project.

### Preset Options

1. Default (Vue 2): Babel + ESLint
2. Default (Vue 3): Babel + ESLint
3. Manually select features

For beginners, choosing one of the default presets is recommended. For more advanced users or specific project requirements, select "Manually select features" to customize your project setup.

## Project Structure

After creating your project, you'll see a directory structure similar to this:

```
my-project/
├── node_modules/
├── public/
├── src/
│   ├── assets/
│   ├── components/
│   ├── App.vue
│   └── main.js
├── .gitignore
├── babel.config.js
├── package.json
└── README.md
```

## Development

To start the development server, navigate to your project directory and run:

```bash
npm run serve
```

This command will start a local development server, usually at `http://localhost:8080`. You can now begin developing your Vue.js application with hot-reload enabled.

## Adding Plugins

Vue CLI allows you to add plugins to your project after creation. To add a plugin, use the following command:

```bash
vue add <plugin-name>
```

For example, to add the Vuex state management library:

```bash
vue add vuex
```

## Customizing the Build Process

You can customize your project's build process by creating a `vue.config.js` file in the root of your project. Here's an example of how to modify the webpack configuration:

```javascript
// vue.config.js
module.exports = {
  configureWebpack: {
    plugins: [
      // Add your custom webpack plugins here
    ]
  },
  chainWebpack: config => {
    // Modify the webpack config chain here
  }
}
```

## Building for Production

When you're ready to build your application for production, run:

```bash
npm run build
```

This command will create a `dist` folder with your optimized production build.

## Conclusion

Vue CLI provides a robust set of tools for developing Vue.js applications. By following this guide, you should now be able to create, develop, and customize your Vue.js projects efficiently. For more detailed information, refer to the [official Vue CLI documentation](https://cli.vuejs.org/).