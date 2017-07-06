## Neat JS Error trick
```javascript
try {
	something;
}catch(e){
	window.location.href = "http://stackoverflow.com/search?q=[js] + " + e.message;
}
```