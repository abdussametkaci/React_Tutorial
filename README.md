# React_Tutorial
Reference: [w3shools](https://www.w3schools.com/react/default.asp)

## Create React App
The create-react-app tool is an officially supported way to create React applications.

Node.js is required to use create-react-app.

Open your terminal in the directory you would like to create your application.

Run this command to create a React application named my-react-app:
```
npx create-react-app my-react-app
```

## Run the React Application
Run this command to move to the my-react-app directory:
```
cd my-react-app
```
Run this command to execute the React application my-react-app:
```
npm start
```
A new browser window will pop up with your newly created React App! If not, open your browser and type [http://localhost:3000](http://localhost:3000) in the address bar.

## What is React?
React, sometimes referred to as a frontend JavaScript framework, is a JavaScript library created by Facebook.

React is a tool for building UI components.

## How does React Work?
```
React creates a VIRTUAL DOM in memory.
```

Instead of manipulating the browser's DOM directly, React creates a virtual DOM in memory, where it does all the necessary manipulating, before making the changes in the browser DOM.

```
React only changes what needs to be changed!
```

React finds out what changes have been made, and changes **only** what needs to be changed.

## React ES6 Classes
### Classes
ES6 introduced classes.

A class is a type of function, but instead of using the keyword function to initiate it, we use the keyword class, and the properties are assigned inside a constructor() method.
A simple class constructor:

``` javascript
class Car {
  constructor(name) {
    this.brand = name;
  }
}
```

Now you can create objects using the Car class:

``` javascript
class Car {
  constructor(name) {
    this.brand = name;
  }
}

mycar = new Car("Ford");
```

### Method in Classes
You can add your own methods in a class:

``` javascript
class Car {
  constructor(name) {
    this.brand = name;
  }
  
  present() {
    return 'I have a ' + this.brand;
  }
}

mycar = new Car("Ford");
mycar.present();
```

### Class Inheritance
To create a class inheritance, use the extends keyword.

A class created with a class inheritance inherits all the methods from another class:

``` javascript
class Car {
  constructor(name) {
    this.brand = name;
  }

  present() {
    return 'I have a ' + this.brand;
  }
}

class Model extends Car {
  constructor(name, mod) {
    super(name);
    this.model = mod;
  }  
  show() {
      return this.present() + ', it is a ' + this.model
  }
}
mycar = new Model("Ford", "Mustang");
mycar.show();
```

The **super()** method refers to the parent class.

By calling the **super()** method in the constructor method, we call the parent's constructor method and gets access to the parent's properties and methods.

Run Code for Classes: [React Classes](https://abdussametkaci.github.io/React_Tutorial/my-react-app/src/classes.html)

## React ES6 Arrow Functions
### Arrow Functions
Arrow functions allow us to write shorter function syntax:

``` javascript
hello = () => {
  return "Hello World!";
}
```

It gets shorter! If the function has only one statement, and the statement returns a value, you can remove the brackets and the return keyword:

``` javascript
hello = () => "Hello World!";
```

**Note:** This works only if the function has only one statement.

If you have parameters, you pass them inside the parentheses:

``` javascript
hello = (val) => "Hello " + val;
```

In fact, if you have only one parameter, you can skip the parentheses as well:

``` javascript
hello = val => "Hello " + val;
```

### What About this?
The handling of **this** is also different in arrow functions compared to regular functions.

In short, with arrow functions there are no binding of **this**.

In regular functions the **this** keyword represented the object that called the function, which could be the window, the document, a button or whatever.

With arrow functions, the **this** keyword always represents the object that defined the arrow function.

Let us take a look at two examples to understand the difference.

Both examples call a method twice, first when the page loads, and once again when the user clicks a button.

The first example uses a regular function, and the second example uses an arrow function.

The result shows that the first example returns two different objects (window and button), and the second example returns the Header object twice.

Example: With a regular function, this represents the object that called the function:

``` javascript
class Header {
  constructor() {
    this.color = "Red";
  }

//Regular function:
  changeColor = function() {
    document.getElementById("demo").innerHTML += this;
  }
}

myheader = new Header();

//The window object calls the function:
window.addEventListener("load", myheader.changeColor);

//A button object calls the function:
document.getElementById("btn").addEventListener("click", myheader.changeColor);
```

Reasult:

```
[object Window][object HTMLButtonElement]
```

Example: With an arrow function, this represents the Header object no matter who called the function:

``` javascript
class Header {
  constructor() {
    this.color = "Red";
  }

//Arrow function:
  changeColor = () => {
    document.getElementById("demo").innerHTML += this;
  }
}

myheader = new Header();


//The window object calls the function:
window.addEventListener("load", myheader.changeColor);

//A button object calls the function:
document.getElementById("btn").addEventListener("click", myheader.changeColor);
```

Reasult:

```
[object Object][object Object]
```

Run Code for Arrow Function: [React Classes](https://abdussametkaci.github.io/React_Tutorial/my-react-app/src/arrowFunctions.html)

## React ES6 Variables
Before ES6 there were only one way of defining your variables: with the var keyword. If you did not define them, they would be assigned to the global object. Unless you were in strict mode, then you would get an error if your variables were undefined.

Now, with ES6, there are three ways of defining your variables: **var**, **let**, and **const**.

### var

``` javascript
var x = 5.6;
```

If you use **var** outside of a function, it belongs to the global scope.

If you use **var** inside of a function, it belongs to that function.

If you use **var** inside of a block, i.e. a for loop, the variable is still available outside of that block.

**var has a function scope, not a block scope.**

### let

``` javascript
let x = 5.6;
```

**let** is the block scoped version of var, and is limited to the block (or expression) where it is defined.

If you use **let** inside of a block, i.e. a for loop, the variable is only available inside of that loop.

**let has a block scope.**

### const

``` javascript
const x = 5.6;
```

**const** is a variable that once it has been created, its value can never change.

**const has a block scope.**

## React ES6 Array Methods
### Array Methods
There are many JavaScript array methods.

One of the most useful in React is the **.map()** array method.

The **.map()** method allows you to run a function on each item in the array, returning a new array as the result.

In React, **map()** can be used to generate lists.

``` jsx
import React from 'react';
import ReactDOM from 'react-dom';

const myArray = ['apple', 'banana', 'orange'];

const myList = myArray.map((item) => <p>{item}</p>)

ReactDOM.render(myList, document.getElementById('root'));
```

Result:

```
apple

banana

orange
```

## React ES6 Destructuring
### Destructuring
To illustrate destructuring, we'll make a sandwich. Do you take everything out of the refrigerator to make your sandwich? No, you only take out the items you would like to use on your sandwich.

Destructuring is exactly the same. We may have an array or object that we are working with, but we only need some of the items contained in these.

Destructuring makes it easy to extract only what is needed.

### Destructing Arrays
Here is the old way of assigning array items to a variable:

Before:

``` javascript
const vehicles = ['mustang', 'f-150', 'expedition'];

// old way
const car = vehicles[0];
const truck = vehicles[1];
const suv = vehicles[2];
```

Here is the new way of assigning array items to a variable:

With destructuring:

``` javascript
const vehicles = ['mustang', 'f-150', 'expedition'];

const [car, truck, suv] = vehicles;
```

If we only want the car and suv we can simply leave out the truck but keep the comma:

``` javascript
const vehicles = ['mustang', 'f-150', 'expedition'];

const [car,, suv] = vehicles;
```

Destructuring comes in handy when a function returns an array:

``` javascript
function calculate(a, b) {
  const add = a + b;
  const subtract = a - b;
  const multiply = a * b;
  const divide = a / b;

  return [add, subtract, multiply, divide];
}

const [add, subtract, multiply, divide] = calculate(4, 7);
```

Run Code for Destructing Array: [Destruct Array](https://abdussametkaci.github.io/React_Tutorial/my-react-app/src/destructArray.html)

### Destructuring Objects
Here is the old way of using an object inside a function:

``` javascript
const vehicleOne = {
  brand: 'Ford',
  model: 'Mustang',
  type: 'car',
  year: 2021, 
  color: 'red'
}

myVehicle(vehicleOne);

// old way
function myVehicle(vehicle) {
  const message = 'My ' + vehicle.type + ' is a ' + vehicle.color + ' ' + vehicle.brand + ' ' + vehicle.model + '.';
}
```

Here is the new way of using an object inside a function:

``` javascript
const vehicleOne = {
  brand: 'Ford',
  model: 'Mustang',
  type: 'car',
  year: 2021, 
  color: 'red'
}

myVehicle(vehicleOne);

function myVehicle({type, color, brand, model}) {
  const message = 'My ' + type + ' is a ' + color + ' ' + brand + ' ' + model + '.';
}
```

**Notice that the object properties do not have to be declared in a specific order.**

We can even destructure deeply nested objects by referencing the nested object then using a colon and curly braces to again destructure the items needed from the nested object:

``` javascript
const vehicleOne = {
  brand: 'Ford',
  model: 'Mustang',
  type: 'car',
  year: 2021, 
  color: 'red',
  registration: {
    city: 'Houston',
    state: 'Texas',
    country: 'USA'
  }
}

myVehicle(vehicleOne)

function myVehicle({ model, registration: { state } }) {
  const message = 'My ' + model + ' is registered in ' + state + '.';
}
```

Result:

```
My Mustang is registered in Texas.
```

Run Code for Destructing Object: [Destruct Object](https://abdussametkaci.github.io/React_Tutorial/my-react-app/src/destructObject.html)

## React ES6 Spread Operator
### Spread Operator
The JavaScript spread operator (...) allows us to quickly copy all or part of an existing array or object into another array or object.

``` javascript
const numbersOne = [1, 2, 3];
const numbersTwo = [4, 5, 6];
const numbersCombined = [...numbersOne, ...numbersTwo] // 1,2,3,4,5,6
```

The spread operator is often used in combination with destructuring.

``` javascript
const numbers = [1, 2, 3, 4, 5, 6];

const [one, two, ...rest] = numbers;
// one -> 1
// two -> 2
// rest -> 3,4,5,6
```

We can use the spread operator with objects too:

``` javascript
const myVehicle = {
  brand: 'Ford',
  model: 'Mustang',
  color: 'red'
}

const updateMyVehicle = {
  type: 'car',
  year: 2021, 
  color: 'yellow'
}

const myUpdatedVehicle = {...myVehicle, ...updateMyVehicle}
/*
{
    brand: "Ford"
    color: "yellow"
    model: "Mustang"
    type: "car"
    year: 2021
}
*/
```

**Notice the properties that did not match were combined, but the property that did match, color, was overwritten by the last object that was passed, updateMyVehicle. The resulting color is now yellow.**

## React ES6 Modules
### Modules
JavaScript modules allow you to break up your code into separate files.

This makes it easier to maintain the code-base.

ES Modules rely on the **import** and **export** statements.

### Export
You can export a function or variable from any file.

Let us create a file named **person.js**, and fill it with the things we want to export.

There are two types of exports: Named and Default.

### Named Exports
You can create named exports two ways. In-line individually, or all at once at the bottom.

In-line individually:

``` javascript
export const name = "Jesse"
export const age = "40"
```

All at once at the bottom:

``` javascript
const name = "Jesse"
const age = "40"

export { name, age }
```

### Default Exports
Let us create another file, named **message.js**, and use it for demonstrating default export.

You can only have one default export in a file.

``` javascript
const message = () => {
  const name = "Jesse";
  const age = "40";
  return name + ' is ' + age + 'years old.';
};

export default message;
```

### Import
You can import modules into a file in two ways, based on if they are named exports or default exports.

Named exports must be destructured using curly braces. Default exports do not.

### Import from named exports
``` javascript
import { name, age } from "./person.js";
```

Run Code for Named Export: [Named Export](https://abdussametkaci.github.io/React_Tutorial/my-react-app/src/importNamedExport.html)

### Import from default exports
``` javascript
import message from "./message.js";
```

Run Code for Default Export: [Default Export](https://abdussametkaci.github.io/React_Tutorial/my-react-app/src/importNamedExport.html)

## React ES6 Ternary Operator
### Ternary Operator
The ternary operator is a simplified conditional operator like if / else.

Syntax: condition ? <expression if true> : <expression if false>

Here is an example using if / else:

``` javascript
if (authenticated) {
  renderApp();
} else {
  renderLogin();
}
```

Here is the same example using a ternary operator:

``` javascript
authenticated ? renderApp() : renderLogin();
```

Run Code for Ternary Operator: [Ternary Operator](https://abdussametkaci.github.io/React_Tutorial/my-react-app/src/ternaryOperator.html)

## React Render HTML
React's goal is in many ways to render HTML in a web page.

React renders HTML to the web page by using a function called **ReactDOM.render()**.

### The Render Function
The **ReactDOM.render()** function takes two arguments, HTML code and an HTML element.

The purpose of the function is to display the specified HTML code inside the specified HTML element.

But render where?

There is another folder in the root directory of your React project, named "public". In this folder, there is an index.html file.

You'll notice a single **<div>** in the body of this file. This is where our React application will be rendered.

``` javascript
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(<p>Hello</p>, document.getElementById('root'));
```

### The HTML Code
The HTML code in this tutorial uses JSX which allows you to write HTML tags inside the JavaScript code:

``` javascript
const myelement = (
  <table>
    <tr>
      <th>Name</th>
    </tr>
    <tr>
      <td>John</td>
    </tr>
    <tr>
      <td>Elsa</td>
    </tr>
  </table>
);

ReactDOM.render(myelement, document.getElementById('root'));
```

Result:

```
Name
John
Elsa
```

### The Root Node
The root node is the HTML element where you want to display the result.

It is like a container for content managed by React.

It does NOT have to be a <div> element and it does NOT have to have the id='root':

The root node can be called whatever you like:

``` html
<body>
  <header id="sandy"></header>
</body>
```

Display the result in the <header id="sandy"> element:

``` javascript
ReactDOM.render(<p>Hallo</p>, document.getElementById('sandy'));
```

## React JSX
JSX stands for JavaScript XML.

JSX allows us to write HTML in React.

JSX makes it easier to write and add HTML in React.

### Coding JSX
JSX allows us to write HTML elements in JavaScript and place them in the DOM without any **createElement()**  and/or **appendChild()** methods.

JSX converts HTML tags into react elements.

You are not required to use JSX, but JSX makes it easier to write React applications.

#### Example 1
``` javascript
import React from 'react';
import ReactDOM from 'react-dom';

const myelement = <h1>I Love JSX!</h1>;

ReactDOM.render(myelement, document.getElementById('root'));
```

#### Example 2
``` javascript
import React from 'react';
import ReactDOM from 'react-dom';

const myelement = React.createElement('h1', {}, 'I do not use JSX!');

ReactDOM.render(myelement, document.getElementById('root'));
```

### Expressions in JSX
``` javascript
const myelement = <h1>React is {5 + 5} times better with JSX</h1>;
```

### Inserting a Large Block of HTML
To write HTML on multiple lines, put the HTML inside parentheses:
``` javascript
const myelement = (
  <ul>
    <li>Apples</li>
    <li>Bananas</li>
    <li>Cherries</li>
  </ul>
);
```

### One Top Level Element
The HTML code must be wrapped in ONE top level element.

So if you like to write two paragraphs, you must put them inside a parent element, like a **div** element.
``` javascript
const myelement = (
  <div>
    <p>I am a paragraph.</p>
    <p>I am a paragraph too.</p>
  </div>
);
```

Note: JSX will throw an error if the HTML is not correct, or if the HTML misses a parent element.

Alternatively, you can use a "fragment" to wrap multiple lines. This will prevent unnecessarily adding extra nodes to the DOM.

A fragment looks like an empty HTML tag: **<></>**.
``` javascript
const myelement = (
<>
<p>I am a paragraph.</p>
<p>I am a paragraph too.</p>
</>
);
```

### Elements Must be Closed
JSX follows XML rules, and therefore HTML elements must be properly closed.
``` javascript
const myelement = <input type="text" />;
```

### Attribute class = className
The **class** attribute is a much used attribute in HTML, but since JSX is rendered as JavaScript, and the **class** keyword is a reserved word in JavaScript, you are not allowed to use it in JSX.

Use attribute **className** instead.

JSX solved this by using **className** instead. When JSX is rendered, it translates **className** attributes into **class** attributes.
``` javascript
const myelement = <h1 className="myclass">Hello World</h1>;
```

### Conditions - if statements
React supports **if** statements, but not inside JSX.

To be able to use conditional statements in JSX, you should put the **if** statements outside of the JSX, or you could use a ternary expression instead:

#### Option 1:
Write if statements outside of the JSX code:
``` javascript
const x = 5;
let text = "Goodbye";
if (x < 10) {
  text = "Hello";
}

const myelement = <h1>{text}</h1>;
```

#### Option 2:
Use ternary expressions instead:
``` javascript
const x = 5;
const myelement = <h1>{(x) < 10 ? "Hello" : "Goodbye"}</h1>;
```