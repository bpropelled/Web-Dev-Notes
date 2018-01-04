[Source](https://www.digitalocean.com/community/tutorials/how-to-access-elements-in-the-dom "Permalink to Methods for Accessing Elements in the DOM File with JavaScript")

# Methods for Accessing Elements in the DOM File with JavaScript

### Introduction

In [Understanding the DOM Tree and Nodes][1], we went over how the DOM is structured as a tree of objects called nodes, and that nodes can be text, comments, or elements. Usually when we access content in the DOM, it will be through an HTML element node.

In order to be proficient at accessing elements in the DOM, it is necessary to have a working knowledge of CSS selectors, syntax and terminology as well as an understanding of HTML elements. In this tutorial, we will go over several ways to access elements in the DOM: by ID, class, tag, and query selectors.

## Overview

Here is a table overview of the five methods we will cover in this tutorial.

| Gets              | Selector Syntax | Method                     |  
| ----------------- | --------------- | -------------------------- |  
| ID                | `#demo`         | `getElementById()`         |  
| Class             | `.demo`         | `getElementsByClassName()` |  
| Tag               | `demo`          | `getElementsByTagName()`   |  
| Selector (single) |                 | `querySelector()`          |  
| Selector (all)    |                 | `querySelectorAll()`       |  

It is important when studying the DOM to type the examples on your own computer to ensure that you are understanding and retaining the information you learn.

You can save this HTML file, `access.html`, to your own project to work through the examples along with this article. If you are unsure how to work with JavaScript and HTML locally, review our [How To Add JavaScript to HTML][2] tutorial.

access.html
    
    
    
    
    
    
      
      
    
      
    
      
    
    
    
    
    
      
Accessing Elements in the DOM

    
      
ID (#demo)

      
Access me by ID

    
      
Class (.demo)

      
Access me by class (1)

      
Access me by class (2)

    
      
Tag (article)

      
Access me by tag (1)

      
Access me by tag (2)

    
      
Query Selector

      
Access me by query

    
      
Query Selector All

      
Access me by query all (1)

      
Access me by query all (2)

    
    
    
    
    

In this HTML file, we have many elements that we will access with different `document` methods. When we render the file in a browser, it will look similar to this:

![Browser rendering of access.html page][3]

We'll be using the different methods that we outlined in the [Overview][4] above to access the available elements in the file.

## Accessing Elements by ID

The easiest way to access a single element in the DOM is by its unique [ID][5]. We can grab an element by ID with the [`getElementById()`][6] method of the `document` object.
    
    
    document.getElementById();
    

In order to be accessed by ID, the HTML element must have an `id` attribute. We have a `div` element with an ID of `demo`.
    
    
    
Access me by ID

    

In the _Console_, let's get the element and assign it to the `demoId` variable.
    
        * const demoId = document.getElementById('demo');
    

Logging `demoId` to the console will return our entire HTML element.
    
    
    Output
    
    
Access me by ID

    

We can be sure we're accessing the correct element by changing the `border` property to `purple`.
    
        * demoId.style.border = '1px solid purple';
    

Once we do so, our live page will look like this:

![Browser rendering of ID element styling][7]

Accessing an element by ID is an effective way to get an element quickly in the DOM. However, it has drawbacks; an ID must always be unique to the page, and therefore you will only ever be able to access a single element at a time with the `getElementById()` method. If you wanted to add a function to many elements throughout the page, your code would quickly become repititious.

## Accessing Elements by Class

The [class][8] attribute is used to access one or more specific elements in the DOM. We can get all the elements with a given class name with the [`getElementsByClassName()`][9] method.
    
    
    document.getElementsByClassName();
    

Now we want to access more than one element, and in our example we have two elements with a `demo` class.
    
    
    
Access me by class (1)

    
Access me by class (2)

    

Let's access our elements in the _Console_ and put them in a variable called `demoClass`.
    
        * const demoClass = document.getElementsByClassName('demo');
    

At this point, you might think you can modify the elements the same way you did with the ID example. However, if we try to run the following code and change the `border` property of the class demo elements to orange, we will get an error.
    
        * demoClass.style.border = '1px solid orange';
    
    
    
    Output
    
    Uncaught TypeError: Cannot set property 'border' of undefined
    

The reason this doesn't work is because instead of just getting one element, we have an array-like object of elements.
    
    
    Output
    
    (2) [div.demo, div.demo]
    

[JavaScript arrays][10] must be accessed with an index number. We can therefore change the first element of this array by using an index of `0`.
    
        * demoClass[0].style.border = '1px solid orange';
    

Generally when accessing elements by class, we want to apply a change to all the elements in the document with that particular class, not just one. We can do this by creating a `for` loop, and looping through every item in the array. 
    
        * for (i = 0; i < demoClass.length; i++) {
    
    *   demoClass[i].style.border = '1px solid orange';
    
    * }
    

When we run this code, our live page will be rendered like this:

![Browser rendering of class element styling][11]

We have now selected every element on the page that has a `demo` class, and changed the `border` property to `orange`.

## Accessing Elements by Tag

A less specific way to access multiple elements on the page would be by its HTML tag name. We access an element by tag with the [`getElementsByTagName()`][12] method.
    
    
    document.getElementsByTagName();
    

For our tag example, we're using `article` elements.
    
    
    
Access me by tag (1)

    
Access me by tag (2)

    

Just like accessing an element by its class, `getElementsByTagName()` will return an array-like object of elements, and we can modify every tag in the document with a `for` loop.
    
        * const demoTag = document.getElementsByTagName('article');
    
    * 
    
    * for (i = 0; i < demoTag.length; i++) {
    
    *   demoTag[i].style.border = '1px solid blue';
    
    * }
    

Upon running the code, the live page will be modified like so:

![Browser rendering of tag element styling][13]

The loop changed the `border` property of all `article` elements to `blue`.

## Query Selectors

If you have any experience with the [jQuery][14] API, you may be familiar with jQuery's method of accessing the DOM with CSS selectors.
    
    
    $('#demo'); // returns the demo ID element in jQuery
    

We can do the same in plain JavaScript with the `querySelector()` and `querySelectorAll()` methods.
    
    
    document.querySelector();
    document.querySelectorAll();
    

To access a single element, we will use the [`querySelector()`][15] method. In our HTML file, we have a `demo-query` element
    
    
    
Access me by query

    

The selector for an `id` attribute is the hash symbol (`#`). We can assign the element with the `demo-query` id to the `demoQuery` variable.
    
        * const demoQuery = document.querySelector('#demo-query');
    

In the case of a selector with multiple elements, such as a class or a tag, `querySelector()` will return the first element that matches the query. We can use the [`querySelectorAll()`][16] method to collect all the elements that match a specific query.

In our example file, we have two elements with the `demo-query-all` class applied to them.
    
    
    
Access me by query all (1)

    
Access me by query all (2)

    

The selector for a `class` attribute is a period or full stop (`.`), so we can access the class with `.demo-query-all`.
    
        * const demoQueryAll = document.querySelectorAll('.demo-query-all');
    

Using the `forEach()` method, we can apply the color `green` to the `border` property of all matching elements.
    
        * demoQueryAll.forEach(query => {
    
    *   query.style.border = '1px solid green';
    
    * });
    

![Browser rendering of querySelector\(\) styling][17]

With `querySelector()`, comma-separated values function as an OR operator. For example, `querySelector('div, article')` will match `div` _or_ `article`, whichever appears first in the document. With `querySelectorAll()`, comma-separated values function as an AND operator, and `querySelectorAll('div, article')` will match all `div` _and_ `article` values in the document.

Using the query selector methods is extremely powerful, as you can access any element or group of elements in the DOM the same way you would in a CSS file. For a complete list of selectors, review [CSS Selectors][18] on the Mozilla Developer Network.

## Complete JavaScript Code

Below is the complete script of the work we did above. You can use it to access all the elements on our example page. Save the file as `access.js` and load it in to the HTML file right before the closing `body` tag.

access.js
    
    
    // Assign all elements
    const demoId = document.getElementById('demo');
    const demoClass = document.getElementsByClassName('demo');
    const demoTag = document.getElementsByTagName('article');
    const demoQuery = document.querySelector('#demo-query');
    const demoQueryAll = document.querySelectorAll('.demo-query-all');
    
    // Change border of ID demo to purple
    demoId.style.border = '1px solid purple';
    
    // Change border of class demo to orange
    for (i = 0; i < demoClass.length; i++) {
      demoClass[i].style.border = '1px solid orange';
    }
    
    // Change border of tag demo to blue
    for (i = 0; i < demoTag.length; i++) {
      demoTag[i].style.border = '1px solid blue';
    }
    
    // Change border of ID demo-query to red
    demoQuery.style.border = '1px solid red';
    
    // Change border of class query-all to green
    demoQueryAll.forEach(query => {
      query.style.border = '1px solid green';
    });
    

Your final HTML file will look like this:

access.html
    
    
    
    
    
    
      
      
    
      
    
      
    
    
    
    
    
      
Accessing Elements in the DOM

    
      
ID (#demo)

      
Access me by ID

    
      
Class (.demo)

      
Access me by class (1)

      
Access me by class (2)

    
      
Tag (article)

      
Access me by tag (1)

      
Access me by tag (2)

    
      
Query Selector

      
Access me by query

    
      
Query Selector All

      
Access me by query all (1)

      
Access me by query all (2)

    
      ">https://www.digitalocean.com/access.js">
    
    
    
    
    

You can continue to work on these template files to make additional changes by accessing HTML elements.

## Conclusion

In this tutorial, we went over 5 ways to access HTML elements in the DOM — by ID, by class, by HTML tag name, and by selector. The method you will use to get an element or group of elements will depend on browser support and how many elements you will be manipulating. You should now feel confident to access any HTML element in a document with JavaScript through the DOM.

[1]: https://www.digitalocean.com/community/tutorials/understanding-the-dom-tree-and-nodes
[2]: https://www.digitalocean.com/community/tutorials/how-to-add-javascript-to-html
[3]: https://assets.digitalocean.com/articles/eng_javascript/dom/html-rendering.png
[4]: https://www.digitalocean.com/community/tutorials/how-to-access-elements-in-the-dom#overview
[5]: https://developer.mozilla.org/en-US/docs/Web/API/Element/id
[6]: https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById
[7]: https://assets.digitalocean.com/articles/eng_javascript/dom/id-element.png
[8]: https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/class
[9]: https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName
[10]: https://www.digitalocean.com/community/tutorials/understanding-arrays-in-javascript
[11]: https://assets.digitalocean.com/articles/eng_javascript/dom/class-element.png
[12]: https://developer.mozilla.org/en-US/docs/Web/API/Element/getElementsByTagName
[13]: https://assets.digitalocean.com/articles/eng_javascript/dom/tag-element.png
[14]: https://jquery.com/
[15]: https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector
[16]: https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll
[17]: https://assets.digitalocean.com/articles/eng_javascript/dom/query-selector.png
[18]: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors