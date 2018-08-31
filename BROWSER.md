## How to: Disable Same-Origin Policy in Chrome
I’ve been doing some Chrome extension development in the past week and as you may or may not know, chrome extensions are allowed to make cross-domain ajax calls. This is allowed because of the Chrome extension permission model which requires a user installing an extension to agree to that the installed application may access your data on the domain in question.

However, by default, the extension only has this capability when the extension is installed and activated (say by clicking on the app icon on the chrome toolbar).

If you’re developing an extension, this means you have to constantly refresh the extension and click the button in order to test your XHR requests.

It turns out, you can start Chrome with a couple of flags that will allow you to simply browse to your files directly and execute cross-domain XMLHttpRequest calls.

For additional ease, I’ve created a shortcut on my desktop with the flags appended. Your shortcut should look something like this:

C:\Users\YOUR_USER\AppData\Local\Google\Chrome\Application\chrome.exe --allow-file-access-from-files --disable-web-security
The Flags

You’ll notice the two flags appended to the shortcut path.
```html
–allow-file-access-from-files

–disable-web-security
```
Together, both of these flags will allow a developer to test cross-domain ajax requests from a local file.

P.S. I labeled the extension “UNSECURED CHROME” so that I don’t risk always running Chrome with these flags.

//test
