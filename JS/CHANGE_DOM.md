
[Source](https://www.digitalocean.com/community/tutorials/how-to-make-changes-to-the-dom "Permalink to Create, Insert, Replace, and Delete DOM Nodes with JavaScript")

# Create, Insert, Replace, and Delete DOM Nodes with JavaScript

### Introduction

In the previous two installments of the [Understanding the DOM][1] series, we learned [How To Access Elements in the DOM][2] and [How To Traverse the DOM][3]. Using this knowledge, a developer can use classes, tags, ids, and selectors to find any node in the DOM, and use parent, child, and sibling properties to find relative nodes.

The next step to becoming more fully proficient with the DOM is to learn how to add, change, replace, and remove nodes. A to-do list application is one practical example of a JavaScript program in which you would need to be able to create, modify, and remove elements in the DOM.

In this tutorial, we will go over how to create new nodes and insert them into the DOM, replace existing nodes, and remove nodes.

## Creating New Nodes

In a static website, elements are added to the page by directly writing HTML in an `.html` file. In a dynamic web app, elements and text are often added with JavaScript. The `createElement()` and `createTextNode()` methods are used to create new nodes in the DOM.

To begin, let's create an `index.html` file and save it in a new project directory.

index.html
    
    
    
    
    
      
        
      
    
      
        
Document Object Model

      
    
    
    

Right click anywhere on the page and select "Inspect" to open up Developer Tools, then navigate to the [**Console][4]**.

We will use `createElement()` on the `document` object to create a new `p` element.
    
        * const paragraph = document.createElement('p');
    

We've created a new `p` element, which we can test out in the _Console_.
    
    
    Output
    
    

    

The `paragraph` variable outputs an empty `p` element, which is not very useful without any text. In order to add text to the element, we'll set the `textContent` property.
    
        * paragraph.textContent = "I'm a brand new paragraph.";
    
    * console.log(paragraph)
    
    
    
    Output
    
    
I'm a brand new paragraph.


    

A combination of `createElement()` and `textContent` creates a complete element node.

An alternate method of setting the content of the element is with the `innerHTML` property, which allows you to add HTML as well as text to an element.
    
        * paragraph.innerHTML = "I'm a paragraph with bold text.";
    

**Note:**  
While this will work and is a common method of adding content to an element, there is a possible [cross-site scripting (XSS)][5] risk associated with using the `innerHTML` method, as inline JavaScript can be added to an element. Therefore, it is recommended to use `textContent` instead, which will strip out HTML tags.  

It is also possible to create a text node with the `createTextNode()` method.
    
        * const text = document.createTextNode("I'm a new text node.");
    
    * console.log(text)
    
    
    
    Output
    
    "I'm a new text node."
    

With these methods, we've created new elements and text nodes, but they are not visible on the front end of a website until they've been inserted into the document.

## Inserting Nodes into the DOM

In order to see the new text nodes and elements we create on the front end, we will need to insert them into the `document`. The methods `appendChild()` and `insertBefore()` are used to add items to the beginning, middle, or end of a parent element, and `replaceChild()` is used to replace an old node with a new node.

To practice these methods, let's create a to-do list in HTML:

todo.html
    
    
    

      
Buy groceries

      
Feed the cat

      
Do laundry

    

    

When you load your page in the browser, it will look like this:

![DOM Screenshot 1][6]

In order to add a new item to the end of the to-do list, we have to create the element and add text to it first, as we did in the "Creating New Nodes" section above.
    
        * // To-do list ul element
    
    * const todoList = document.querySelector('ul');
    
    * 
    
    * // Create new to-do
    
    * const newTodo = document.createElement('li');
    
    * newTodo.textContent = 'Do homework';
    

Now that we have a complete element for our new to-do, we can add it to the end of the list with `appendChild()`.
    
        * // Add new todo to the end of the list
    
    * todoList.appendChild(newTodo);
    

You can see the new `li` element has been appended to the end of the `ul`.

todo.html
    
    
    

      
Buy groceries

      
Feed the cat

      
Do laundry

      
Do homework

    

    

![DOM Screenshot 2][7]

Maybe we have a higher priority task to do, and we want to add it to the beginning of the list. We'll have to create another element, as `createElement()` only creates one element and cannot be reused.
    
        * // Create new to-do
    
    * const anotherTodo = document.createElement('li');
    
    * anotherTodo.textContent = 'Pay bills';
    

We can add it to the beginning of the list using `insertBefore()`. This method takes two arguments — the first is the new child node to be added, and the second is the sibling node that will immediately follow the new node. In other words, you're inserting the new node before the next sibling node. This will look similar to the following pseudocode:
    
    
    parentNode.insertBefore(newNode, nextSibling);
    

For our to-do list example, we'll add the new `anotherTodo` element before the first element child of the list, which is currently the `Buy groceries` list item.
    
        * // Add new to-do to the beginning of the list
    
    * todoList.insertBefore(anotherTodo, todoList.firstElementChild);
    

todo.html
    
    
    

      
Pay bills

      
Buy groceries

      
Feed the cat

      
Do laundry

      
Do homework

    

    

![DOM Screenshot 3][8]

The new node has successfully been added at the beginning of the list. Now we know how to add a node to a parent element. The next thing we may want to do is replace an existing node with a new node.

We'll modify an existing to-do to demonstrate how to replace a node. The first step of creating a new element remains the same.
    
        * const modifiedTodo = document.createElement('li');
    
    * modifiedTodo.textContent = 'Feed the dog';
    

Like `insertBefore()`, `replaceChild()` takes two arguments — the new node, and the node to be replaced, as shown in the pseudocode below.
    
    
    parentNode.replaceChild(newNode, oldNode);
    

We will replace the third element child of the list with the modified to-do.
    
        * // Replace existing to-do with modified to-do
    
    * todoList.replaceChild(modifiedTodo, todoList.children[2]);
    

todo.html
    
    
    

      
Pay bills

      
Buy groceries

      
Feed the dog

      
Do laundry

      
Do homework

    

    

![DOM Screenshot 4][9]

With a combination of `appendChild()`, `insertBefore()`, and `replaceChild()`, you can insert nodes and elements anywhere in the DOM.

## Removing Nodes from the DOM

Now we know how to create elements, add them to the DOM, and modify existing elements. The final step is to learn to remove existing nodes from the DOM. Child nodes can be removed from a parent with `removeChild()`, and a node itself can be removed with `remove()`.

Using the to-do example above, we'll want to delete items after they've been completed. If you completed your homework, you can remove the `Do homework` item, which happens to be the last child of the list, with `removeChild()`.
    
        * todoList.removeChild(todoList.lastElementChild);
    

todo.html
    
    
    

      
Pay bills

      
Buy groceries

      
Feed the dog

      
Do laundry

    

    

![DOM Screenshot 5][10]

Another method could be to remove the node itself, using the `remove()` method directly on the node.
    
        * // Remove second element child from todoList
    
    * todoList.children[1].remove();
    

todo.html
    
    
    

      
Pay bills

      
Feed the dog

      
Do laundry

    

    

![DOM Screenshot 6][11]

Between `removeChild()` and `remove()`, you can remove any node from the DOM. Another method you may see for removing child elements from the DOM is setting the `innerHTML` property of a parent element to an empty string (`""`). This is not the preferred method because it is less explicit, but you might see it in existing code.

## Conclusion

In this tutorial, we learned how to use JavaScript to create new nodes and elements and insert them into the DOM, and replace and remove existing nodes and elements.

At this point in the [Understanding the DOM series][1] you know how to access any element in the DOM, walk through any node in the DOM, and modify the DOM itself. You can now feel confident in creating basic front-end web apps with JavaScript.

[1]: https://www.digitalocean.com/community/tutorial_series/understanding-the-dom-document-object-model
[2]: https://www.digitalocean.com/community/tutorials/how-to-access-elements-in-the-dom
[3]: https://www.digitalocean.com/community/tutorials/how-to-traverse-the-dom
[4]: https://www.digitalocean.com/community/tutorials/how-to-use-the-javascript-developer-console
[5]: https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML#Security_considerations
[6]: https://assets.digitalocean.com/articles/eng_javascript/dom/to-do-1.png
[7]: https://assets.digitalocean.com/articles/eng_javascript/dom/to-do-2.png
[8]: https://assets.digitalocean.com/articles/eng_javascript/dom/to-do-3.png
[9]: https://assets.digitalocean.com/articles/eng_javascript/dom/to-do-4.png
[10]: https://assets.digitalocean.com/articles/eng_javascript/dom/to-do-5.png
[11]: https://assets.digitalocean.com/articles/eng_javascript/dom/to-do-6.png

  