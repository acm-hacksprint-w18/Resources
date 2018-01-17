# Hack Sprint - Guide to Swift

## Constants and Variables

Constants and variables associate a **name** with a **value** of a particular type.

The value of a **constant** cannot be changed once it is set, whereas a **variable** can be set to a different value in the future.

We use the `let` keyword to declare a constant, and the `var` keyword to declare a variable.

```
let maximumLoginAttempts = 10
var currentNumberOfAttempts = 0
```

### Type Inference

Swift doesn’t need you to declare the type name… it can tell what a variable’s type is based on the value you assign it!

```
var x = 5            // x is of type Int!
var y = 3.8          // y is of type Double!
var s = "UCLA"       // s is of type String!
var b = false        // b is of type Bool!
```

### Type Annotations

You can provide a type annotation when you declare a constant or variable, to be clear about the kind of values the constant or variable can store.

```
var i: Int
var d: Double
var c: Character = "C"
```

### Uninitialized Variables

In Swift, you cannot use uninitialized data: you must assign a value to a variable before using it.

```
// BAD:
var num: Int
var tripleNum = num * 3	// Error! num has not been given a value.

// GOOD:
var num: Int = 5
var tripleNum = num * 3	// tripleNum now holds the value 15.
```

## If Statements

The **if statement** has a condition. It executes a certain set of statements if that condition is true, and can execute others if it is not true.

```
let hunger = some integer value...

if hunger < 20 {
    print("I can deal with Bplate portions.")
}
else if hunger >= 20 {
    print("I need De Neve Late Night Chicken Tenders.")
}
else {
    // Never triggered...
    print("Let’s go to Feast.")
}
```

## Functions

**Functions** are self-contained chunks of code that perform a specific task. You give a function a name that identifies what it does, and this name is used to “call” the function to perform its task when needed.

A function takes inputs (called **parameters**) and returns some output.

### Declaring a Function

```
func squareNum(n: Int) -> Int {
    return n * n
}
```

- "**squareNum** is a function that takes in an integer (named **n**) and returns an integer."

### Calling a Function

```
let num = squareNum(n: 5)
```

- **num** now contains the value 25.

### No Parameters/Return Type

Functions don't have to have parameters or a return type:

```
func printHelloWorld() {
    print("Hello, world!")
}
```

## Classes

Sometimes we want to group together multiple related pieces of data and store them in a single variable.

**Classes** are general-purpose, flexible constructs that become the building blocks of your program’s code. 

You add functionality to your classes and structures by adding **properties** (variables) and **methods** (functions).

### Declaring a Class

```
class Flatulan {
    
    /* Properties */
    
    var x: Int
    var y: Int
    
    /* Methods */
    
    func moveRight() {
        x += 1
    }
    
    func fart() {
        print("Farted at position \(x), \(y)")
    }
    
}
```

- The **Flatulan** class has two properties:
  - `x`, an integer.
  - `y`, and integer.
- It also has two methods:
  - `moveRight()`, which increments its `x` property by 1.
  - `fart()`, which prints out a statement.

### Initializers

The class declaration of Flatulan above is actually incomplete. If your class has any **uninitialized** properties (variables), you must declare an **initializer** that will assign values to these uninitialized properties when you create an instance of that class.

An initializer is the exact same thing as a **constructor** in C++.

We declare an initializer with the `init` keyword:

```
init(initialX: Int, initialY: Int) {
	x = initialX
	y = initialY
}
```

- This initializer takes in two parameters:
  - `initialX`, which will be the initial value for the `x` property.
  - `initialY`, which will be the initial value for the `y` property.

### Creating a Class Instance

We can create an instance of our **Flatulan** class as follows:

```
let myFlatulan = Flatulan(initialX: 0, initialY: 0)
```

And use it like this:

```
myFlatulan.moveRight()
myFlatulan.fart()
```

