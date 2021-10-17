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

Full code: [React Classes](https://abdussametkaci.github.io/React_Tutorial/my-react-app/src/classes.html)

Reference: [w3shools](https://www.w3schools.com/react/default.asp)