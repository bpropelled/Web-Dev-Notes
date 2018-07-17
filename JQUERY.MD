# Jquery Notes

## Dynamically Increment an Attribute like a list or form elements.  Use case, for adding dynamically appended fields

- Create a counter variable, this will be the start number for the dynamically added fields
```javascript
var count = 3;

$('#example').on('click', function(e){
    $('.submit').before('<li id="field-' + count + '" >Adding Item # ' + count + '</li>');
    //increment the count var
    count++;
});
```

## Parse Float to n decimals
```javascript
let x = '3.456789';

parseFloat(x).toFixed(2);

// x 3.45
```

## Create an Average Function from an array of numbers
```javascript

let array = [1,4.5,5.5,3.3];

    var avg = function(arr){
        if(typeof(arr) !== 'object' || arr.length === 0 ){ 
            return 0;
        }else{
            let total = 0;
            for(var i = 0; i < arr.length; i++){
                total += arr[i];
            }
            let average = parseFloat(total / arr.length).toFixed(1);
            return average;
        }
    }
    
let x = avg(array);

console.log(x);
```

## Add single and multiple CSS styles to elements
Single CSS
```javascript
$('.test').css('background','#000');
```
Multiple CSS by using an object
```javascript
$('.test')
.css({
   'filter'         : 'blur(0px)',
   '-webkit-filter' : 'blur(0px)',
   '-moz-filter'    : 'blur(0px)',
   '-o-filter'      : 'blur(0px)',
   '-ms-filter'     : 'blur(0px)'
});
```
## Here is a little trick to only have an event fire once
```javascript
$('#element').one{function(e){
    //code here
}}
```

## Check Jquery Version
```js
$.fn.jquery
```