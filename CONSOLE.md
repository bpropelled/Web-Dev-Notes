## Console Notes

### Make the console output look nice
- to make the console nice looking with CSS, do the following
```js
console.log('%c a colorful message', 'background: green; color: white; display: block;');
```

### Make an empty file from cmd
```cmd
echo > test.txt
```

this will mkae a file with one line "Echo is on"
to make this an empty file just do this
```cmd
echo.> test.txt
```

or add items into it bby putting them before the ">"

```cmd
echo hey this is cool > test.txt
```

## Stylish Console Logs
You can style the text you display via console.log() with CSS. Just stick “%c” at the beginning of your string, then add a second string parameter for the CSS. Like so:
```cmd
console.log('%cHey, look at me, being all fancy and stuff!', 'font-size: 26px; font-weight: bold; color: purple;')
```
