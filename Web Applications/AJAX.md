Historically, AJAX stands for Asynchronous JavaScript And XML, an acronym
containing the technologies used at the time (JavaScript and XML). AJAX now
indicates a group of technologies that offer asynchronous functionality in the browser.

### Synchronous vs Asynchronous 
### Synchronous
When a browser comes across a tag, it will typically stop processing the rest of the page until is has loaded and processed it. This is an example of synchronous processing model
### Asynchronous
AJAX instead uses an asynchronous (non-blocking) processing model, i.e. the user can do other things while the web browser is waiting for the data to load, speeding up the user experience. 


### XMLHttpRequest
AJAX uses the XMLHttpRequest object to communicate with servers

``` javascript
var request = new XMLHttpRequest(); 
```

## Perform a request
``` javascript
// open the request
request.open('GET', 'http://www.example.org/some.file');
// set the necessary headers 
request.setRequestHeader("Content-Type", "text/plain");
// function that handles when the function is performed
request.onload = nameOfTheFunction;
//send the request 
request.send();
```
- As security feature, you cannot call URLs on third-party domains  (avoidable with [[#Cross Origin Resource Sharing (CORS)|CORS]])

To pass data in this request we can both:
1. Form-encoded requests: `find=pizza&zipcode=02134&radius=1km`
2. Form data encoding format has a formal MIME type like `application/x-www-form-urlencoded`
3. Json-encoded requests like by setting the `request.setRequestHeader("Content-Type", "application/json");`

### Cross Origin Resource Sharing (CORS)
Cross-Origin Resource Sharing, (CORS): is a mechanism that uses additional HTTP headers to let a user agent gain permission to access selected resources from a server on a different origin (domain) than the site currently in use. A user agent makes a cross-origin HTTP request when it requests a resource from a different domain, protocol, or port than the one from which the current document originated.

Example: A HTML page served from http://domain-a.com makes an <img> src request for http://domain-b.com/image.jpg. 

note that normally these **do not** include any user credentials


### Respose method
``` javascript
request.onload = nameOfTheFunction;
```
the response method needs also to check for the answer by checking XMLHttpRequest.DONE
or these falues of readyState values is as follows :
- 0 (uninitialized) or (request not initialized), open() has not been called yet;
- 1 (loading) or (server connection established), open() has been called;
- 2 (loaded) or (request received), headers have been received;
- 3 (interactive) or (processing request), the response body is being received;
- 4 (complete) or (request finished and response is ready), the response is complete.


and that the response of the server is successful:
``` javascript 
request.status == 200
```


#### Parsing of the response
- request.responseText – returns the server response as a string of text;
- request.responseXML – returns the response as an XMLDocument object you can traverse with JavaScript DOM functions


# Types of receivable data from ajax 
### Html 
- easy to write, request , display 
- no good for portability(data only for browsers)
## Xml :
- flexible even for complex structures 
- uses HTML DOM  methods for parsing 
## JSON:
- can be called from any domain(CORS); 
- more coincise 
- Strict syntax (just a wrong comma can broke it )
- passive to malicious attacks since is essentially javascript code 


# Json parsing 

When it reaches the browser, a script must convert the string into a JavaScript object — deserialization of the object — through the parse() method of the JSON object,
so you do not need to instantiate it.

The method JSON.stringify() converts objects into a string using JSON notation, thus to send the object from the browser back to the server, a.k.a. serialization of the object

``` javascript
responseObject = JSON.parse(xhr.responseText);
```


## Fetch 
new way to send request to servers(to note that is not supported in older browsers)
``` javascript 
// default is HTTP 
var promise = fetch(url, [options])
```
The JavaScript Fetch object is based on the use of a Promise, an object that encapsulates the result of an asynchronous operation .

The idea that it will resolve(aka change) when an answer is returned from the server turning into a an object Response.

``` javascript 
let response = await fetch(url);
if (response.ok) { // if HTTP-status is 200-299
 //receive the body of the answer
 let json = await response.json();
} else {
 alert("HTTP-Error: " + response.status);
}
```

 to not he use of **await** to wait for the fulfilled value of the proise 
 
