# CSS Variables

To define a variable globally, it is best to define it on the :root pseudo-element. In practice, this ends up referencing the html element, but using :root is a good way of maintaining obvious separation.

In the basic example below, we define our primary colour in the :root element and reference it later using var. Now if we want to change the primary colour across the site, we only need to change it in one place, rather than everywhere across the code.

```css
:root {
  --primary-color: #2a90e7;
}

body {
  background-color: var(--primary-color);
}

a {
  color: var(--primary-color);
}
```

Variables can be used anywhere you would normally write a string. In the simple example below, CSS variables are used within a calc, as a fallback font, and also to define part of an rgba colour.

```css
:root {
  --default-padding: 10px;
  --fallback-font: 'Courier New';
  --primary-color: 0, 0, 0;
}

h1 {
  padding: calc(var(--default-padding) * 2);
  font-family: 'NotARealFont', var(--fallback-font);
  color: rgba(var(--primary-color), 0.5);
}
```

## Accessing from Javascript
One feature that CSS variables offer, which preprocessors cannot, is the ability to easily access these variables from Javascript. To do this, simple call getPropertyStyle on the element's computed style, with the name of the variable you want. If you have defined your variables on root, then the element you want is document.documentElement.
```js
window.getComputedStyle(document.documentElement).getPropertyValue('--primary-color');
```