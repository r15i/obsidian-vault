Form validiation of data from the client:
- get right data in the right format for the server 
- protect he user's accounts by enforcing password policies 
- protection from the misues of the forms(XSS)

# Types of validations 
#### client side validation:
- by [[JavaScript]] 
- by bulilt in [[HTML5]] 
#### server side validation:
- not as user frendly 
- need to send back an error message 

#### HTML5 validation:
the element matches the style :valid or :invalid css pseudo class based on the request required pattern of the input method



``` css 
input:invalid {
border: 2px dashed red;}
input:valid {
 border: 2px solid black;}
``` 


``` html 
<body>
 <form>
<label for="choose">In which course are you enrolled?
Informatics or ICT?</label>
<input id="choose" name="course" required pattern=“Informatics|
ICT|Cybersecurity">
<button>Submit</button>
 </form>
</body>
</html>

```


### Validity api Html5 
HTML5 provides the constraint validation API to check and
customize the state of a form element. Among other things,
it's possible to change the text of the error message with the
setCustomValidity() method.
``` javascript 
var email = document.getElementById("provide_email");
email.addEventListener("input", function (event) {
if (email.validity.typeMismatch) {
	email.setCustomValidity("Please insert an email address!");
} else {
	email.setCustomValidity("");
}
});
``` 


### Validating forms without a built-in Api with javascript 
a good validation strategy should Answer these questions :
- what kind of validation should i perform?
- what to do if the form does not validate? 
- how can i help the user to correct invalid data?

for the form validation essentially he uses a regula expression like this to check if the email is correct 

``` javascript 
var mailRegExp = /^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/;
// This defines what happens when the user insert the email text
email.addEventListener("input", function () {
// here it creates the check by using the regex as an expression 
var test = email.value.length === 0 || mailRegExp.test(email.value);
if (test) {
	email.className = "valid";
	error.innerHTML = "";
} else {
	email.className = "invalid";
	error.innerHTML = "Please insert an e-mail address";
	error.className = "error";
 }
});
```



