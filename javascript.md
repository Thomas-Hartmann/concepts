# Javascript
[functions](###)
[data types](###)
[array](###)
[object](###)
[closure](###)
[callback](###)
[event loop](###)
[promises](###)
[fetch](###-Fetch)
[this operator](###-this)
[scope](###-scope)
[node js](###-node)

### Functions
### Data Types
### Array
### Object
### Closure
### Callback
### Event Loop
[Good read](https://medium.com/front-end-hacking/javascript-event-loop-explained-4cd26af121d4)  
![](media/js_event_loop.png)

**Web API** in this case is browser events that are caught by eventhandlers. These event handlers send callbacks to the callback queue whenever an event occurs.
Each callback is garantied to run entirely (not interrupted). The queue submit each callback to the function stack whenever the stack is empty.
The callback functions will only get executed whenever the stack is empty again. This means that all code in the stack will run entirely before new callbacks are commited. (If callbacks where put on top of the stack it would run before some other code there)

### Promises
### Fetch 
### this operator 
### Fetch
```javascript
let options = {
   method: "POST",
   headers: {
   'Accept': 'application/json',
   'Content-Type': 'application/json'
   },
   body: JSON.stringify({
     age: 34,
     name: "lis Benson",
     gender: "female",
     email: "lis@lis.com"
   })
}
fetch("http://localhost:3000/users",options);

```
A problem, which has annoyed many developers is that fetch only rejects a promise when “a network error is encountered, although this usually means permissions issues or similar.”
When a promise is rejected we can “catch” it as sketched below (using arrow notation for simplicity)
```javascript
fetch('https://swapi.co/api/people/999999999999')
 .then(res=> res.json())
 .then(data => console.log(data.name))
 .catch(err =>console.log("UPPS"));
```
Solution:
```javascript
function handleHttpErrors(res){
 if(!res.ok){
   return Promise.reject({status: res.status, fullError: res.json() })
 }
 return res.json();
}

fetch('https://swapi.co/api/people/999999999999')
 .then(handleHttpErrors)
 .then(data => console.log(data.name))
 .catch(err =>{
    if(err.status){
      err.fullError.then(e=> console.log(e.detail))
    }
    else{console.log("Network error"); }
 });

```
Helper method:
```javascript
function makeOptions(method, body) {
 var opts =  {
   method: method,
   headers: {
     "Content-type": "application/json"
   }
 }
 if(body){
   opts.body = JSON.stringify(body);
 }
 return opts;
}

can make the POST request from our previous example as simple as this:

const data = {age: 34,name: "lis Benson", gender: "female",email: "lis@lis.com"};
const options = makeOptions("POST",data);
fetch("http://localhost:3000/users",options);

```

### node
- Start a new project
   - `mkdir <folder>`
   - `cd <folder>`
   - `npm init`
   - `touch server.js`
   - `touch README.md`
   - `code .`
   - `npm install express --save`
   - `npm install nodemon --save-dev` Installs nodemon to enable auto restart server whenever a file is saved in the project.
   - Add to package.json: `"scripts": { "dev": "nodemon server.js"}`
   - Start server with `npm run dev`
   - install body-parser to enable express to read form parameters: `npm install body-parser --save`
   - install mongodb: `npm install mongodb --save`
   - 

### this
- `this` is a reference to the functions calling context.
- calling context is the last function on the callstack
```js
function foo(){
  const a = 1;
  console.log(this.b, a) // 2 1
}
function bar(){
  const b = 2;
  console.log(this.c) // 3
  console.log(this.z) // undefined
  console.log(window.z) // undefined
  foo();
}
function baz(){
  const c = 3;
  var z = 26;
  console.log(this.d) // 4 - from the global object: window.d
  console.log(window.d) // 4 - from the global object: window.d
  console.log(window.e) // undefined
  bar();
}
var d = 4;
let e = 5;
baz();
```

### scope
lexical scope or static scope means that variable scope is determined at compiletime -> inner functions contain the scope of parent functions even if the parent function has returned.
```js
var a = 20;
window.a // 20
```