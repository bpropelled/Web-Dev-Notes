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