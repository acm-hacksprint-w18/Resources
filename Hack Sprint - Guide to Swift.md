# Hack Sprint - Guide to Swift

## Table of Contents

- <a href="#1">Constants and Variables</a>
  - <a href="#2">Type Inference</a>
  - <a href="#3">Type Annotations</a>
  - <a href="#4">Uninitialized Variables</a>
- <a href="#5">Print Statements</a>
- <a href="#6">Collections</a>
  - <a href="#7">Arrays</a>
    - <a href="#8">Declaration</a>
    - <a href="#9">Initialization</a>
    - <a href="#10">Adding/Deleting Items</a>
    - <a href="#11">Accessing/Modifying Elements</a>
  - <a href="#12">Dictionaries</a>
    - <a href="#13">Declaration</a>
    - <a href="#14">Initialization</a>
    - <a href="#15">Adding/Deleting Items</a>
    - <a href="#16">Accessing/Modifying Elements</a>
- <a href="#17">If Statements</a>
- <a href="#18">For-In Loops</a>
- <a href="#19">Functions</a>
  - <a href="#20">Declaring a Function</a>
  - <a href="#21">Calling a Function</a>
  - <a href="#22">No Parameters/Return Type</a>
- <a href="#23">Classes</a>
  - <a href="24">Declaring a Class</a>
  - <a href="#25">Initializers</a>
  - <a href="#26">Creating a Class Instance</a>

---

## <a id="1">Constants and Variables</a>

Constants and variables associate a **name** with a **value** of a particular type.

The value of a **constant** cannot be changed once it is set, whereas a **variable** can be set to a different value in the future.

We use the `let` keyword to declare a constant, and the `var` keyword to declare a variable.

```
let maximumLoginAttempts = 10
var currentNumberOfAttempts = 0
```

### <a id="2">Type Inference</a>

Swift doesn’t need you to declare the type name… it can tell what a variable’s type is based on the value you assign it!

```
var x = 5            // x is of type Int!
var y = 3.8          // y is of type Double!
var s = "UCLA"       // s is of type String!
var b = false        // b is of type Bool!
```

### <a id="3">Type Annotations</a>

You can provide a type annotation when you declare a constant or variable, to be clear about the kind of values the constant or variable can store.

```
var i: Int
var d: Double
var c: Character = "C"
```

### <a id="4">Uninitialized Variables</a>

In Swift, you cannot use uninitialized data: you must assign a value to a variable before using it.

```
// BAD:
var num: Int
var tripleNum = num * 3	// Error! num has not been given a value.

// GOOD:
var num: Int = 5
var tripleNum = num * 3	// tripleNum now holds the value 15.
```

---

## <a id="5">Print Statements</a>

Swift has a built-in global function `print()`.

By default, it terminates the line it prints with a line break (\n). 

To print a value without a line break after it, pass an empty string as the terminator—for example, `print(someValue, terminator: "")`

```
var x = 6
var y = "foobar"				// This code prints:
print("Hello World!")			// Hello World!
print(y)						// foobar
print("I have \(x) dogs.")	// I have 6 dogs.
```

---

## <a id="6">Collections</a>

![CollectionTypes_intro_2x.png](https://lh6.googleusercontent.com/4KBpjQDoDJpmd6WwH9ThMkS7YF4ohUOznHt6y4dWhRID2l62beS-4Yu2hOlDcy8UFZGVRL4EyHsX_NTGsJb7FGFazps-sB6ObQkPri1OESPwvxBvl7RgSzAsHEmpc7IUEPGmqiRsF_o)

### <a id="7">Arrays</a>

An array stores values of the same type in an ordered list. 

The same value can appear in an array multiple times at different positions.

Arrays in Swift are **0-indexed**, meaning the first object is at position 0, the second object is at position 1, etc. (like in C++)

#### <a id="8">Declaration</a>

There are two ways to declare an array. There is no difference between them except their appearance; they do the exact same thing. 

**Note:** The following statements only **declare** an array; they do not **initialize** them. You must initialize your array before you can use it.

```
var a: Array<Int>		// Declare an array of Integers
var b: [String]			// Declare an array of Strings
```

#### <a id="9">Initialization</a>

Use `()` to initialize an empty array.

```
var arrayOfInts = Array<Int>()	// Empty array of Integers
var arrayOfBools = [Bool]()
```

Use `[item1, item2, ...]` to initialize an array with values item1, item2, ...

```
var arrayOfStrings = ["eggs", "milk"]
// arrayOfStrings is now ["eggs", "milk"]
```

Use `Array(repeating:count:)` to initialize an array with a value repeated `count` times.

```
var arrayOfDoubles = Array(repeating: 2.5, count: 3)
// arrayOfDoubles is now [2.5, 2.5, 2.5]
```

#### <a id="10">Adding/Deleting Items</a>

Here are some ways you can add/delete items in an array:

```
var arrayOfNumbers = [1, 2, 3, 4, 5]

arrayOfNumbers.append(10)			// [1, 2, 3, 4, 5, 10]
arrayOfNumbers.insert(20, at: 2)	// [1, 2, 20, 3, 4, 5, 10]
arrayOfNumbers += [30, 40]	// [1, 2, 20, 3, 4, 5, 10, 30, 40]

arrayOfNumbers.popLast()		// [1, 2, 20, 3, 4, 5, 10, 30]
arrayOfNumbers.remove(at: 0)	// [2, 20, 3, 4, 5, 100, 30]
```

#### <a id="11">Accessing/Modifying Elements</a>

Here are some ways you can access/modify elements in an array:

```
var arrayOfNumbers = [1, 2, 3, 4, 5]

print(arrayOfNumbers[3])		// will print "4"
arrayOfNumbers[0] = 10			// array is now [10, 2, 3, 4, 5]
arrayOfNumbers[2...4] = [7, 7] 	// array is now [10, 2, 7, 7]

arrayOfNumbers.isEmpty			// returns false
arrayOfNumbers.count			// returns 4
arrayOfNumbers.index(of: 7)		// returns 2
```

### <a id="12">Dictionaries</a>

A dictionary stores associations between keys of the same type and values of the same type in a collection with no defined ordering. 

Each value is associated with a unique key, which acts as an identifier for that value within the dictionary.

#### <a id="13">Declaration</a>

There are two ways to declare a dictionary. There is no difference between them except their appearance; they do the exact same thing. 

**Note:** The following statements only **declare** a dictionary; they do not **initialize** them. You must initialize your dictionary before you can use it.

```
Dictionary<Int, String>		// Dictionary of Int -> String
[String : Bool]				// Dictionary of String -> Bool
```

#### <a id="14">Initialization</a>

Use `()` to initialize an empty dictionary.

```
var intToString = Dictionary<Int, String>()
var intToBool = [Int : Bool]()
```

Use `[item1, item2, ...]` to specify initial values for the dictionary.

```
var groceryCosts = ["eggs" : 4.20, "milk" : 3.99]
```

#### <a id="15">Adding/Deleting Items</a>

```
var airports: [String : String]()	// Empty dictionary

airports["LAX"] = "LA Intl"			// Add "LAX" -> "LA Intl"
airports.updateValue("NY Intl", forKey: "JFK")	// Add "JFK" -> "NY Intl"

airports["JFK"] = nil				// key "JFK" has been removed
airports.removeValue(forKey: "LAX")	// key "LAX" has been removed
```

#### <a id="16">Accessing/Modifying Elements</a>

```
var airports = ["LAX" : "LA Intl", "JFK" : "NY Intl", "YYZ" : "Toronto Pearson"]

print(airports["JFK"])				// will print "NY Intl"
airports["JFK"] = "New York Intl"	// updated value at key "JFK"
airports.updateValue("Los Angeles Intl", forKey: "LAX") 		
									// updated value at key "LAX"
arrayOfNumbers.isEmpty				// returns false
arrayOfNumbers.count				// returns 3
```

---

## <a id="17">If Statements</a>

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

---

## <a id="18">For-In Loops</a>

You use the for-in loop to iterate over a sequence, such as items in an array, ranges of numbers, or characters in a string.

Here's a dictionary:

```
let numberOfLegs = ["spider" : 8, "bobber" : 4, "ant" : 6]

for (animalName, legCount) in numberOfLegs {
	print("\(animalName)s have \(legCount) legs.")
}
// spiders have 8 legs.
// bobbers have 4 legs.
// ants have 6 legs.
```

---

## <a id="19">Functions</a>

**Functions** are self-contained chunks of code that perform a specific task. You give a function a name that identifies what it does, and this name is used to “call” the function to perform its task when needed.

A function takes inputs (called **parameters**) and returns some output.

### <a id="20">Declaring a Function</a>

```
func squareNum(n: Int) -> Int {
    return n * n
}
```

- "**squareNum** is a function that takes in an integer (named **n**) and returns an integer."

### <a id="21">Calling a Function</a>

```
let num = squareNum(n: 5)
```

- **num** now contains the value 25.

### <a id="22">No Parameters/Return Type</a>

Functions don't have to have parameters or a return type:

```
func printHelloWorld() {
    print("Hello, world!")
}
```

---

## <a id="23">Classes</a>

Sometimes we want to group together multiple related pieces of data and store them in a single variable.

**Classes** are general-purpose, flexible constructs that become the building blocks of your program’s code. 

You add functionality to your classes and structures by adding **properties** (variables) and **methods** (functions).

### <a id="24">Declaring a Class</a>

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

### <a id="25">Initializers</a>

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

### <a id="26">Creating a Class Instance</a>

We can create an instance of our **Flatulan** class as follows:

```
let myFlatulan = Flatulan(initialX: 0, initialY: 0)
```

And use it like this:

```
myFlatulan.moveRight()
myFlatulan.fart()
```

