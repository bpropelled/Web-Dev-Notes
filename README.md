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