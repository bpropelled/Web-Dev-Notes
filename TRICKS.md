## Neat JS Error trick
```javascript
try {
	something;
}catch(e){
	window.location.href = "http://stackoverflow.com/search?q=[js] + " + e.message;
}
```

## Change LocalHost to a fancy domain
This is a simple trick that is nice to use on a dev environment

Forexample, when using Xampp or Laravel's Artisan web server, you typically have to go to localhost:8000.  Boring.  So here is a trick to add a fancy url to your local dev on Windows

1. Go to C:\{USER}\windows\system32\drivers\etc\hosts
2. Add a line that goes
```cmd
127.0.0.1 fu.ck
```
3. Fire up server
4. Now go to fu.ck, or for a typical laravel install use fu.ck:8000

**Cool Eh!**