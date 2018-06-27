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
here is a list of all 18 properties
```
grid
grid-area
grid-auto-columns
grid-auto-flow
grid-auto-rows
grid-column
grid-column-end
grid-column-gap
grid-column-start
grid-gap
grid-row
grid-row-end
grid-row-gap
grid-row-start
grid-template
grid-template-areas
grid-template-columns
grid-template-rows
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
  background-color: #1EAAFC;
  background-image: linear-gradient(130deg, #6C52D9 0%, #1EAAFC 85%, #3EDFD7 100%);
  box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
  color: #fff;
  border-radius: 4px;
  border: 6px solid #171717;
}

.item1 {
  background: black;
    background-image: linear-gradient(130deg, pink 0%, white 85%, white 100%);
}
.item:hover {
  transform: scale(1.025);
   transition: all 2s linear;
}
```

## The FR (Fraction) Unit 

A fraction of the available space in the grid container

Create a row with 3 equal columns

```css
.wrapper {
display: grid;
grid-template-columns: 1fr 1fr 1fr;
grid-template-rows: 50vh 50vh;
}
```
or if you are repeating fr units you can use the "repeat" method

```css
.wrapper {
display: grid;
grid-template-columns: repeat(3,1fr);
grid-template-rows: 50vh 50vh;
}
```
#### Mixing Units
```css
.wrapper {
display: grid;
grid-template-columns: 100px 10% 1fr;
grid-template-rows: 50vh 50vh;
}
```
or like this piece of magic
```css
.wrapper {
display: grid;
grid-template-columns: 100px repeat(2,1fr);
grid-template-rows: 50vh 50vh;
}
```
When declaring track sizes, you can use fixed sizes with units such as px and em. You can also use flexible sizes such as percentages or the fr unit. 


## Positioning Items
you can position items using the track lines, starting at one from top left for certical and horizontal

here .item1 will be positioned in the second row and the second column
```css
.item1 {
  grid-row-start: 2;
  grid-row-end: 3;
  grid-column-start: 2;
  grid-column-end: 3;
}
 ```     
Shorthand property
We can also rewrite this with shorthand properties:

```css
.item1 {
  grid-row: 2 / 3;
  grid-column: 2 / 3;
}
```

doing this will be like budding in line.  The grid cell numbers take over your spot and you sit between where you budded back in line to.  eg. 2,3,4,5,1,6

## Grid Areas

This is really cool.  So instead of positioning line by line, there is this thing you can do by arranging the grid by using names.  Here is an example
```css
.container {
  display: grid;
  width: 100%;
  height: 600px;
  grid-template-columns: 200px 1fr 1fr;
  grid-template-rows: 80px 1fr 1fr 100px;
  grid-gap: 1rem;
  grid-template-areas:
      "header header header"
      "sidebar content-1 content-1"
      "sidebar content-2 content-3"
      "footer footer footer";
}
```

```html
<div class="container">
  <div class="header">header</div>
  <div class="sidebar">sidebar</div>
  <div class="content-1">Content-1</div>
  <div class="content-2">Content-2</div>
  <div class="content-3">Content-3</div>
  <div class="footer">footer</div>
</div>
```

```css
.header {
  grid-area: header;
}

.sidebar {
  grid-area: sidebar;
}

.content-1 {
  grid-area: content-1;
}

.content-2 {
  grid-area: content-2;
}

.content-3 {
  grid-area: content-3;
}

.footer {
  grid-area: footer;
}
      
```
We can also name some or all of those grid lines when defining a grid. This allows us to use those names instead of grid lines. To name a grid line, simply add the name in square brackets:
To name a grid line, provide the name in square brackets:

```css
.container {
  display: grid;
  width: 100%;
  height: 600px;
  grid-gap: 1rem;
  grid-template-columns:
    [main-start sidebar-start] 200px
    [sidebar-end content-start] 1fr
    [column3-start] 1fr
    [content-end main-end];
  grid-template-rows:
    [row1-start] 80px
    [row2-start] 1fr
    [row3-start] 1fr
    [row4-start] 100px
    [row4-end];
}
 ```        
 
 we can use those names when placing items. Let's recreate our basic layout using named lines, instead of line numbers: 
 ```css
 .header {
  grid-column: main-start / main-end;
  grid-row: row1-start / row2-start;
}

.sidebar {
  grid-column: sidebar-start / sidebar-end;
  grid-row: row2-start / row4-start;
}

.content-1 {
  grid-column: content-start / content-end;
  grid-row: row2-start / row3-start;
}

.content-2 {
  grid-column: content-start / column3-start;
  grid-row: row3-start / row4-start;
}

.content-3 {
  grid-column: column3-start / content-end;
  grid-row: row3-start / row4-start;
}

.footer {
  grid-column: main-start / main-end;
  grid-row: row4-start / row4-end;
}
```


