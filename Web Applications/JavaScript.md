Javascript is high-level, dynamically typed, interpreted for client and Server side (Node.js) of the web 

[[HTML5]] $\rightarrow$ structure
[[CSS3]] $\rightarrow$ presentation 
[[JavaScript]] $\rightarrow$ behaviour

### Limitation of javascript:
- **To avoid Pop-up abuse** most browsers restricts javascript to allow the creation of new windows only if triggered by user activity 
- Is **allowed** to close only windows that it opened itself but only after user confirmation 
- a script **cannot** read or modify the content of documents in other tabs and windows
- **cannot**  register event listeners on pages on different tabs or windows 
### Inserting scripts in a page 

``` javascript
//Embedded script:
<script>
... JavaScript code goes here
</script>
//External scripts:
<script src="my_script.js"></script>
```
- All js code in the page share the same set of global functions and variables
- All the code is loaded and executed int the same order as they appear in the document 
- Usually scripts are placed at the `head` or at the end of `body` tags, the main difference is when the body of the page is loaded and the tradeoff on the performace on page loading 

To note that when multiple web pages share the same JavaScript code,using the src attribute allows you to maintain only a single copy of that code.
**If a file of JavaScript code is shared by more than one page, it only needs to be downloaded once**. 
# Core javascript 
Javascript is a **case-sensitive** language(differently from HTML).
## Statements 
Statements are separated by `;` but can understand a new statement as a new line 
None the less can create situation like this :
``` javascript 
var y = x + f
(a+b).toString()

// wich is actually equal to  
var y = x + f(a+b).toString()

```
### Comments 
javascript uses `//comment` and `/*comment*/`  as comments


## Javascript data types 
Any javascript value that is not:
- a number 
- a string 
- boolean(aka. all the primitives) 
- null or undefined 
is an object 

#### Special Values
- **null** indicates the absence of a value 
- **undefined** indicates that the value has not been inizialized 

javascript interpreter performs an automatic garbage collection for memory management 
## Variable Declatration 
``` javascript  
var y; 
var message = "hello";
```

### Numbers 
JavaScript does not make a distinction between integer values and floating-point values
``` javascript  
var a = 5;
var pi = 3.14;
```
and support all normal + ,- , * , / , % and more complex one with the module Math 

## Strings 
JavaScript’s strings (and its arrays) use zero-based indexing.
``` javascript  
var a = 'Hello';
var b = "bye";
```
and uses / for escape characters and + sign for concatenation 
## Booleans 
``` javascript  
var a = 'Hello';
var b = "bye";
```
- Booleans sopport a method toString() that convert the values into "true"and "false"
- Boolean operators: AND (&&), OR (||), NOT (!)


## Javascript Objects 
Javascript Object are essentially **associative arrays**
``` javascript  
object.property
object["property"]
```
Differently from strong typed languages any program can add remove or alter properties of the objects 
#### Object definitions 
``` javascript  
// By assignation 
var o = {
data_prop1: value1,
data_prop2: value2,
method_1() { /* function body here */ },
method_2(value) { /* function body here */ }
};
// By costructor 
function Person(first, last, age, eye) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eye;
 this.plusOne = function() {this.age = this.age + 1};
 this.name = function() {
 return this.firstName + " " + this.lastName
 };
}
// declaration 
var myFather = new Person("John", "Doe", 50, "blue");
document.getElementById("demo").innerHTML = "My father is " + myFather.name(); 
```
#### `this` keyword
``` javascript  
var person = {
 firstName: "John",
 lastName : "Doe",
 id       : 5566,
 fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};
```
the this keyword refere always to the owner of the function aka the object from wich it comes 

#### delete keyword 
``` javascript  
delete book.audience;
```
A delete expression remove the property of the object and evaluates to true if the delete succeeded or if the delete had no effect.

## Arrays 
Javascript uses dynamic arrays 
``` javascript  
var empty = [];
var primes = [2, 3, 5, 7, 11];
var misc = [ 1.1, true, "a", ];
var nest = [[1,{x:1, y:2}], [2, {x:3, y:4}]];
var v_0 = new Array();
var v_1 = new Array(10);
var v_2 = new Array(5, 4, 3, 2, 1);
// access the first element
a.[0]
// return the length of the array 
a.length
```

###### Array methods
- Array.join() method converts all the elements of an array to strings and concatenates them.
- Array.reverse() method reverses the order of the elements of an array and returns the reversed array 
- Array.sort() sorts the elements of an array in place andreturns the sorted array.
- Array.concat() method creates and returns a new arraythat contains the elements of the original array on which concat()
## forEach()
method iterates through an array, invoking a function you specify for each element.

``` javascript  
var data = [1,2,3,4,5];
var sum = 0;
// in order the function specify 
// value , index, object array 
data.forEach(function(value) { sum += value; });
data.forEach(function(v, i, a) { a[i] = v + 1; });
```

# Function definition 
``` javascript  
function addNumbers(a,b) {
	return a + b;
}
```

# Browser manipulation 

## Window Object 
Allow to manipulate parts of the browser.

### Dialog boxes
- **alert()** displays a message to the user and waits for the user to dismiss the dialog.
- **confirm()** displays a message, waits for the user to click an OK or Cancel button and returns a boolean value.
- **prompt()** displays a message, waits for the user to enter a string, and returns that string.

``` javascript 
do {
	var name = prompt("What is your name?");
	var correct = confirm("You entered '" + name +
	"'.\n" + "Click Okay to proceed or Cancel to reenter.”);
} while (!correct)
	alert("Hello, " + name);
```
### Timers 
- **setTimeout()**: method schedules a function to run after a specified number of milliseconds elapses.
- **setInterval()**: is like setTimeout() except that the specified function is invoked repeatedly at intervals of the specified number of milliseconds
### Browser and Screen Information 
#### Navigator 
The navigator property of a Window object refers to a Navigator object that contains browser vendor and version number information. 
The Navigator object has four properties:
- **appName**: full name of the web browser;
- **appVersion**: browser vendor and version information;
- **userAgent**: string that the browser sends in its User-Agent HTTP header;
- **platform**: the operating system.
#### Screen 
The screen property of a Window object refers to a Screen object that provides information about the **size** of the user’s display and the number of **colors**  available on it.

# Document object model(DOM)

- window object has a document property that refers to a document object (wich represents the content of the windows). Fundamental Api for representing and manipulationg the content of HTML
## DOM Structure 
Dom has a tree like rappresentation with the content of the tags on the leafs
![[Pasted image 20240529205653.png]]
 
## Selecting Document Elements
#### By id 
Usually the Id is univoque.
``` javascript 
var section1 = document.getElementById("section1");
```
#### By name 
Name attribute is inteded to be assigned to a form (or multiple elements).
``` javascript 
var radiobuttons = document.getElementsByName("favorite_color"); 
```
#### By tag name 
Select all the similar html tags
``` javascript 
var spans = document.getElementsByTagName("span");
```
#### By tag name 
Select all the element with the same class  or selected by a certain class.
``` javascript 
var sidebarPara = document.querySelectorAll(".sidebar p”);
var textInput = document.querySelectorAll("input[type='text']");
```

## Node objects
**Each element of the Dom tree is a node and has certain properties The Document object, its Element objects, and the Text objects:**
- parentNode childNodes firstChild, lastChild nextSibling, previousSibling 
- nodeType: the kind of node this is: 
		Document nodes have the value 9
		Element nodes have the value 1
		Text nodes have the value 3
		Comments nodes are 8 
		Document-Fragment nodes are 11
- nodeValue: the textual content of a Text or Comment node 
- nodeName: the tag name of an Element(uppercase)

**if we need to access only to the elements of a document instead of the text within them we can search around with:**
- children: returns only Element objects.
- firstElementChild, lastElementChild 
- nextElementSibling, previousElementSibling
- childElementCount: the number of element children
### Attributes as Element Properties
The HTMLElement objects define read/write properties that mirror the
HTML attributes of the elements. 
``` javascript 
// selecting the element
var image = document.getElementById("myimage");
// to ways to refer to the attribute 
var imgurl = image.getAttribute("src");
var imgurl = image.src;
```
also we can use the methods :
- setAttribute() methods that you can use to set HTML attributes.
- hasAttribute() checks for the presence of a named attribute.
- removeAttribute() removes an attribute entirely.


## Manipulating Doms Nodes
The Document type defines methods for creating Element and Text objects, and the Node type defines methods for inserting, deleting, and replacing nodes in the tree.

#### Create Element 
You can create new Element nodes with the createElement()
``` javascript 
var newDiv = document.createElement("div"); 
var ourText = document.createTextNode("Put text here.");
```


#### append Child 
appendChild() is invoked on the Element node that you want to insert into, and it inserts the specified node so that it becomes the last child of that node.
``` javascript 
var ourDiv = document.getElementById("our-div");
var newParagraph = document.createElement("p");
var newText = document.createTextNode("Hello, world!");
newParagraph.appendChild(newText);
ourDiv.appendChild(newParagraph); 
```
#### insert Child 
insertBefore() is like appendChild(), but it takes two arguments: the first argument is the node to be inserted, the second argument is the node before which that node is to be inserted

``` javascript 
var ourDiv = document.getElementById("our-div");
var para = document.getElementById("our-paragraph");
var newHeading = document.createElement("h1");
var headingText = document.createTextNode("A new heading");
newHeading.appendChild(headingText);
// the element para is inserted before the note to be inserted
ourDiv.insertBefore(newHeading, para);
```

#### Remove childs

``` javascript 
var parentDiv = document.getElementById("parent");
var remove_el = document.getElementById("removable_element");
// removes the element
parentDiv.removeChild(remove_el);

var parentDiv = document.getElementById("parent");
var swap_el = document.getElementById("swap-me");
var newImg = document.createElement("img");
newImg.setAttribute("src", "path/to/image.jpg");
// replace with an image 
ourDiv.replaceChild(newImg, swap_el);
```


# Handling events 
### Javascript Life cycle 
1. web browser creates a document object and start the parsing of the web page 
2. `<script>` elements are added to the document and  then executes the script (synchronously)
3. The document is completely parsed but need to load additional content. document.readyState property changes to **complete** 
4. frm now the events the event handlers are invoked asynchronously in response to user input events,network events,timer expirations and so on 

### Events 
Events are occurrences that a web browser will notify your JavaScript program about
###### Event Type 
The event type is a string that specifies what kind of event occurred, examples are: mouseup, keydown, click...
###### Event Target 
The event target is the object on which the event occurred or with which the event is associated.
#### Most used events 
- the mouse (mouseover,mousedown,click,dbclick,mouseover,mouseout,mousewheel) 
- the keyboard (keyboard focus,keyup/keydown,key press)
- HTML FORMS(onclick,onchange) 
![[Pasted image 20240530182737.png]]
	Form elements also fire a **focus** event when they receive keyboard focus and a **blur** event when they lose it.
	Each Form element has an onsubmit event handler to
	detect form submission and an onreset event handler to detect form resets.

- the Windows object : 
![[Pasted image 20240530185215.png]]


### Register Event Handlers

#### 1. Classic Way:
- Setting the event handler property:

```javascript
var elt = document.getElementById("address");
elt.onsubmit = function() { 
    return validate(this); 
};
```

- Setting the attribute in HTML:

```html
<form id="address" onsubmit="return validate(this);">
    <!-- form elements -->
</form>
```

#### 2. Using `addEventListener`:
- Passing the handler to a method of the object or element:

```javascript
var b = document.getElementById("mybutton");

// Using onclick property
b.onclick = function() { 
    alert("Thanks for clicking me!"); 
};

// Using addEventListener
b.addEventListener("click", function() { 
    alert("Thanks again!"); 
});
```

- Using `attachEvent` (Only for Internet Explorer):

```javascript
// For older versions of IE
var b = document.getElementById("mybutton");
b.attachEvent("onclick", function() { 
    alert("Thanks for clicking me!"); 
});
```

### Best Choice: `addEventListener`

Using `addEventListener` is generally the best choice because:
- **Multiple Handlers**: It allows adding more than a single handler for an event.
- **Control**: It gives you finer-grained control over the phase when the listener is activated (capturing vs. bubbling).
- **Versatility**: It works on any DOM element, not just HTML elements.

### Removing Event Listeners

To remove an event listener, you can use the `removeEventListener` method:

```javascript
document.removeEventListener("mousemove", handleMouseMove);
document.removeEventListener("mouseup", handleMouseUp);
```
