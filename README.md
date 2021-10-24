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

You'll notice a single **div** in the body of this file. This is where our React application will be rendered.

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

It does NOT have to be a div element and it does NOT have to have the id='root':

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

## React Props
Props are arguments passed into React components.

Props are passed to components via HTML attributes.
```
props stands for properties.
```

React Props are like function arguments in JavaScript and attributes in HTML.

To send props into a component, use the same syntax as HTML attributes
``` jsx
const myelement = <Car brand="Ford" />;
```

The component receives the argument as a props object:
``` jsx
function Car(props) {
  return <h2>I am a { props.brand }!</h2>;
}
```

### Pass Data
Props are also how you pass data from one component to another, as parameters.

end the "brand" property from the Garage component to the Car component:
``` jsx
function Car(props) {
  return <h2>I am a { props.brand }!</h2>;
}

function Garage() {
  return (
    <>
      <h1>Who lives in my garage?</h1>
      <Car brand="Ford" />
    </>
  );
}

ReactDOM.render(<Garage />, document.getElementById('root'));
```

If you have a variable to send, and not a string as in the example above, you just put the variable name inside curly brackets:
``` jsx
function Car(props) {
  return <h2>I am a { props.brand }!</h2>;
}

function Garage() {
  const carName = "Ford";
  return (
    <>
      <h1>Who lives in my garage?</h1>
      <Car brand={ carName } />
    </>
  );
}

ReactDOM.render(<Garage />, document.getElementById('root'));
```

Or if it was an object:,
``` jsx
function Car(props) {
  return <h2>I am a { props.brand.model }!</h2>;
}

function Garage() {
  const carInfo = { name: "Ford", model: "Mustang" };
  return (
    <>
      <h1>Who lives in my garage?</h1>
      <Car brand={ carInfo } />
    </>
  );
}

ReactDOM.render(<Garage />, document.getElementById('root'));
```
```
Note: React Props are read-only! You will get an error if you try to change their value.
```

## React Events
Just like HTML DOM events, React can perform actions based on user events.

React has the same events as HTML: click, change, mouseover etc.

### Adding Events
React events are written in camelCase syntax:

**onClick** instead of **onclick**.

React event handlers are written inside curly braces:

**onClick={shoot}**  instead of **onClick="shoot()"**.
``` jsx
<button onClick={shoot}>Take the Shot!</button>
```

#### Example
``` jsx
function Football() {
  const shoot = () => {
    alert("Great Shot!");
  }

  return (
    <button onClick={shoot}>Take the shot!</button>
  );
}

ReactDOM.render(<Football />, document.getElementById('root'));
```

### Passing Arguments
To pass an argument to an event handler, use an arrow function.
``` jsx
function Football() {
  const shoot = (a) => {
    alert(a);
  }

  return (
    <button onClick={() => shoot("Goal!")}>Take the shot!</button>
  );
}

ReactDOM.render(<Football />, document.getElementById('root'));
```

### React Event Object
Event handlers have access to the React event that triggered the function.

In our example the event is the "click" event.
``` jsx
function Football() {
  const shoot = (a, b) => {
    alert(b.type);
    /*
    'b' represents the React event that triggered the function,
    in this case the 'click' event
    */
  }

  return (
    <button onClick={(event) => shoot("Goal!", event)}>Take the shot!</button>
  );
}

ReactDOM.render(<Football />, document.getElementById('root'));
```

## React Conditional Rendering
In React, you can conditionally render components.

There are several ways to do this.

### if Statement
We can use the if JavaScript operator to decide which component to render.
``` jsx
function Goal(props) {
  const isGoal = props.isGoal;
  if (isGoal) {
    return <MadeGoal/>;
  }
  return <MissedGoal/>;
}

ReactDOM.render(
  <Goal isGoal={false} />,
  document.getElementById('root')
);
```

### Logical && Operator
``` jsx
function Garage(props) {
  const cars = props.cars;
  return (
    <>
      <h1>Garage</h1>
      {cars.length > 0 &&
        <h2>
          You have {cars.length} cars in your garage.
        </h2>
      }
    </>
  );
}

const cars = ['Ford', 'BMW', 'Audi'];
ReactDOM.render(
  <Garage cars={cars} />,
  document.getElementById('root')
);
```

### Ternary Operator
``` jsx
function Goal(props) {
  const isGoal = props.isGoal;
  return (
    <>
      { isGoal ? <MadeGoal/> : <MissedGoal/> }
    </>
  );
}

ReactDOM.render(
  <Goal isGoal={false} />,
  document.getElementById('root')
);
```

## React Lists
In React, you will render lists with some type of loop.

The JavaScript **map()** array method is generally the preferred method.
``` jsx
  return <li>I am a { props.brand }</li>;
}

function Garage() {
  const cars = ['Ford', 'BMW', 'Audi'];
  return (
    <>
      <h1>Who lives in my garage?</h1>
      <ul>
        {cars.map((car) => <Car brand={car} />)}
      </ul>
    </>
  );
}

ReactDOM.render(<Garage />, document.getElementById('root'));
```

### Keys
Keys allow React to keep track of elements. This way, if an item is updated or removed, only that item will be re-rendered instead of the entire list.

Keys need to be unique to each sibling. But they can be duplicated globally.

Generally, the key should be a unique ID assigned to each item. As a last resort, you can use the array index as a key.
``` jsx
function Car(props) {
  return <li>I am a { props.brand }</li>;
}

function Garage() {
  const cars = [
    {id: 1, brand: 'Ford'},
    {id: 2, brand: 'BMW'},
    {id: 3, brand: 'Audi'}
  ];
  return (
    <>
      <h1>Who lives in my garage?</h1>
      <ul>
        {cars.map((car) => <Car key={car.id} brand={car.brand} />)}
      </ul>
    </>
  );
}

ReactDOM.render(<Garage />, document.getElementById('root'));
```

## React Forms
Just like in HTML, React uses forms to allow users to interact with the web page.

### Adding Forms in React
``` jsx
function MyForm() {
  return (
    <form>
      <label>Enter your name:
        <input type="text" />
      </label>
    </form>
  )
}

ReactDOM.render(<MyForm />, document.getElementById('root'));
```

This will work as normal, the form will submit and the page will refresh.

But this is generally not what we want to happen in React.

We want to prevent this default behavior and let React control the form.

### Handling Forms
Handling forms is about how you handle the data when it changes value or gets submitted.

In HTML, form data is usually handled by the DOM.

In React, form data is usually handled by the components.

When the data is handled by the components, all the data is stored in the component state.

You can control changes by adding event handlers in the **onChange** attribute.

We can use the **useState** Hook to keep track of each inputs value and provide a "single source of truth" for the entire application.
``` jsx
import { useState } from "react";
import ReactDOM from 'react-dom';

function MyForm() {
  const [name, setName] = useState("");

  return (
    <form>
      <label>Enter your name:
        <input
          type="text" 
          value={name}
          onChange={(e) => setName(e.target.value)}
        />
      </label>
    </form>
  )
}

ReactDOM.render(<MyForm />, document.getElementById('root'));
```

### Submitting Forms
You can control the submit action by adding an event handler in the onSubmit attribute for the form
``` jsx
import { useState } from "react";
import ReactDOM from 'react-dom';

function MyForm() {
  const [name, setName] = useState("");

  const handleSubmit = (event) => {
    event.preventDefault();
    alert('The name you entered was: ${name}')
  }

  return (
    <form onSubmit={handleSubmit}>
      <label>Enter your name:
        <input 
          type="text" 
          value={name}
          onChange={(e) => setName(e.target.value)}
        />
      </label>
      <input type="submit" />
    </form>
  )
}

ReactDOM.render(<MyForm />, document.getElementById('root'));
```

### Multiple Input Fields
You can control the values of more than one input field by adding a **name** attribute to each element.

We will initialize our state with an empty object.

To access the fields in the event handler use the **event.target.name** and **event.target.value** syntax.

To update the state, use square brackets [bracket notation] around the property name.
``` jsx
import { useState } from "react";
import ReactDOM from "react-dom";

function MyForm() {
  const [inputs, setInputs] = useState({});

  const handleChange = (event) => {
    const name = event.target.name;
    const value = event.target.value;
    setInputs(values => ({...values, [name]: value}))
  }

  const handleSubmit = (event) => {
    event.preventDefault();
    alert(inputs);
  }

  return (
    <form onSubmit={handleSubmit}>
      <label>Enter your name:
      <input 
        type="text" 
        name="username" 
        value={inputs.username || ""} 
        onChange={handleChange}
      />
      </label>
      <label>Enter your age:
        <input 
          type="number" 
          name="age" 
          value={inputs.age || ""} 
          onChange={handleChange}
        />
        </label>
        <input type="submit" />
    </form>
  )
}

ReactDOM.render(<MyForm />, document.getElementById('root'));
```

```
Note: We use the same event handler function for both input fields, we could write one event handler for each, but this gives us much cleaner code and is the preferred way in React.
```

### Textarea
The textarea element in React is slightly different from ordinary HTML.

In HTML the value of a textarea was the text between the start tag ```<textarea>``` and the end tag ```</textarea>```.
``` html
<textarea>
  Content of the textarea.
</textarea>
```

In React the value of a textarea is placed in a value attribute. We'll use the **useState** Hook to mange the value of the textarea:
``` jsx
import { useState } from "react";
import ReactDOM from "react-dom";

function MyForm() {
  const [textarea, setTextarea] = useState(
    "The content of a textarea goes in the value attribute"
  );

  const handleChange = (event) => {
    setTextarea(event.target.value)
  }

  return (
    <form>
      <textarea value={textarea} onChange={handleChange} />
    </form>
  )
}

ReactDOM.render(<MyForm />, document.getElementById('root'));
```

### Select
A drop down list, or a select box, in React is also a bit different from HTML.

in HTML, the selected value in the drop down list was defined with the **selected** attribute:
``` html
<select>
  <option value="Ford">Ford</option>
  <option value="Volvo" selected>Volvo</option>
  <option value="Fiat">Fiat</option>
</select>
```

In React, the selected value is defined with a **value** attribute on the **select** tag:
``` jsx
function MyForm() {
  const [myCar, setMyCar] = useState("Volvo");

  const handleChange = (event) => {
    setMyCar(event.target.value)
  }

  return (
    <form>
      <select value={myCar} onChange={handleChange}>
        <option value="Ford">Ford</option>
        <option value="Volvo">Volvo</option>
        <option value="Fiat">Fiat</option>
      </select>
    </form>
  )
}
```

By making these slight changes to ```<textarea>``` and ```<select>```, React is able to handle all input elements in the same way.

## React Router
Create React App doesn't include page routing.

React Router is the most popular solution.

### Add React Router
To add React Router in your application, run this in the terminal from the root directory of the application:
```
npm i -D react-router-dom
```

### Folder Structure
To create an application with multiple page routes, let's first start with the file structure.

Within the **src** folder, we'll create a folder named **pages** with several files:

src\pages\:

1. **Home.js**
2. **Blogs.js**
3. **Contact.js**

Each file will contain a very basic React component:
``` jsx
// Home.js
const Home = () => {
  return <h1>Home</h1>;
};

export default Home;

```

``` jsx
// Blogs.js
const Blogs = () => {
  return <h1>Blog Articles</h1>;
};

export default Blogs;
```

``` jsx
// Contact.js
const Contact = () => {
  return <h1>Contact Me</h1>;
};

export default Contact;
```

### Basic Usage
Now we will use our Router in our **index.js** file.
``` jsx
import ReactDOM from "react-dom";
import { BrowserRouter as Router, Switch, Route, Link } from "react-router-dom";
import Home from "./pages/Home";
import Blogs from "./pages/Blogs";
import Contact from "./pages/Contact";

export default function App() {
  return (
    <Router>
      <div>
        <Link to="/">Home</Link>
      </div>
      <div>
        <Link to="/blogs">Blog Articles</Link>
      </div>
      <div>
        <Link to="/contact">Contact Me</Link>
      </div>

      <hr />

      <Switch>
        <Route exact path="/">
          <Home />
        </Route>
        <Route path="/blogs">
          <Blogs />
        </Route>
        <Route path="/contact">
          <Contact />
        </Route>
      </Switch>
    </Router>
  );
}

ReactDOM.render(<App />, document.getElementById("root"));
```

### Example Explained
We wrap our content first with ```<Router>```.

```<Link>``` is used to set the URL and keep track of browsing history.

Anytime we link to an internal path, we will use ```<Link>``` instead of ```<a href="">```.

```<Switch>``` is similar to a JavaScript switch statement. It will conditionally render the ```<Route>``` that matches the ```<Link>``` path.

## React Memo
Using **memo** will cause React to skip rendering a component if its props have not changed.

This can improve performance.

### Problem
In this example, the **Todos** component re-renders even when the todos have not changed
``` jsx
// index.js
import { useState } from "react";
import ReactDOM from "react-dom";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState(["todo 1", "todo 2"]);

  const increment = () => {
    setCount((c) => c + 1);
  };

  return (
    <>
      <Todos todos={todos} />
      <hr />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};

ReactDOM.render(<App />, document.getElementById('root'));
```

``` jsx
// Todos.js
const Todos = ({ todos }) => {
  console.log("child render");
  return (
    <>
      <h2>My Todos</h2>
      {todos.map((todo, index) => {
        return <p key={index}>{todo}</p>;
      })}
    </>
  );
};

export default Todos;
```

When you click the increment button, the **Todos** component re-renders.

If this component was complex, it could cause performance issues.

### Solution
To fix this, we can use **memo**.

Use **memo** to keep the **Todos** component from needlessly re-rendering.

Wrap the **Todos** component export in **memo**:
``` jsx
// index.js
import { useState } from "react";
import ReactDOM from "react-dom";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState(["todo 1", "todo 2"]);

  const increment = () => {
    setCount((c) => c + 1);
  };

  return (
    <>
      <Todos todos={todos} />
      <hr />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};

ReactDOM.render(<App />, document.getElementById('root'));
```

``` jsx
// Todos.js
import { memo } from "react";

const Todos = ({ todos }) => {
  console.log("child render");
  return (
    <>
      <h2>My Todos</h2>
      {todos.map((todo, index) => {
        return <p key={index}>{todo}</p>;
      })}
    </>
  );
};

export default memo(Todos);
```

Now the **Todos** component only re-renders when the **todos** that are passed to it through props are updated.

## Styling React Using CSS
There are many ways to style React with CSS, this tutorial will take a closer look at three common ways:

1. Inline styling
2. CSS stylesheets
3. CSS Modules

### Inline Styling
To style an element with the inline style attribute, the value must be a JavaScript object:
``` jsx
const Header = () => {
  return (
    <>
      <h1 style={{color: "red"}}>Hello Style!</h1>
      <p>Add a little style!</p>
    </>
  );
}
```

```
Note: In JSX, JavaScript expressions are written inside curly braces, and 
since JavaScript objects also use curly braces, the styling in the example
above is written inside two sets of curly braces {{}}.
```

#### camelCased Property Names
Since the inline CSS is written in a JavaScript object, properties with hyphen separators, like **background-color**, must be written with camel case syntax:
``` jsx
const Header = () => {
  return (
    <>
      <h1 style={{backgroundColor: "lightblue"}}>Hello Style!</h1>
      <p>Add a little style!</p>
    </>
  );
}
```

#### JavaScript Object
You can also create an object with styling information, and refer to it in the style attribute:
``` jsx
const Header = () => {
  const myStyle = {
    color: "white",
    backgroundColor: "DodgerBlue",
    padding: "10px",
    fontFamily: "Sans-Serif"
  };
  return (
    <>
      <h1 style={myStyle}>Hello Style!</h1>
      <p>Add a little style!</p>
    </>
  );
}
```

### CSS Stylesheet
You can write your CSS styling in a separate file, just save the file with the .css file extension, and import it in your application.

Create a new file called "App.css" and insert some CSS code in it:
``` css
body {
  background-color: #282c34;
  color: white;
  padding: 40px;
  font-family: Sans-Serif;
  text-align: center;
}
```

**Note**: You can call the file whatever you like, just remember the correct file extension.

Import the stylesheet in your application:
``` jsx
import React from 'react';
import ReactDOM from 'react-dom';
import './App.css';

const Header = () => {
  return (
    <>
      <h1>Hello Style!</h1>
      <p>Add a little style!.</p>
    </>
  );
}

ReactDOM.render(<Header />, document.getElementById('root'));
```

### CSS Modules
Another way of adding styles to your application is to use CSS Modules.

CSS Modules are convenient for components that are placed in separate files.

**Note**: The CSS inside a module is available only for the component that imported it, and you do not have to worry about name conflicts.

Create the CSS module with the **.module.css** extension, example: **my-style.module.css**.
``` css
/*my-style.module.css*/
.bigblue {
  color: DodgerBlue;
  padding: 40px;
  font-family: Sans-Serif;
  text-align: center;
}
```

``` jsx
// Car.js
import styles from './my-style.module.css'; 

const Car = () => {
  return <h1 className={styles.bigblue}>Hello Car!</h1>;
}

export default Car;
```

Import the component in your application:
``` jsx
// index.js
import ReactDOM from 'react-dom';
import Car from './Car.js';

ReactDOM.render(<Car />, document.getElementById('root'));
```

## Styling React Using Sass
### What is Sass
Sass is a CSS pre-processor.

Sass files are executed on the server and sends CSS to the browser.

Learn More: [Sass Tutorial](https://www.w3schools.com/sass/default.php)

### Can I use Sass?
If you use the **create-react-app** in your project, you can easily install and use Sass in your React projects.

Install Sass by running this command in your terminal:
```
npm i sass
```

Now you are ready to include Sass files in your project!

### Create a Sass file
Create a Sass file the same way as you create CSS files, but Sass files have the file extension **.scss**

In Sass files you can use variables and other Sass functions:

Create a variable to define the color of the text:

my-sass.scss:
``` scss
$myColor: red;

h1 {
  color: $myColor;
}
```

Import the Sass file the same way as you imported a CSS file:
``` jsx
import React from 'react';
import ReactDOM from 'react-dom';
import './my-sass.scss';

const Header = () => {
  return (
    <>
      <h1>Hello Style!</h1>
      <p>Add a little style!.</p>
    </>
  );
}

ReactDOM.render(<Header />, document.getElementById('root'));
```

## React Hooks
Hooks were added to React in version 16.8.

Hooks allow function components to have access to state and other React features. Because of this, class components are generally no longer needed.

**Note**: Although Hooks generally replace class components, there are no plans to remove classes from React.

### What is a Hook?
Hooks allow us to "hook" into React features such as state and lifecycle methods.

Example:
``` jsx
import React, { useState } from "react";
import ReactDOM from "react-dom";

function FavoriteColor() {
  const [color, setColor] = useState("red");

  return (
    <>
      <h1>My favorite color is {color}!</h1>
      <button
        type="button"
        onClick={() => setColor("blue")}
      >Blue</button>
      <button
        type="button"
        onClick={() => setColor("red")}
      >Red</button>
      <button
        type="button"
        onClick={() => setColor("pink")}
      >Pink</button>
      <button
        type="button"
        onClick={() => setColor("green")}
      >Green</button>
    </>
  );
}

ReactDOM.render(<FavoriteColor />, document.getElementById('root'));
```

You must **import** Hooks from **react**.

Here we are using the **useState** Hook to keep track of the application state.

State generally refers to application data or properties that need to be tracked.

### Hook Rules
There are 3 rules for hooks:

1. Hooks can only be called inside React function components.
2. Hooks can only be called at the top level of a component.
3. Hooks cannot be conditional

**Note**: Hooks will not work in React class components.

## React useState Hook
The React **useState** Hook allows us to track state in a function component.

State generally refers to data or properites that need to be tracking in an application.

### Import useState
To use the **useState Hook**, we first need to **import** it into our component.
``` jsx
import { useState } from "react";
```

### Initialize useState
We initialize our state by calling **useState** in our function component.

**useState** accepts an initial state and returns two values:

1. The current state.
2. A function that updates the state.

``` jsx
import { useState } from "react";

function FavoriteColor() {
  const [color, setColor] = useState("");
}
```

The first value, **color**, is our current state.

The second value, **setColor**, is the function that is used to update our state.

These names are variables that can be named anything you would like.

Lastly, we set the initial state to an empty string: **useState("")**

### Read State
We can now include our state anywhere in our component.
``` jsx
import { useState } from "react";
import ReactDOM from "react-dom";

function FavoriteColor() {
  const [color, setColor] = useState("red");

  return <h1>My favorite color is {color}!</h1>
}

ReactDOM.render(<FavoriteColor />, document.getElementById('root'));
```

### Update State
To update our state, we use our state updater function.

**Note**: We should never directly update state. Ex: **color = "red"** is not allowed.
``` jsx
import { useState } from "react";
import ReactDOM from "react-dom";

function FavoriteColor() {
  const [color, setColor] = useState("red");

  return (
    <>
      <h1>My favorite color is {color}!</h1>
      <button
        type="button"
        onClick={() => setColor("blue")}
      >Blue</button>
    </>
  )
}

ReactDOM.render(<FavoriteColor />, document.getElementById('root'));
```

### What Can State Hold
The **useState** Hook can be used to keep track of strings, numbers, booleans, arrays, objects, and any combination of these!

We could create multiple state Hooks to track individual values.
``` jsx
import { useState } from "react";
import ReactDOM from "react-dom";

function Car() {
  const [brand, setBrand] = useState("Ford");
  const [model, setModel] = useState("Mustang");
  const [year, setYear] = useState("1964");
  const [color, setColor] = useState("red");

  return (
    <>
      <h1>My {brand}</h1>
      <p>
        It is a {color} {model} from {year}.
      </p>
    </>
  )
}

ReactDOM.render(<Car />, document.getElementById('root'));
```

Or, we can just use one state and include an object instead!
``` jsx
import { useState } from "react";
import ReactDOM from "react-dom";

function Car() {
  const [car, setCar] = useState({
    brand: "Ford",
    model: "Mustang",
    year: "1964",
    color: "red"
  });

  return (
    <>
      <h1>My {car.brand}</h1>
      <p>
        It is a {car.color} {car.model} from {car.year}.
      </p>
    </>
  )
}

ReactDOM.render(<Car />, document.getElementById('root'));
```

**Note**: Since we are now tracking a single object, we need to reference that object and then the property of that object when rendering the component. (Ex: car.brand)

### Updating Objects and Arrays in State
When state is updated, the entire state gets overwritten.

What if we only want to update the color of our car?

If we only called **setCar({color: "blue"})**, this would remove the brand, model, and year from our state.

We can use the JavaScript spread operator to help us.
``` jsx
import { useState } from "react";
import ReactDOM from "react-dom";

function Car() {
  const [car, setCar] = useState({
    brand: "Ford",
    model: "Mustang",
    year: "1964",
    color: "red"
  });

  const updateColor = () => {
    setCar(previousState => {
      return { ...previousState, color: "blue" }
    });
  }

  return (
    <>
      <h1>My {car.brand}</h1>
      <p>
        It is a {car.color} {car.model} from {car.year}.
      </p>
      <button
        type="button"
        onClick={updateColor}
      >Blue</button>
    </>
  )
}

ReactDOM.render(<Car />, document.getElementById('root'));
```

Because we need the current value of state, we pass a function into our **setCar** function. This function receives the previous value.

We then return an object, spreading the **previousState** and overwriting only the color.

## React useEffect Hooks
The **useEffect** Hook allows you to perform side effects in your components.

Some examples of side effects are: fetching data, directly updating the DOM, and timers.

**useEffect** accepts two arguments. The second argument is optional.

**useEffect(<function>, <dependency>)**

Let's use a timer as an example.
``` jsx
import { useState, useEffect } from "react";
import ReactDOM from "react-dom";

function Timer() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    setTimeout(() => {
      setCount((count) => count + 1);
    }, 1000);
  });

  return <h1>I've rendered {count} times!</h1>;
}

ReactDOM.render(<Timer />, document.getElementById('root'));
```

But wait!! I keep counting even though it should only count once!

**useEffect** runs on every render. That means that when the count changes, a render happens, which then triggers another effect.

This is not what we want. There are several ways to control when side effects run.

We should always include the second parameter which accepts an array. We can optionally pass dependencies to **useEffect** in this array.

#### 1. No dependency passed:
``` jsx
useEffect(() => {
    //Runs on every render
  });
```

#### 2. An empty array:
``` jsx
useEffect(() => {
    //Runs only on the first render
  }, []);
```

#### 3. Props or state values:
``` jsx
useEffect(() => {
    //Runs on the first render
    //And any time any dependency value changes
  }, [prop, state]);
```

Only run the effect on the initial render:
``` jsx
import { useState, useEffect } from "react";
import ReactDOM from "react-dom";

function Timer() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    setTimeout(() => {
      setCount((count) => count + 1);
    }, 1000);
  } []); // <- add empty brackets here

  return <h1>I've rendered {count} times!</h1>;
}

ReactDOM.render(<Timer />, document.getElementById('root'));
```

Here is an example of a **useEffect** Hook that is dependent on a variable. If the **count** variable updates, the effect will run again:
``` jsx
import { useState, useEffect } from "react";
import ReactDOM from "react-dom";

function Counter() {
  const [count, setCount] = useState(0);
  const [calculation, setCalculation] = useState(0);

  useEffect(() => {
    setCalculation(() => count * 2);
  }, [count]); // <- add the count variable here

  return (
    <>
      <p>Count: {count}</p>
      <button onClick={() => setCount((c) => c + 1)}>+</button>
      <p>Calculation: {calculation}</p>
    </>
  );
}

ReactDOM.render(<Counter />, document.getElementById('root'));
```

If there are multiple dependencies, they should be included in the useEffect dependency array.

### Effect Cleanup
Some effects require cleanup to reduce memory leaks.

Timeouts, subscriptions, event listeners, and other effects that are no longer needed should be disposed.

We do this by including a return function at the end of the **useEffect** Hook.
``` jsx
import { useState, useEffect } from "react";
import ReactDOM from "react-dom";

function Timer() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    let timer = setTimeout(() => {
    setCount((count) => count + 1);
  }, 1000);

  return () => clearTimeout(timer)
  }, []);

  return <h1>I've rendered {count} times!</h1>;
}

ReactDOM.render(<Timer />, document.getElementById("root"));
```

**Note**: To clear the timer, we had to name it

## React useContext Hook
### React Context
React Context is a way to manage state globally.

It can be used together with the **useState** Hook to share state between deeply nested components more easily than with **useState** alone.

### The Problem
State should be held by the highest parent component in the stack that requires access to the state.

To illustrate, we have many nested components. The component at the top and bottom of the stack need access to the state.

To do this without Context, we will need to pass the state as "props" through each nested component. This is called "prop drilling".

Example:

Passing "props" through nested components:
``` jsx
import { useState } from "react";
import ReactDOM from "react-dom";

function Component1() {
  const [user, setUser] = useState("Jesse Hall");

  return (
    <>
      <h1>{`Hello ${user}!`}</h1>
      <Component2 user={user} />
    </>
  );
}

function Component2({ user }) {
  return (
    <>
      <h1>Component 2</h1>
      <Component3 user={user} />
    </>
  );
}

function Component3({ user }) {
  return (
    <>
      <h1>Component 3</h1>
      <Component4 user={user} />
    </>
  );
}

function Component4({ user }) {
  return (
    <>
      <h1>Component 4</h1>
      <Component5 user={user} />
    </>
  );
}

function Component5({ user }) {
  return (
    <>
      <h1>Component 5</h1>
      <h2>{`Hello ${user} again!`}</h2>
    </>
  );
}

ReactDOM.render(<Component1 />, document.getElementById("root"));
```

Even though components 2-4 did not need the state, they had to pass the state along so that it could reach component 5.

### The Solution
The solution is to create context.

#### Create Context
To create context, you must Import **createContext** and initialize it:
``` jsx
import { useState, createContext } from "react";
import ReactDOM from "react-dom";

const UserContext = createContext()
```

Next we'll use the Context Provider to wrap the tree of components that need the state Context.

#### Context Provider
Wrap child components in the Context Provider and supply the state value.
``` jsx
function Component1() {
  const [user, setUser] = useState("Jesse Hall");

  return (
    <UserContext.Provider value={user}>
      <h1>{`Hello ${user}!`}</h1>
      <Component2 user={user} />
    </UserContext.Provider>
  );
}
```

Now, all components in this tree will have access to the user Context.

#### Use the useContext Hook
In order to use the Context in a child component, we need to access it using the **useContext** Hook.

First, include the **useContext** in the import statement:
``` jsx
import { useState, createContext, useContext } from "react";
```

Then you can access the user Context in all components:
``` jsx
function Component5() {
  const user = useContext(UserContext);

  return (
    <>
      <h1>Component 5</h1>
      <h2>{`Hello ${user} again!`}</h2>
    </>
  );
}
```

### Full Example
``` jsx
import { useState, createContext, useContext } from "react";
import ReactDOM from "react-dom";

const UserContext = createContext();

function Component1() {
  const [user, setUser] = useState("Jesse Hall");

  return (
    <UserContext.Provider value={user}>
      <h1>{`Hello ${user}!`}</h1>
      <Component2 user={user} />
    </UserContext.Provider>
  );
}

function Component2() {
  return (
    <>
      <h1>Component 2</h1>
      <Component3 />
    </>
  );
}

function Component3() {
  return (
    <>
      <h1>Component 3</h1>
      <Component4 />
    </>
  );
}

function Component4() {
  return (
    <>
      <h1>Component 4</h1>
      <Component5 />
    </>
  );
}

function Component5() {
  const user = useContext(UserContext);

  return (
    <>
      <h1>Component 5</h1>
      <h2>{`Hello ${user} again!`}</h2>
    </>
  );
}

ReactDOM.render(<Component1 />, document.getElementById("root"));
```

## React useRef Hook
The **useRef** Hook allows you to persist values between renders.

It can be used to store a mutable value that does not cause a re-render when updated.

It can be used to access a DOM element directly.

### Does Not Cause Re-renders
If we tried to count how many times our application renders using the **useState** Hook, we would be caught in an infinite loop since this Hook itself causes a re-render.

To avoid this, we can use the **useRef** Hook.
``` jsx
import { useState, useEffect, useRef } from "react";
import ReactDOM from "react-dom";

function App() {
  const [inputValue, setInputValue] = useState("");
  const count = useRef(0);

  useEffect(() => {
    count.current = count.current + 1;
  });

  return (
    <>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
      />
      <h1>Render Count: {count.current}</h1>
    </>
  );
}

ReactDOM.render(<App />, document.getElementById('root'));
```

**useRef()** only returns one item. It returns an Object called **current**.

When we initialize useRef we set the initial value: **useRef(0)**.

It's like doing this: **const count = {current: 0}**. We can access the count by using **count.current**.

Run this on your computer and try typing in the input to see the application render count increase.

### Accessing DOM Elements
In general, we want to let React handle all DOM manipulation.

But there are some instances where **useRef** can be used without causing issues.

In React, we can add a **ref** attribute to an element to access it directly in the DOM.
``` jsx
import { useRef } from "react";
import ReactDOM from "react-dom";

function App() {
  const inputElement = useRef();

  const focusInput = () => {
    inputElement.current.focus();
  };

  return (
    <>
      <input type="text" ref={inputElement} />
      <button onClick={focusInput}>Focus Input</button>
    </>
  );
}

ReactDOM.render(<App />, document.getElementById('root'));
```

### Tracking State Changes
The **useRef** Hook can also be used to keep track of previous state values.

This is because we are able to persist **useRef** values between renders.
``` jsx
import { useState, useEffect, useRef } from "react";
import ReactDOM from "react-dom";

function App() {
  const [inputValue, setInputValue] = useState("");
  const previousInputValue = useRef("");

  useEffect(() => {
    previousInputValue.current = inputValue;
  }, [inputValue]);

  return (
    <>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
      />
      <h2>Current Value: {inputValue}</h2>
      <h2>Previous Value: {previousInputValue.current}</h2>
    </>
  );
}

ReactDOM.render(<App />, document.getElementById('root'));
```

This time we use a combination of useState, useEffect, and useRef to keep track of the previous state.

In the useEffect, we are updating the useRef current value each time the inputValue is updated by entering text into the input field.

## React useReducer Hook
The **useReducer** Hook is similar to the **useState** Hook.

It allows for custom state logic.

If you find yourself keeping track of multiple pieces of state that rely on complex logic, **useReducer** may be useful.

### Syntax
The useReducer Hook accepts two arguments.

**useReducer(<reducer>, <initialState>)**

The **reducer** function contains your custom state logic and the **initialState** can be a simple value but generally will contain an object.

The useReducer Hook returns the current **state** and a **dispatch** method.

Here is an example of **useReducer** in a counter app:
``` jsx
import { useReducer } from "react";
import ReactDOM from "react-dom";

const initialTodos = [
  {
    id: 1,
    title: "Todo 1",
    complete: false,
  },
  {
    id: 2,
    title: "Todo 2",
    complete: false,
  },
];

const reducer = (state, action) => {
  switch (action.type) {
    case "COMPLETE":
      return state.map((todo) => {
        if (todo.id === action.id) {
          return { ...todo, complete: !todo.complete };
        } else {
          return todo;
        }
      });
    default:
      return state;
  }
};

function Todos() {
  const [todos, dispatch] = useReducer(reducer, initialTodos);

  const handleComplete = (todo) => {
    dispatch({ type: "COMPLETE", id: todo.id });
  };

  return (
    <>
      {todos.map((todo) => (
        <div key={todo.id}>
          <label>
            <input
              type="checkbox"
              checked={todo.complete}
              onChange={() => handleComplete(todo)}
            />
            {todo.title}
          </label>
        </div>
      ))}
    </>
  );
}

ReactDOM.render(<Todos />, document.getElementById('root'));
```

This is just the logic to keep track of the todo complete status.

All of the logic to add, delete, and complete a todo could be contained within a single **useReducer** Hook by adding more actions.

## React useCallback Hook
The React **useCallback** Hook returns a memoized callback function.

Think of memoization as caching a value so that it does not need to be recalculated.

This allows us to isolate resource intensive functions so that they will not automatically run on every render.

The **useCallback** Hook only runs when one of its dependencies update.

This can improve performance.

The **useCallback** and **useMemo** Hooks are similar. The main difference is that useMemo returns a memoized value and useCallback returns a memoized function.

### Problem
One reason to use **useCallback** is to prevent a component from re-rendering unless its props have changed.

In this example, you might think that the **Todos** component will not re-render unless the **todos** change:
``` jsx
// index.js
import { useState } from "react";
import ReactDOM from "react-dom";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState([]);

  const increment = () => {
    setCount((c) => c + 1);
  };
  const addTodo = () => {
    setTodos((t) => [...t, "New Todo"]);
  };

  return (
    <>
      <Todos todos={todos} addTodo={addTodo} />
      <hr />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};

ReactDOM.render(<App />, document.getElementById('root'));
```

``` jsx
// Todos.js
import { memo } from "react";

const Todos = ({ todos, addTodo }) => {
  console.log("child render");
  return (
    <>
      <h2>My Todos</h2>
      {todos.map((todo, index) => {
        return <p key={index}>{todo}</p>;
      })}
      <button onClick={addTodo}>Add Todo</button>
    </>
  );
};

export default memo(Todos);
```

Try running this and click the count increment button.

You will notice that the **Todos** component re-renders even when the **todos** do not change.

Why does this not work? We are using **memo**, so the Todos component should not re-render since neither the todos state nor the **addTodo** function are changing when the count is incremented.

This is because of something called "referential equality".

Every time a component re-renders, its functions get recreated. Because of this, the **addTodo** function has actually changed.

### Solution
To fix this, we can use the **useCallback** hook to prevent the function from being recreated unless necessary.

Use the **useCallback** Hook to prevent the Todos component from re-rendering needlessly:
``` jsx
import { useState, useCallback } from "react";
import ReactDOM from "react-dom";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState([]);

  const increment = () => {
    setCount((c) => c + 1);
  };
  const addTodo = useCallback(() => {
    setTodos((t) => [...t, "New Todo"]);
  }, [todos]);

  return (
    <>
      <Todos todos={todos} addTodo={addTodo} />
      <hr />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};

ReactDOM.render(<App />, document.getElementById('root'));
```

Now the **Todos** component will only re-render when the **todos** prop changes.
