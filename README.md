# Web-Dev-Notes



## HTACCESS
### Remove the File Extension at the end of the url
    - For HTML
    
```html
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^([^\.]+)$ $1.html [NC,L]
```
    - For Php
```html
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^([^\.]+)$ $1.php [NC,L]
```
That’s it! You can now link pages inside the HTML document without needing to add the extension of the page. For example:
```html
<a href="http://whatever.com/wallpaper" title="wallpaper">wallpaper</a>
```
source is https://alexcican.com/post/how-to-remove-php-html-htm-extensions-with-htaccess/


## HTML
### Setup the base URL for all links on the page
```html
 <base href="http://www.example.ca/" target="_blank"> 
```
### Center an object in bootstrap
```css
.centered{
    float: none;
    margin: 0 auto;
}
```



## Markdown Cheat Sheet
---
title: Markdown Cheatsheet
area: docs
section: content
---

> This cheatsheet is rendered from [a Gist](https://gist.github.com/jonschlinkert/5854601) using the [\{{gist}} helper](https://github.com/assemble/handlebars-helpers#gist).  

If you find any issues or have a suggestion for something we can add, please [create an issue](https://github.com/assemble/assemble-docs/issues),
or just make a comment on [the Gist](https://gist.github.com/jonschlinkert/5854601). Thanks!

### Grab this Cheatsheet

* [Download the cheatsheet](https://gist.github.com/jonschlinkert/5854601/download)
* Copy this Embed it on your own site: `<script src="https://gist.github.com/jonschlinkert/5854601.js"></script>`
* See the [template for this page](https://github.com/assemble/assemble-docs/blob/master/src/templates/pages/docs/Cheatsheet-Markdown.md.hbs).

{{gist "5854601"}}
<br>
<br>


