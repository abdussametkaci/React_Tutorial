# React_Tutorial
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

Reference: [w3shools](https://www.w3schools.com/react/default.asp)

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