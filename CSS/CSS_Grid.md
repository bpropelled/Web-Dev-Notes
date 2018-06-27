## CSS Grid 

## Getting started
the frst thing you do to get started with CSS grid is to add the display: grid property to an element

```css
.wrapper {
display: grid;
}
```

Next you will need to define the rows and columns of your grid
```css
.wrapper {
display: grid;
/* Create a 3 Column x 2 row grid */
grid-template-columns: 150px 150px 150px;
grid-template-rows: 100px 100px;
}
```

and you can define the gutter gap, the space between the "cells"
```css
.wrapper {
display: grid;
/* Create a 3 Column x 2 row grid */
grid-template-columns: 150px 150px 150px;
grid-template-rows: 100px 100px;
grid-gap:25px;
}
```

or you could manually set the column and row gap individually

```css
.wrapper {
display: grid;
/* Create a 3 Column x 2 row grid */
grid-template-columns: 150px 150px 150px;
grid-template-rows: 100px 100px;
grid-column-gap: 25px;
grid-row-gap: 50px;

}
```

Now you can add items to your grid and watch the magic
```html
<div class="wrapper">
  <div class="item item1"></div>
  <div class="item"></div>
  <div class="item"></div>
  <div class="item"></div>
  <div class="item"></div>
  <div class="item"></div>
</div>
```

```css
.wrapper {
  width: 100%;
  background: white;
  border: 1px solid red;
  display: grid;
  grid-template-columns: 50% auto auto;
  grid-template-rows: 50vh 50vh;
  grid-gap: 25px;
}
.item {
  border: 2px solid blue;
  background: #c3c3c3;
}

.item1 {
  background: black;
}
```