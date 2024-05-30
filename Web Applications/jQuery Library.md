# Context
jQuery is  a small and fast javascript library that **offers**:
- **consistency across browsers without fallback on code**
- **select elements in a simpler way and more powerful way**
- **manipulate html/dom elements**
- **attach event listeners without fallback code**
- **html event mothods**
- **easier [[AJAX]]**
- **utilities**

# Usage
The library is defined as a variable jQuery() shorted as the character **$**

``` javascript
var divs = jQuery.("div");

var divs = $("div");
```

# jQuery Objects 
### As selectors 
Array like structures of elements of the page
``` javascript
var divs = $("div");

$("p.details").css("background-color", "yellow").show("fast")

```
this return a jQuery object with the property of :
- length 
- selector : what we selected ("div:")
- context: passed as the second argoument  or the document object 
- jquery property: flag that check if is a javascript array or a jQuery object 

example;
``` javascript
$("body").length
$("body")[0]
``` 

to convert to array exist **toArray()** method 

##### As instatiator 
if the selector argoument of  **$()** looks like HTML code jQuery will instantiate sad object.

``` javascript
var img = $("<img/>",
{ src: url,
 css: {borderWidth:5},
 click: handleClick
});
``` 
note that if it is not valid html code the selector string will be treated as  a [[jQuery Library#As selectors|selector]]

#### Iteration 
to iterate over this structures exist the method **each()** similar to **forEach()** of the javascript arrays 


# Getters and Setters methods
jQuery uses a single method as both setter and getter **.attr()**

``` javascript
// as a getter
$("a").attr("href");
// as a setter
$("a").attr("href", "allMyHrefsAreTheSameNow.html");
``` 

#### Getting and Setting CSS Attributes
``` javascript
$("h1").css("fontSize", "100px");
$("h1").css({
 fontSize: "100px",
 color: "red"
});
``` 
and also defines to manage **classesses assignments**:
``` javascript
var h1 = $("h1");
h1.addClass("big");
h1.removeClass("big");
h1.toggleClass("big");
if (h1.hasClass("big")) {
}
``` 

#### Getting and Setting Inner Text
``` javascript
// as a getter
var singleValues = $("#single").val();
var multipleValues = $("#multiple").val();

// as a setter
$("input[type=text].tags").val(function(index, value) {
 return value.trim();
});
```

#### Getting and Setting Generic Html code 
The **text() and html()** methods query and set the plain-text or HTML content of an element or elements:

#### with no arguments:
- **text()** return the playtext of all text nodes
- If you invoke the **html()** method with no arguments, it returns the HTML content of just the first matched element.
#### passing a string:
passing a string to these methods will result in the substitution of the html or text in the tags


# Manipulating Dom structure
The insertion is made into or before or after or in place of (depending on the method) each of the selected elements and follow 2 different convetions with different methods for each convention 


``` javascript
$(target).method(content)
$(content).method(target)
```

**Examples**:

``` javascript
$("#log").append("<br/>"+message);
$("p").prepend("<b>Hello </b>");;
$("h1").before("<hr/>");
$("h1").after("<hr/>");
$("hr").replaceWith("<br/>");

$("<br/>+message").appendTo("#log");
$(document.createTextNode("<b>Hello </b>")).prependTo("p");
$("<hr/>").insertBefore("h1");
$("<hr/>").insertAfter("h1");
$("<br/>").replaceAll("hr");
```

### Cloning part of the html code 

``` javascript
// clone the class hello 
$(".hello").clone().appendTo(".goodbye");
``` 

### Wrapping content 
``` javascript
//wraps each of the selected items
$("h1").wrap(document.createElement("i"));
//wraps the content of each selected items 
$(".inner").wrapInner("<div class='new'></div>");
//wraps the selected items as a group 
$(".inner").wrapAll("<div class=‘new'></div>");
``` 
### Other content related methods:
- **empty()** removes all children of each of the selected elements.
- **remove()** removes the selected elements (together with their event handlers
and data) from the document. 
- detach() method works like remove() but does not remove event handlers
and data. 
- **unwrap()** method performs element removal in a way that is the opposite of
the wrap() or wrapAll() method.


# Handling events with jquery 

``` javascript
$("p").click(function() { $(this).css("background-color", "gray"); });
``` 

### Event Handler Registration Methods:
blur() change() click() dblclick() focus() focusin() focusout() error() keydown() keypress() keyup() load() mousedown() mouseenter() mouseleave() mousemove() mouseout() mouseover() mouseup() resize() scroll() select() submit() unload()


to register multiple event we use **bind()**
``` javascript
$("a").hover(f);
$("a").bind("mouseenter mouseleave", f);
``` 

to remove all the listeners (**related to jQuery**)or only the select ones:
``` javascript
//remove all 
$("*").unbind();
//remove the selected
$("a").unbind("mouseover mouseout"); 
``` 

## Ajax and jQuery

Since Ajax implementation may vary Jquery provides several methods for ajax functionality across multiple browsers
``` javascript
jQuery.ajax()

//not much used in favor of more specific methods
$.ajax({
 method: "POST",
 url: "some.jsp",
 data: { name: "John", location: "Boston" }
})
 .done(function( msg ) {
 alert( "Data Saved: " + msg );
 });
``` 
### .get()
``` javascript
$.get(URL, callback);
// specify what to do on completion 
$.get("test.jsp", { name: "John", time: "2pm" } )
 .done(function(data, status) {
 alert("Data Loaded: " + data “\nStatus: ” + status);
 });
``` 
### .post(URL,data,callback)
``` javascript
$.post(URL, data, callback)
// specify what to do on completion 
$.post("test.jsp", { name: "John", time: "2pm" })
 .done(function(data) {
 alert("Data Loaded:" + data);
 });
``` 

### .getScript()
``` javascript
$.getScript("ajax/test.js", function( data, textStatus, jqxhr) {
 console.log(data); // Data returned
 console.log(textStatus); // Success
 console.log(jqxhr.status); // 200
 console.log("Load was performed.");
});
``` 
### .getJSON()
load JSON-encoded data from the server using a GET HTTP request.

``` javascript
$.getJSON("ajax/test.json", function(data) {
 var items = [];
 $.each(data, function(key, val) {
 items.push( "<li id='" + key + "'>" + val + "</li>" );
 });

 $("<ul/>", {
 "class": "my-new-list",
 html: items.join( "" )
 }).appendTo( "body" );
});
``` 

### .load()
load() is a simple but powerful AJAX method.Loads data and put it directly inside a selected element.

``` javascript
$(selector).load(URL,data,callback); 
//load / replace all the content at the id result
$("#result").load("ajax/test.html");
$("#address").load("address.jsp", { zipcode:"02134", country:"IT" }); 
``` 

# Canvas
Html5 specification incluedes canvas eleemntes that allow to draw graphics using javascript
For each canvas element you can use a "context" (similar to a page in a drawing pad), into which you can issue JavaScript commands to draw anything you want 

``` HTML 
<canvas id="tutorial" width="150" height="150"></canvas>
``` 
The element can be sized arbitrarily by CSS, but during rendering the image is scaled to fit its layout size: if the CSS sizing doesn't respect the ratio of the initial canvas, it will appear distorted


example of use 
``` HTML 

 <script type="text/javascript">
 function draw() {
	 var canvas = document.getElementById('tutorial');
	 if (canvas.getContext) {
		 var ctx = canvas.getContext('2d');
	 }
 }
 </script>
 <style type="text/css">
 canvas { border: 1px solid black; }
 </style>
 </head>
 <body onload="draw();">
 <canvas id="tutorial" width="150" height="150"></canvas>
 </body>
``` 


## Draw on the canvas 
#### Coordinate sistem 
![[Pasted image 20240527201503.png]]
## Drawing Rectangles
canvas only supports one primitive shape: rectangles. 
**All other shapes mustbe created by combining one or more paths, lists of points connected by lines** 

- fillRect(x, y, width, height): draws a filled rectangle.
- strokeRect(x, y, width, height): draws a rectangular outline.
- clearRect(x, y, width, height): clears the specified rectangular area, making it  fully transparent. 


``` javascript  
ctx.fillRect(25, 25, 100, 100);
ctx.clearRect(45, 45, 60, 60);
ctx.strokeRect(50, 50, 50, 50);
``` 

![[Pasted image 20240527202048.png]]


### Drawing 

### Drawing straight lines 
``` javascript  
//start the drawing
ctx.beginPath();
//move the brush in position without drawing 
ctx.moveTo(75, 50);
// draw a line  
ctx.lineTo(100, 75);
ctx.lineTo(100, 25);
// actually draw the shape as lines
ctx.stroke();
// fill the designed figure
ctx.fill();
``` 


### Drawing arcs 


 arc(x, y, radius, startAngle, endAngle,anticlockwise): 
 draw a circle of center (x,y) of radius and start and end angle in a clock or anticlocwise fashion

arcTo(x1, y1, x2, y2, radius):
draws an arc with the given control points and radius, connected to the previous point by a straight line.


``` javascript  
ctx.beginPath();
ctx.arc(75, 75, 50, 0, Math.PI * 2, true);
ctx.moveTo(110, 75);
ctx.arc(75, 75, 35, 0, Math.PI, false);
ctx.moveTo(65, 65);
ctx.arc(60, 65, 5, 0, Math.PI * 2, true);
ctx.moveTo(95, 65);
ctx.arc(90, 65, 5, 0, Math.PI * 2, true);
ctx.stroke();
``` 

![[Pasted image 20240527203534.png]]



# Trasformations and rotations 
Translate(x, y): moves the canvas and its origin on the grid. x indicates the horizontal distance to move, and y indicates how far to move the grid vertically

Rotate(angle): rotates the canvas clockwise around the current origin by the angle number of radians

## Saving canvas state and restore 

A drawing state consists of:
- The transformations that have been applied (i.e. translate, rotate and scale).
- The current values of some attributes associated to the style.
- The current clipping path (clipping path is like a normal canvas shape but it acts as a mask to hide unwanted parts of shapes).

save(): saves the entire state of the canvas.
restore(): restores the most recently saved canvas state. 

### Animations 
These are the steps you need to take to draw a frame: 

1. Clear the canvas: clear any shapes that have been drawn previously. The easiest way to do this is using the clearRect() method. 
2. Save the canvas state: if you're changing any setting (such as styles, transformations, etc.) which affect the canvas state and you want to make sure the original state is used each time a frame is drawn, you need to save that original state. 
3. Draw animated shapes: the step where you do the actual frame rendering. 
4. Restore the canvas state: if you've saved the state, restore it before drawing a new frame

##### Timers for the animations 
The window.setInterval(), window.setTimeout(), and window.requestAnimationFrame() functions can be used to call a specific function over a set period of time: 

-  **setInterval(function, delay)**: starts repeatedly executing the function specified by function every delay milliseconds.
- **setTimeout(function, delay)**: executes the function specified by function in delay milliseconds. 
- **requestAnimationFrame(callback)**: tells the browser that you wish to perform an animation and requests that the browser call a specified function to update an animation before the next repaint.

## Examples of animations 
https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Basic_animations