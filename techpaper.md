# DOM - Technical Paper  
-Subhadeep Bandyopadhyay
<br />

## Table of Contents

<!--ts-->
* [What is DOM?](#what-is-dom)
* [How does it help?](#how-does-it-help)
* [How to access it?](#how-to-access-it)
* [What are JS Helper methods?](#what-are-JS-Helper-methods)
* [References](#references)
<!--te-->

## What is DOM?
DOM stands for Document Object Model. It is a programming API for HTML and XML documents. It represents the way documents might be accessed or manipulated. Now, the object model resembles the structure of the documents it models. For example: 

```javascript
<TABLE>
      <ROWS> 
      <TR> 
      <TD>Shady Grove</TD>
      <TD>Aeolian</TD> 
      </TR> 
      <TR>
      <TD>Over the River, Charlie</TD>
      <TD>Dorian</TD> 
      </TR> 
      </ROWS>
      </TABLE>
```

The Document Object Model representation looks like this:

![Dom representation](https://www.w3.org/TR/WD-DOM/table.gif)

As you can see from the above representation, the structure is much like a tree; to be more precise, it is like a "forest", i.e., it can contain more than one tree. DOM specifies the logical model for the programming interface, and this can be implemented according to convenience. There are no particular implementations, so terminologies like "tree" or "forest" are avoided; instead, we use the term _structure model_ to describe the tree-like representation. Another important property of DOM is that the same structure model will be created, with precisely the same objects and relationships, if any two DOM interpretations are used to create a representation of the same document. 

"Document Object Model" is called by its name because it is an "object model" and is used in the Object-Oriented design. Therefore, the nodes within the above diagram don't represent a data structure; instead, they represent objects, which have functions and identities. The DOM identifies:
- to manipulate a document, the interfaces and objects are used
- the details of these interfaces and objects - including both behaviour and attributes
- the relationships between these interfaces and objects

## How does it help? 

Maintaining a standard programming interface for HTML and XML documents, which is language-independent is one of the main reasons why the DOM is developed. Setting and maintaining this standard enables programmers to create or navigate these types of documents and modify their elements predictably, using any type of language or development environment.

Having said that, JavaScript language is arguably one of the most popular ways of working with HTML documents using the DOM. 

The uses of the DOM are many and varied, but if we were to make a list of the key abilities, these would include:
* to locate elements in the document by their ID, class, tag name and other characteristics
* to add, remove, or modify the HTML elements
* to modify any attributes of an HTML element such as their class
* to add animation to a document by gradually changing an element's position on the page over time in JavaScript

## How to access it? 

Beginning to use DOM isn't anything special. Different browsers implement DOM differently, and these implementations show varying degrees of consistency to the actual DOM standard, but every browser uses some DOM to make its web pages accessible via JavaScript.

When a script is created, you can begin using the API for the document to manipulate itself or to get at the children of that document, which are the various elements in the web page. DOM programming may be something as simple as using the alert() function from the window object to display an alert message like in the first example, or it may use more sophisticated DOM methods to create new material, as in the second example below.

The following JavaScript will display an alert when the document is loaded (and when the whole DOM is available for use):
```javascript
<body onload="window.alert('Hello World!');">
```
Another example. This function creates a new H1 element, adds text to that element, and then adds the H1 to the tree for this document:
```javascript
<html>
  <head>
    <script>
       // run this function when the document is loaded
       window.onload = function() {

         // create a couple of elements in an otherwise empty HTML page
         const heading = document.createElement("h1");
         const heading_text = document.createTextNode("Big Head!");
         heading.appendChild(heading_text);
         document.body.appendChild(heading);
      }
    </script>
  </head>
  <body>
  </body>
</html>
```

## What are JS Helper methods?


Helper methods are JavaScript functions that can be called from templates. Helper methods make complicated tasks a bit easier and keep the code DRY (an acronym for Don’t Repeat Yourself).

Some of the important Helper Methods are:

**1. fill() Method**: This method fills the array with a static value. It overrides all array values starting from the first element and up to the last element.

Input:
```
value
```
Output:
```
Modified array
```
```javascript
const employees = [
    { name: "Smith",   age: 25, role: "Developer" },
    { name: "Jimmy",   age: 32, role: "Manager"   },
    { name: "Rudolph", age: 29, role: "Architect" },
    { name: "Paul",    age: 25, role: "Developer" },
    { name: "Steve",   age: 38, role: "Director"  },
    { name: "Karen",   age: 21, role: "Developer" },
];
         
const newEmployees = employees.fill(
    { name: "Steven", age: 25, role: "Developer" });
console.log(employees);
 
console.log(newEmployees === employees);    // true
```
Output:
```
[
 { name: 'Steven', age: 25, role: 'Developer' },
 { name: 'Steven', age: 25, role: 'Developer' },
 { name: 'Steven', age: 25, role: 'Developer' },
 { name: 'Steven', age: 25, role: 'Developer' },
 { name: 'Steven', age: 25, role: 'Developer' },
 { name: 'Steven', age: 25, role: 'Developer' }
]

true
```
**2. find() Method**: This method returns the first element that passes the test with the provided function.

Input:
```
Predicate function 
```
Output:
```
Element that passes the test else undefined 
```
```javascript
const employees = [
    { name: "Smith",   age: 25, role: "Developer" },
    { name: "Jimmy",   age: 32, role: "Manager"   },
    { name: "Rudolph", age: 29, role: "Architect" },
    { name: "Paul",    age: 25, role: "Developer" },
    { name: "Steve",   age: 38, role: "Director"  },
    { name: "Karen",   age: 21, role: "Developer" },
];

function searchFirstDevEmployee(employee) {
  return employee.role === "Developer";
}
const firstEmployeeDeveloper = employees.find(searchFirstDevEmployee);
console.log(firstEmployeeDeveloper);   
```
Output:
```
{ name: 'Smith', age: 25, role: 'Developer' }
```

**3.  flat() Method**: This method is used to concatenate the array with the sub-array elements recursively.

Input: 
```
depth(default value is 1)
```
Output:
```
New array
```
```javascript
const arr1 = [1, [2, 3, 4], 5];
const flattened1 = arr1.flat();
console.log(flattened1); // [ 1, 2, 3, 4, 5 ]

const arr2 = [1, 2, [3, 4, [5, 6]]];

const flattened2 = arr2.flat();
console.log(flattened2); // [1, 2, 3, 4, [5, 6]]
```
Output:
```
[1, 2, 3, 4, 5]
[1, 2, 3, 4, [5, 6]]
```
**4.  includes() Method**: This method is used to test whether an element is present in an array or not. It checks for a value in primitive and reference in case of an object.

Input:  
```
value
```
Output:
```
Boolean value weather array includes value or not
```
```javascript
const numbers = [1, 6, 8, 11, 5, 9, 4];
console.log( numbers.includes(6) ); 
console.log( numbers.includes(3) );
```
Output:
```
true
false
```
**5. join() Method**: This method concatenates the array values into a string separated by comma(if no separator is provided) or with separator provided.
Input:  
```
separator
```
Output:
```
New string          
```
```javascript
const names = ["Smith", "Jimmy", "Rudolph", "Paul", "Steve", "Karen"];
console.log( names.join() );
 
console.log( names.join(" -> ") );
```
Output:
```
'Smith, Jimmy, Rudolph, Paul, Steve, Karen'
 'Smith -> Jimmy -> Rudolph -> Paul -> Steve -> Karen'
```

## References
- https://www.w3.org/TR/WD-DOM/introduction.html
- https://www.w3schools.com/js/js_htmldom.asp
- https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction
- https://www.quora.com/Why-is-a-DOM-useful
- https://guides.emberjs.com/release/components/helper-functions/
- https://www.geeksforgeeks.org/array-helper-methods-in-es6/
- https://vanillajstoolkit.com/helpers/
