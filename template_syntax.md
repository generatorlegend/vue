# Template Syntax

Vue.js uses an HTML-based template syntax that allows you to declaratively bind the rendered DOM to the underlying Vue instance's data. All Vue.js templates are valid HTML that can be parsed by spec-compliant browsers and HTML parsers.

## Interpolations

### Text

The most basic form of data binding is text interpolation using the "Mustache" syntax (double curly braces):

```html
<span>Message: {{ msg }}</span>
```

The mustache tag will be replaced with the value of the `msg` property on the corresponding data object. It will also be updated whenever the data object's `msg` property changes.

### Raw HTML

Double mustaches interpret the data as plain text, not HTML. In order to output real HTML, you will need to use the `v-html` directive:

```html
<p>Using mustaches: {{ rawHtml }}</p>
<p>Using v-html directive: <span v-html="rawHtml"></span></p>
```

### Attributes

Mustaches cannot be used inside HTML attributes. Instead, use a `v-bind` directive:

```html
<div v-bind:id="dynamicId"></div>
```

For boolean attributes (their mere existence implies `true`), `v-bind` works a little differently:

```html
<button v-bind:disabled="isButtonDisabled">Button</button>
```

## Directives

Directives are special attributes with the `v-` prefix. Directive attribute values are expected to be a single JavaScript expression (with the exception of `v-for`, which will be discussed later).

### v-if

The `v-if` directive is used to conditionally render a block:

```html
<p v-if="seen">Now you see me</p>
```

### v-for

The `v-for` directive can be used to render a list of items based on an array:

```html
<ul>
  <li v-for="item in items">
    {{ item.text }}
  </li>
</ul>
```

### v-on

The `v-on` directive is used to attach event listeners to elements:

```html
<button v-on:click="doSomething">Click me</button>
```

### v-bind

As we've seen earlier, `v-bind` is used to dynamically bind one or more attributes, or a component prop to an expression:

```html
<!-- Bind an attribute -->
<img v-bind:src="imageSrc">

<!-- Shorthand -->
<img :src="imageSrc">
```

### v-model

You can use the `v-model` directive to create two-way data bindings on form input, textarea, and select elements:

```html
<input v-model="message" placeholder="edit me">
<p>Message is: {{ message }}</p>
```

## Special Attributes

### key

The `key` special attribute is primarily used as a hint for Vue's virtual DOM algorithm to identify VNodes when diffing the new list of nodes against the old list:

```html
<ul>
  <li v-for="item in items" :key="item.id">
    {{ item.text }}
  </li>
</ul>
```

### ref

The `ref` attribute is used to register a reference to an element or a child component:

```html
<input ref="input">
```

## Best Practices

1. Use `v-for` with a `key` attribute to help Vue identify which items have changed, been added, or been removed in a list.
2. Avoid using `v-if` and `v-for` on the same element due to priority issues. Instead, use a wrapper `<template>` element with `v-if`.
3. Use computed properties for complex logic in templates to keep them clean and efficient.
4. Use `v-bind` shorthand (`:`) and `v-on` shorthand (`@`) for more concise template code.
5. Prefer `v-if` over `v-show` when the condition doesn't change often, as `v-if` is "real" conditional rendering.

Remember, Vue's template syntax is designed to be readable and expressive while maintaining high performance. By following these guidelines and understanding the various template features, you can create efficient and maintainable Vue applications.