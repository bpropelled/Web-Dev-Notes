## CSS Notes and Tricks

### Make Label Clickable for checks, readios and text input fields
Making checkbox labels clickable via <label>

[2014-04-02] dev, html
The <label> element has been around for a while, but I still don’t see enough websites use it. In lets you make labels of checkboxes and radio buttons clickable.

Without <label>, you need to click directly on a checkbox in order to toggle it:

 Some option
```html
<input type="checkbox"> Some option
```

If you use <label>, the text after the checkbox becomes clickable:
 Some option
 ```html
<label><input type="checkbox"> Some option</label>
'''
For styling via CSS, you may sometimes need another, more verbose, variant of this element: You can link a label to its control by referring to the control’s ID via the label’s attribute for (thanks to Evgeny Gorbachev for mentioning this use case for this attribute).
 Some option
 ```html
<style>
input:checked + label { color: green; }
</style>
<input id="check1" type="checkbox">
<label for="check1">Some option</label>
<label> works the same for radio buttons (type="radio"). It also works for text fields where you can use the labels to focus (activate) the fields (thanks, Paul Vorbach):
Text: 
```html


### CSS Media Query Template
```css
/*
 * Author: http://stuffandnonsense.co.uk/blog/about/hardboiled_css3_media_queries/
 */

/* Smartphones (portrait and landscape) ----------- */
@media only screen 
and (min-device-width : 320px) 
and (max-device-width : 480px) {
/* Styles */
}

/* Smartphones (landscape) ----------- */
@media only screen 
and (min-width : 321px) {
/* Styles */
}

/* Smartphones (portrait) ----------- */
@media only screen 
and (max-width : 320px) {
/* Styles */
}

/* iPads (portrait and landscape) ----------- */
@media only screen 
and (min-device-width : 768px) 
and (max-device-width : 1024px) {
/* Styles */
}

/* iPads (landscape) ----------- */
@media only screen 
and (min-device-width : 768px) 
and (max-device-width : 1024px) 
and (orientation : landscape) {
/* Styles */
}

/* iPads (portrait) ----------- */
@media only screen 
and (min-device-width : 768px) 
and (max-device-width : 1024px) 
and (orientation : portrait) {
/* Styles */
}

/* Desktops and laptops ----------- */
@media only screen 
and (min-width : 1224px) {
/* Styles */
}

/* Large screens ----------- */
@media only screen 
and (min-width : 1824px) {
/* Styles */
}

/* iPhone 4 ----------- */
@media
only screen and (-webkit-min-device-pixel-ratio : 1.5),
only screen and (min-device-pixel-ratio : 1.5) {
/* Styles */
}
```
## Centering trick (simple)
```css
.content {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```

## Use TRANSFORM for animatinmg items instead of position methods like top, left and margin.  The transform will provide much better performance and much smoother animations
[Explanation]('https://www.paulirish.com/2012/why-moving-elements-with-translate-is-better-than-posabs-topleft/')
```css
.test {
transform: translate(x, y)
}

```

## Make a circe easily
```css
.circle {
    width: 100px;
    height: 100px;
    border-radius: 50%;
}
```

## Calculate CSS Unit Values
A calc() expression lets you give complex length values to CSS properties. For example, want a div to be 80% wide, minus 40px? Just do this:
```css
div { width: calc(80% - 40px); }
```