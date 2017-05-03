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
