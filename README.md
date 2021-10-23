# React_Tutorial
Reference: [w3shools](https://www.w3schools.com/react/default.asp)

You can try all code in **index.js**.

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

``` jsx
class Car {
  constructor(name) {
    this.brand = name;
  }
}
```

Now you can create objects using the Car class:

``` jsx
class Car {
  constructor(name) {
    this.brand = name;
  }
}

mycar = new Car("Ford");
```

### Method in Classes
You can add your own methods in a class:

``` jsx
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

``` jsx
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

``` jsx
hello = () => {
  return "Hello World!";
}
```

It gets shorter! If the function has only one statement, and the statement returns a value, you can remove the brackets and the return keyword:

``` jsx
hello = () => "Hello World!";
```

**Note:** This works only if the function has only one statement.

If you have parameters, you pass them inside the parentheses:

``` jsx
hello = (val) => "Hello " + val;
```

In fact, if you have only one parameter, you can skip the parentheses as well:

``` jsx
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

``` jsx
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

``` jsx
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

``` jsx
var x = 5.6;
```

If you use **var** outside of a function, it belongs to the global scope.

If you use **var** inside of a function, it belongs to that function.

If you use **var** inside of a block, i.e. a for loop, the variable is still available outside of that block.

**var has a function scope, not a block scope.**

### let

``` jsx
let x = 5.6;
```

**let** is the block scoped version of var, and is limited to the block (or expression) where it is defined.

If you use **let** inside of a block, i.e. a for loop, the variable is only available inside of that loop.

**let has a block scope.**

### const

``` jsx
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

``` jsx
const vehicles = ['mustang', 'f-150', 'expedition'];

// old way
const car = vehicles[0];
const truck = vehicles[1];
const suv = vehicles[2];
```

Here is the new way of assigning array items to a variable:

With destructuring:

``` jsx
const vehicles = ['mustang', 'f-150', 'expedition'];

const [car, truck, suv] = vehicles;
```

If we only want the car and suv we can simply leave out the truck but keep the comma:

``` jsx
const vehicles = ['mustang', 'f-150', 'expedition'];

const [car,, suv] = vehicles;
```

Destructuring comes in handy when a function returns an array:

``` jsx
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

``` jsx
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

``` jsx
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

``` jsx
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

``` jsx
const numbersOne = [1, 2, 3];
const numbersTwo = [4, 5, 6];
const numbersCombined = [...numbersOne, ...numbersTwo] // 1,2,3,4,5,6
```

The spread operator is often used in combination with destructuring.

``` jsx
const numbers = [1, 2, 3, 4, 5, 6];

const [one, two, ...rest] = numbers;
// one -> 1
// two -> 2
// rest -> 3,4,5,6
```

We can use the spread operator with objects too:

``` jsx
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

``` jsx
export const name = "Jesse"
export const age = "40"
```

All at once at the bottom:

``` jsx
const name = "Jesse"
const age = "40"

export { name, age }
```

### Default Exports
Let us create another file, named **message.js**, and use it for demonstrating default export.

You can only have one default export in a file.

``` jsx
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
``` jsx
import { name, age } from "./person.js";
```

Run Code for Named Export: [Named Export](https://abdussametkaci.github.io/React_Tutorial/my-react-app/src/importNamedExport.html)

### Import from default exports
``` jsx
import message from "./message.js";
```

Run Code for Default Export: [Default Export](https://abdussametkaci.github.io/React_Tutorial/my-react-app/src/importNamedExport.html)

## React ES6 Ternary Operator
### Ternary Operator
The ternary operator is a simplified conditional operator like if / else.

Syntax: condition ? <expression if true> : <expression if false>

Here is an example using if / else:

``` jsx
if (authenticated) {
  renderApp();
} else {
  renderLogin();
}
```

Here is the same example using a ternary operator:

``` jsx
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

``` jsx
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(<p>Hello</p>, document.getElementById('root'));
```

### The HTML Code
The HTML code in this tutorial uses JSX which allows you to write HTML tags inside the JavaScript code:

``` jsx
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

``` jsx
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
``` jsx
import React from 'react';
import ReactDOM from 'react-dom';

const myelement = <h1>I Love JSX!</h1>;

ReactDOM.render(myelement, document.getElementById('root'));
```

#### Example 2
``` jsx
import React from 'react';
import ReactDOM from 'react-dom';

const myelement = React.createElement('h1', {}, 'I do not use JSX!');

ReactDOM.render(myelement, document.getElementById('root'));
```

### Expressions in JSX
``` jsx
const myelement = <h1>React is {5 + 5} times better with JSX</h1>;
```

### Inserting a Large Block of HTML
To write HTML on multiple lines, put the HTML inside parentheses:
``` jsx
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
``` jsx
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
``` jsx
const myelement = (
<>
<p>I am a paragraph.</p>
<p>I am a paragraph too.</p>
</>
);
```

### Elements Must be Closed
JSX follows XML rules, and therefore HTML elements must be properly closed.
``` jsx
const myelement = <input type="text" />;
```

### Attribute class = className
The **class** attribute is a much used attribute in HTML, but since JSX is rendered as JavaScript, and the **class** keyword is a reserved word in JavaScript, you are not allowed to use it in JSX.

Use attribute **className** instead.

JSX solved this by using **className** instead. When JSX is rendered, it translates **className** attributes into **class** attributes.
``` jsx
const myelement = <h1 className="myclass">Hello World</h1>;
```

### Conditions - if statements
React supports **if** statements, but not inside JSX.

To be able to use conditional statements in JSX, you should put the **if** statements outside of the JSX, or you could use a ternary expression instead:

#### Option 1:
Write if statements outside of the JSX code:
``` jsx
const x = 5;
let text = "Goodbye";
if (x < 10) {
  text = "Hello";
}

const myelement = <h1>{text}</h1>;
```

#### Option 2:
Use ternary expressions instead:
``` jsx
const x = 5;
const myelement = <h1>{(x) < 10 ? "Hello" : "Goodbye"}</h1>;
```

## React Components
Components are independent and reusable bits of code. They serve the same purpose as JavaScript functions, but work in isolation and return HTML.

Components come in two types, Class components and Function components.
```
In older React code bases, you may find Class components primarily used. 
It is now suggested to use Function components along with Hooks, which 
were added in React 16.8. There is an optional section on Class components 
for your reference.
```

### Create Your First Component
When creating a React component, the component's name MUST start with an upper case letter.

#### Class Component
A class component must include the **extends React.Component** statement. This statement creates an inheritance to React.Component, and gives your component access to React.Component's functions.

The component also requires a **render()** method, this method returns HTML.
``` jsx
class Car extends React.Component {
  render() {
    return <h2>Hi, I am a Car!</h2>;
  }
}
```

#### Function Component
Here is the same example as above, but created using a Function component instead.

A Function component also returns HTML, and behaves much the same way as a Class component, but Function components can be written using much less code, are easier to understand, and will be preferred in this tutorial.
``` jsx
function Car() {
  return <h2>Hi, I am a Car!</h2>;
}
```

### Rendering a Component
Now your React application has a component called Car, which returns an ```<h2>``` element.
To use this component in your application, use similar syntax as normal HTML: ```<Car />```
``` jsx
ReactDOM.render(<Car />, document.getElementById('root'));
```

### Props
Components can be passed as **props**, which stands for properties.

Props are like function arguments, and you send them into the component as attributes.
``` jsx
function Car(props) {
  return <h2>I am a {props.color} Car!</h2>;
}

ReactDOM.render(<Car color="red"/>, document.getElementById('root'));
```

Result:
```
I am a red Car!
```

### Components in Components
We can refer to components inside other components:
``` jsx
function Car() {
  return <h2>I am a Car!</h2>;
}

function Garage() {
  return (
    <>
      <h1>Who lives in my Garage?</h1>
      <Car />
    </>
  );
}

ReactDOM.render(<Garage />, document.getElementById('root'));
```

### Components in Files
React is all about re-using code, and it is recommended to split your components into separate files.

To do that, create a new file with a **.js** file extension and put the code inside it:
```
Note that the filename must start with an uppercase character.
```

``` jsx
function Car() {
  return <h2>Hi, I am a Car!</h2>;
}

export default Car;
```

To be able to use the Car component, you have to import the file in your application.
``` jsx
import React from 'react';
import ReactDOM from 'react-dom';
import Car from './Car.js';

ReactDOM.render(<Car />, document.getElementById('root'));
```

## React Class Components
Before React 16.8, Class components were the only way to track state and lifecycle on a React component. Function components were considered "state-less".

With the addition of Hooks, Function components are now almost equivalent to Class components. The differences are so minor that you will probably never need to use a Class component in React.

Even though Function components are preferred, there are no current plans on removing Class components from React.

### Create a Class Component
When creating a React component, the component's name must start with an upper case letter.

The component has to include the extends React.Component statement, this statement creates an inheritance to React.Component, and gives your component access to React.Component's functions.

The component also requires a render() method, this method returns HTML.
``` jsx
class Car extends React.Component {
  render() {
    return <h2>Hi, I am a Car!</h2>;
  }
}
```

### Component Constructor
If there is a constructor() function in your component, this function will be called when the component gets initiated.

The constructor function is where you initiate the component's properties.

In React, component properties should be kept in an object called **state**.

The constructor function is also where you honor the inheritance of the parent component by including the **super()** statement, which executes the parent component's constructor function, and your component has access to all the functions of the parent component (**React.Component**).
``` jsx
class Car extends React.Component {
  constructor() {
    super();
    this.state = {color: "red"};
  }
  render() {
    return <h2>I am a {this.state.color} Car!</h2>; // I am a red Car!
  }
}
```

### Props
Another way of handling component properties is by using **props**.

Props are like function arguments, and you send them into the component as attributes.
``` jsx
class Car extends React.Component {
  render() {
    return <h2>I am a {this.props.color} Car!</h2>;
  }
}

ReactDOM.render(<Car color="red"/>, document.getElementById('root'));
```

### Props in the Constructor
If your component has a constructor function, the props should always be passed to the constructor and also to the React.Component via the **super()** method.
``` jsx
class Car extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <h2>I am a {this.props.model}!</h2>;
  }
}
// I am a Mustang!
ReactDOM.render(<Car model="Mustang"/>, document.getElementById('root'));
```

### Components in Components
``` jsx
class Car extends React.Component {
  render() {
    return <h2>I am a Car!</h2>;
  }
}

class Garage extends React.Component {
  render() {
    return (
      <div>
      <h1>Who lives in my Garage?</h1>
      <Car />
      </div>
    );
  }
}

ReactDOM.render(<Garage />, document.getElementById('root'));
```

### React Class Component State
React Class components have a built-in **state** object.

You might have noticed that we used **state** earlier in the component constructor section.

The **state** object is where you store property values that belongs to the component.

When the **state** object changes, the component re-renders.

### Creating the state Object
The state object is initialized in the constructor:
``` jsx
class Car extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      brand: "Ford",
      model: "Mustang",
      color: "red",
      year: 1964
    };
  }
  render() {
    return (
      <div>
        <h1>My Car</h1>
      </div>
    );
  }
}
```

### Using the state Object
Refer to the state object anywhere in the component by using the this.state.propertyname syntax:
``` jsx
class Car extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      brand: "Ford",
      model: "Mustang",
      color: "red",
      year: 1964
    };
  }
  render() {
    return (
      <div>
        <h1>My {this.state.brand}</h1>
        <p>
          It is a {this.state.color}
          {this.state.model}
          from {this.state.year}.
        </p>
      </div>
    );
  }
}
```

Result:
```
My Ford -> <h1>
It is a red Mustang from 1964. -> <p>
```

### Changing the state Object
To change a value in the state object, use the **this.setState()** method.

When a value in the **state** object changes, the component will re-render, meaning that the output will change according to the new value(s).
``` jsx
class Car extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      brand: "Ford",
      model: "Mustang",
      color: "red",
      year: 1964
    };
  }
  changeColor = () => {
    this.setState({color: "blue"});
  }
  render() {
    return (
      <div>
        <h1>My {this.state.brand}</h1>
        <p>
          It is a {this.state.color}
          {this.state.model}
          from {this.state.year}.
        </p>
        <button
          type="button"
          onClick={this.changeColor}
        >Change color</button>
      </div>
    );
  }
}
```
```
Note: Always use the setState() method to change the state object, it will 
ensure that the component knows its been updated and calls the render() 
method (and all the other lifecycle methods).
```

### Lifecycle of Components
Each component in React has a lifecycle which you can monitor and manipulate during its three main phases.

The three phases are: **Mounting**, **Updating**, and **Unmounting**.

### Mounting
Mounting means putting elements into the DOM.

React has four built-in methods that gets called, in this order, when mounting a component:

1. **constructor()**
2. **getDerivedStateFromProps()**
3. **render()**
4. **componentDidMount()**

The **render()** method is required and will always be called, the others are optional and will be called if you define them.

#### constructor
The **constructor()** method is called before anything else, when the component is initiated, and it is the natural place to set up the initial **state** and other initial values.

The **constructor()** method is called with the **props**, as arguments, and you should always start by calling the **super(props)** before anything else, this will initiate the parent's constructor method and allows the component to inherit methods from its parent (**React.Component**).


``` jsx
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritecolor: "red"};
  }
  render() {
    return (
      <h1>My Favorite Color is {this.state.favoritecolor}</h1>
    );
  }
}
// My Favorite Color is red
ReactDOM.render(<Header />, document.getElementById('root'));
```

#### getDerivedStateFromProps
The **getDerivedStateFromProps()** method is called right before rendering the element(s) in the DOM.

This is the natural place to set the **state** object based on the initial **props**.

It takes **state** as an argument, and returns an object with changes to the **state**.

The example below starts with the favorite color being "red", but the **getDerivedStateFromProps()** method updates the favorite color based on the **favcol** attribute:
``` jsx
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritecolor: "red"};
  }
  static getDerivedStateFromProps(props, state) {
    return {favoritecolor: props.favcol };
  }
  render() {
    return (
      <h1>My Favorite Color is {this.state.favoritecolor}</h1>
    );
  }
}
// My Favorite Color is yellow
ReactDOM.render(<Header favcol="yellow"/>, document.getElementById('root'));
```

#### render
The **render()** method is required, and is the method that actually outputs the HTML to the DOM.
``` jsx
class Header extends React.Component {
  render() {
    return (
      <h1>This is the content of the Header component</h1>
    );
  }
}

ReactDOM.render(<Header />, document.getElementById('root'));
```

#### componentDidMount
The **componentDidMount()** method is called after the component is rendered.

This is where you run statements that requires that the component is already placed in the DOM.
``` jsx
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritecolor: "red"};
  }
  componentDidMount() {
    setTimeout(() => {
      this.setState({favoritecolor: "yellow"})
    }, 1000)
  }
  render() {
    return (
      <h1>My Favorite Color is {this.state.favoritecolor}</h1>
    );
  }
}

ReactDOM.render(<Header />, document.getElementById('root'));
// My Favorite Color is red
// after 1 second, then
// My Favorite Color is yellow
```

### Updating
The next phase in the lifecycle is when a component is updated.

A component is updated whenever there is a change in the component's **state** or **props**.

React has five built-in methods that gets called, in this order, when a component is updated:

1. **getDerivedStateFromProps()**
2. **shouldComponentUpdate()**
3. **render()**
4. **getSnapshotBeforeUpdate()**
5. **componentDidUpdate()**

The **render()** method is required and will always be called, the others are optional and will be called if you define them.

#### getDerivedStateFromProps
Also at updates the **getDerivedStateFromProps** method is called. This is the first method that is called when a component gets updated.

This is still the natural place to set the **state** object based on the initial props.

The example below has a button that changes the favorite color to blue, but since the **getDerivedStateFromProps()** method is called, which updates the state with the color from the favcol attribute, the favorite color is still rendered as yellow:
``` jsx
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritecolor: "red"};
  }
  static getDerivedStateFromProps(props, state) {
    return {favoritecolor: props.favcol };
  }
  changeColor = () => {
    this.setState({favoritecolor: "blue"});
  }
  render() {
    return (
      <div>
      <h1>My Favorite Color is {this.state.favoritecolor}</h1>
      <button type="button" onClick={this.changeColor}>Change color</button>
      </div>
    );
  }
}

ReactDOM.render(<Header favcol="yellow"/>, document.getElementById('root'));
/*
This example has a button that changes the favorite color to blue,
but since the getDerivedStateFromProps() method is called,
the favorite color is still rendered as yellow
(because the method updates the state
with the color from the favcol attribute).
*/
```

#### shouldComponentUpdate
In the **shouldComponentUpdate()** method you can return a Boolean value that specifies whether React should continue with the rendering or not.

The default value is **true**.

The example below shows what happens when the **shouldComponentUpdate()** method returns **false**:
``` jsx
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritecolor: "red"};
  }
  shouldComponentUpdate() {
    return false;
  }
  changeColor = () => {
    this.setState({favoritecolor: "blue"});
  }
  render() {
    return (
      <div>
      <h1>My Favorite Color is {this.state.favoritecolor}</h1>
      <button type="button" onClick={this.changeColor}>Change color</button>
      </div>
    );
  }
}

ReactDOM.render(<Header />, document.getElementById('root'));
```

Same example as above, but this time the **shouldComponentUpdate()** method returns **true** instead:
``` jsx
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritecolor: "red"};
  }
  shouldComponentUpdate() {
    return true;
  }
  changeColor = () => {
    this.setState({favoritecolor: "blue"});
  }
  render() {
    return (
      <div>
      <h1>My Favorite Color is {this.state.favoritecolor}</h1>
      <button type="button" onClick={this.changeColor}>Change color</button>
      </div>
    );
  }
}

ReactDOM.render(<Header />, document.getElementById('root'));
```

#### render
The **render()** method is of course called when a component gets updated, it has to re-render the HTML to the DOM, with the new changes.

The example below has a button that changes the favorite color to blue:
``` jsx
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritecolor: "red"};
  }
  changeColor = () => {
    this.setState({favoritecolor: "blue"});
  }
  render() {
    return (
      <div>
      <h1>My Favorite Color is {this.state.favoritecolor}</h1>
      <button type="button" onClick={this.changeColor}>Change color</button>
      </div>
    );
  }
}

ReactDOM.render(<Header />, document.getElementById('root'));
```

#### getSnapshotBeforeUpdate
n the **getSnapshotBeforeUpdate()** method you have access to the **props** and **state** before the update, meaning that even after the update, you can check what the values were before the update.

If the **getSnapshotBeforeUpdate()** method is present, you should also include the **componentDidUpdate()** method, otherwise you will get an error.

The example below might seem complicated, but all it does is this:

When the component is mounting it is rendered with the favorite color "red".

When the component has been mounted, a timer changes the state, and after one second, the favorite color becomes "yellow".

This action triggers the update phase, and since this component has a **getSnapshotBeforeUpdate()** method, this method is executed, and writes a message to the empty DIV1 element.

Then the **componentDidUpdate()** method is executed and writes a message in the empty DIV2 element:
``` jsx
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritecolor: "red"};
  }
  componentDidMount() {
    setTimeout(() => {
      this.setState({favoritecolor: "yellow"})
    }, 1000)
  }
  getSnapshotBeforeUpdate(prevProps, prevState) {
    document.getElementById("div1").innerHTML =
    "Before the update, the favorite was " + prevState.favoritecolor;
  }
  componentDidUpdate() {
    document.getElementById("div2").innerHTML =
    "The updated favorite is " + this.state.favoritecolor;
  }
  render() {
    return (
      <div>
        <h1>My Favorite Color is {this.state.favoritecolor}</h1>
        <div id="div1"></div>
        <div id="div2"></div>
      </div>
    );
  }
}

ReactDOM.render(<Header />, document.getElementById('root'));
```

#### componentDidUpdate
The **componentDidUpdate** method is called after the component is updated in the DOM.

The example below might seem complicated, but all it does is this:

When the component is mounting it is rendered with the favorite color "red".

When the component has been mounted, a timer changes the state, and the color becomes "yellow".

This action triggers the update phase, and since this component has a **componentDidUpdate** method, this method is executed and writes a message in the empty DIV element:
``` jsx
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritecolor: "red"};
  }
  componentDidMount() {
    setTimeout(() => {
      this.setState({favoritecolor: "yellow"})
    }, 1000)
  }
  componentDidUpdate() {
    document.getElementById("mydiv").innerHTML =
    "The updated favorite is " + this.state.favoritecolor;
  }
  render() {
    return (
      <div>
      <h1>My Favorite Color is {this.state.favoritecolor}</h1>
      <div id="mydiv"></div>
      </div>
    );
  }
}

ReactDOM.render(<Header />, document.getElementById('root'));
```

### Unmounting
The next phase in the lifecycle is when a component is removed from the DOM, or unmounting as React likes to call it.

React has only one built-in method that gets called when a component is unmounted:

1. **componentWillUnmount()**

#### componentWillUnmount
The **componentWillUnmount** method is called when the component is about to be removed from the DOM.
``` jsx
class Container extends React.Component {
  constructor(props) {
    super(props);
    this.state = {show: true};
  }
  delHeader = () => {
    this.setState({show: false});
  }
  render() {
    let myheader;
    if (this.state.show) {
      myheader = <Child />;
    };
    return (
      <div>
      {myheader}
      <button type="button" onClick={this.delHeader}>Delete Header</button>
      </div>
    );
  }
}

class Child extends React.Component {
  componentWillUnmount() {
    alert("The component named Header is about to be unmounted.");
  }
  render() {
    return (
      <h1>Hello World!</h1>
    );
  }
}

ReactDOM.render(<Container />, document.getElementById('root'));
```
