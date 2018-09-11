# Vue Notes

## Getting Started
The first thing you need to do is install Vue for the site.  This step is pretty simple, but there are more advanced ways of adding Vue to a project including using the Vue Cli tool.  We will start with the basics first.  Let's say we had this html structure:
```html

<div id="app">
    <h1>Hello Name</h1>
</div>
<script src="main.js"></script>
```
**In main.js**

```javascript
let name = "Frank";
```
We are going to inject the Vue script just above the </body> tag in the html file and it can be done like so using the Vue CDN url.
```html
    <script src="https://unpkg.com/vue"></script>
    <script src="main.js"></script>
</body>
```