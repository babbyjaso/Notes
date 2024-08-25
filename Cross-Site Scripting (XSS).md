- very flexible vulnerability
	- can chain different issues together
- lets us execute javascript in a victims browser and can give us control over the application via that user.
- three different types
	- Reflected
		- the script you're trying to inject is coming from the current HTTP request
		- send request, get response, script is in the response
		- This only works for you
			- if you make it via a URI, you can entice someone to click on a link and achieve pwn
	- Stored
		- payload is stored in a DB, retrieved later
		- can be accessed by anyone
	- DOM-based
		- Everything happens locally in the browser
- Basic test:
	- `alert(1)`
		- this is super filtered, so you should use these alternatives
	- `print()`
	- `prompt('hello')`
	- [More reading](https://portswigger.net/research/alert-is-dead-long-live-print)
- how to put a basic keylogger on your browser:
```
function logKey(event){console.log(event.key)}
document.addEventListner('keydown'. logKey)
```
- if you don't know a javascript, go through the W3 schools javascript classes
	- he recommends functions specifically
	- god i gotta do js rip