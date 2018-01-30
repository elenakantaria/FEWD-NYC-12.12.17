# Lesson 12 - Native DOM Manipulation

### Learning Objectives
- Explain the DOM: its value and its structure
- Access DOM Elements using relative selection
- Access DOM Elements using query selectors
- Create, Read (access), Update (content and attributes), and Destroy DOM elements

## Introducing the DOM

JavaScript is the lingua franca of the web. Since it's advent in 1995 as a neat but hastily delivered browser feature from Netscape it has revolutionized the web and by extension the world.
Foundational to the success (existence) of this revolution is a clunky and confusing API called the DOM, the Document Object Model.
The DOM's conception was organic and as its importance grew was standardized.

The DOM is best understood through use so we will waste little time before diving in but if you are interested in a more complete / formalized description, check out [CSS Tricks: What is the DOM?](https://css-tricks.com/dom/) and [MDN Intro to the DOM]( https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction )

### Representing the Document

The document is the content of our webpage which is encoded into our HTML. The HTML we write is one representation of this.

> What structure does HTML take? (hint: think of parent / child relationships between elements)
> [ hint 2 ](http://hakim.se/experiments/css/domtree/)

An HTML document (like so many other things in programming) is a tree. We will think of it as a tree of elements:

![Element Tree](http://www.tuxradar.com/files/LXF118.tut_grease.diagram.png)

It is important to note though, that there are separate element and text nodes:

![HTML as a tree](http://www.cs.toronto.edu/~shiva/cscb07/img/dom/treeStructure.png)

![HTML more tree like](http://www.cs.toronto.edu/~shiva/cscb07/img/dom/treeStructureAlternate.png)

We will generally interact with elements and consider the text something belonging to the element but remember to keep in mind actual implementation

## Accessing Element Objects
When interacting with the DOM, we will primarily be interfacing with element object

The `document` object is exposed on the global object, `window`. This is the top level or root element object

If you haven't already, clone this repo. Open `starter_code/lecture/index.html` in your browser and open the developer console.

The document has several entry points to the page's content including `.head` and `.body`

### Relative Selection
There are several properties that every element has which reference the elements proximate to it:

- `.children`
- `.childNodes`
- `.firstChild`
- `.lastChild`
- `.previousSibling`
- `.nextSibling`
- `.parentElement`

![Node Relations]( https://www.w3schools.com/xml/navigate.gif )

#### Independent Practice 1 - Relative Selection

Spend a few minutes navigating our simple list using these properties and methods in the console.
Evaluate frequently to keep you bearings and remember to use the up/down arrows to navigate your history.

Use google throughout and talk with your neighbors about confusing parts of documentation.
Docs are written precisely using sometimes confusing syntax; this is necessary and a good thing but takes some getting used to

### Query Selection

> Why is relative traversal from the top level an unmaintainable approach to element selection?

Fortunately, we have some much easier method of accessing elements.

#### By Id
```javascript
document.getElementById('id')
```

#### By Tag
```javascript
document.getElementsByTagName('tagName')
```

#### By Class
```javascript
document.getElementsByClassName('className')
```

#### By Selector <-- USE THIS ONE
```javascript
document.querySelector('selector')
```
and
```javascript
document.querySelectorAll('selector')
```
use CSS selectors to target elements.

> What's the difference between `querySelector` and `querySelectorAll`? Why would we use any of the other selectors?

#### Independent Practice 2 - Query Selection
Play with that same list, now using query selectors.

As always, discuss what you find with your neighbors -- explaining these ideas in your own words is as valuable as using them

## Lab 1 - JS DOM Quotes

Go to `starter_code/dom_quotes`

## Manipulating Element Objects

#### Attributes

```javascript
element.getAttribute(attr)
element.setAttribute(attr, val)
```

#### Classes

```javascript
element.classList
```

#### Style

```javascript
element.style
```

#### Input Value

```javascript
inputElement.value
inputElement.value = someValue
```

#### Content

```javascript
element.innerHTML
element.innerHTML = '<p> I\'m new </p>'
```

### Independent Practice 3 - Logo Hijack

1. Open up https://www.microsoft.com/en-us/ in Chrome or Firefox, and open up the console.
1. find an image url for the apple logo
1. Store the url to the apple logo in a variable.
1. Find the Microsoft logo using JS and store it in a variable.
1. Modify the source of the logo IMG so that it's an apple logo instead.
1. Find the Microsoft search input and store it in a variable.
1. Modify the placeholder of the input so that it says "Search Apple" instead.

## Creating Elements

```javascript
var newElement = document.createElement(tagName)
```

NOTE: this just creates elements but they are not yet on the document!

### Adding Elements

```javascript
element.appendChild(newElement)
```

> Look at the docs for the JS method `.innerHTML`. How is it different from the above method? Why might we not really like this?

### Removing Elements

```javascript
element.removeChild(childElement)
```

## Reference
- [MDN DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction#Interfaces_and_Objects)
- [Eloquent JS: The Document Object Model](http://eloquentjavascript.net/13_dom.html)
