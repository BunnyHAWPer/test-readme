# The Ore Programming Language

Ore is a modern, developer-friendly programming language combining the best features from multiple programming paradigms. It's designed to be expressive, powerful, and easy to learn.

> **Note on Code Examples:** All code examples in this documentation use the `ore` syntax highlighting tag. For optimal viewing experience, use a Markdown viewer or editor that supports syntax highlighting like GitHub, VS Code, or any modern IDE.
>
> **Custom Syntax Highlighting:** To customize the colors, you can use the following CSS in your markdown renderer or website:
>
> ```css
> /* Dracula Theme (Dark) */
> .language-ore .keyword { color: #ff79c6; }             /* Keywords like let, fn, if */
> .language-ore .string { color: #f1fa8c; }              /* String literals */
> .language-ore .number { color: #bd93f9; }              /* Numeric literals */
> .language-ore .comment { color: #6272a4; }             /* Comments */
> .language-ore .function { color: #50fa7b; }            /* Function names */
> .language-ore .variable { color: #f8f8f2; }            /* Variables */
> .language-ore .operator { color: #ff79c6; }            /* Operators +, -, *, / */
> .language-ore .type { color: #8be9fd; }                /* Type names like int, string */
> .language-ore .class-name { color: #8be9fd; }          /* Class and struct names */
> .language-ore .builtin { color: #ffb86c; }             /* Built-in functions */
>
> /* OR */
>
> /* Nord Theme (Dark) */
> .nord .language-ore .keyword { color: #81A1C1; }       /* Keywords */
> .nord .language-ore .string { color: #A3BE8C; }        /* Strings */
> .nord .language-ore .number { color: #B48EAD; }        /* Numbers */
> .nord .language-ore .comment { color: #616E88; }       /* Comments */
> .nord .language-ore .function { color: #88C0D0; }      /* Functions */
> .nord .language-ore .variable { color: #D8DEE9; }      /* Variables */
> .nord .language-ore .operator { color: #81A1C1; }      /* Operators */
> .nord .language-ore .type { color: #8FBCBB; }          /* Types */
> .nord .language-ore .class-name { color: #8FBCBB; }    /* Classes */
> .nord .language-ore .builtin { color: #EBCB8B; }       /* Built-ins */
>
> /* OR */
>
> /* Monokai Theme (Dark) */
> .monokai .language-ore .keyword { color: #F92672; }    /* Keywords */
> .monokai .language-ore .string { color: #E6DB74; }     /* Strings */
> .monokai .language-ore .number { color: #AE81FF; }     /* Numbers */
> .monokai .language-ore .comment { color: #75715E; }    /* Comments */
> .monokai .language-ore .function { color: #A6E22E; }   /* Functions */
> .monokai .language-ore .variable { color: #F8F8F2; }   /* Variables */
> .monokai .language-ore .operator { color: #F92672; }   /* Operators */
> .monokai .language-ore .type { color: #66D9EF; }       /* Types */
> .monokai .language-ore .class-name { color: #66D9EF; } /* Classes */
> .monokai .language-ore .builtin { color: #FD971F; }    /* Built-ins */
>
> /* OR */
>
> /* GitHub Theme (Light) */
> .github-light .language-ore .keyword { color: #D73A49; }     /* Keywords */
> .github-light .language-ore .string { color: #032F62; }      /* Strings */
> .github-light .language-ore .number { color: #005CC5; }      /* Numbers */
> .github-light .language-ore .comment { color: #6A737D; }     /* Comments */
> .github-light .language-ore .function { color: #6F42C1; }    /* Functions */
> .github-light .language-ore .variable { color: #24292E; }    /* Variables */
> .github-light .language-ore .operator { color: #D73A49; }    /* Operators */
> .github-light .language-ore .type { color: #005CC5; }        /* Types */
> .github-light .language-ore .class-name { color: #6F42C1; }  /* Classes */
> .github-light .language-ore .builtin { color: #E36209; }     /* Built-ins */
> ```
>
> The default Dracula theme provides excellent readability and visual distinction between different syntax elements, or you can choose from the Nord, Monokai, or GitHub light alternatives.
>
> **To use these themes:** Add the CSS to your website's stylesheet, then add the appropriate class to your HTML container (e.g., `<div class="monokai">` or `<div class="github-light">`).

```ore
// A colorful example of the Ore programming language
import math
import Terminal

fn main() {
    // Welcome message with terminal styling
    println(Terminal.bold(Terminal.cyan("Welcome to the Ore Programming Language!")))
    
    // Variable declarations
    let name = "World"
    let numbers = [1, 4, 9, 16, 25]
    
    // String interpolation and f-strings
    println(f"Hello, {name}!")
    
    // Functional operations on collections
    let squares = numbers.map(n => math.sqrt(n))
    
    // Looping with for-in and range
    println(Terminal.yellow("First 5 square roots:"))
    for (num, i in squares) {
        println(f"{i+1}. √{numbers[i]} = {num}")
    }
    
    // Using with statement for file operations
    with (let file = File.open("welcome.txt", "w")) {
        file.write(f"Welcome to Ore, {name}!")
    }
    
    // Creating a simple chart
    Chart.bar(
        ["Easy", "Powerful", "Fun"], 
        [90, 95, 100],
        { title: "Why Choose Ore?" }
    )
}
```

## Table of Contents

- [Basic Syntax](#basic-syntax)
- [Imports](#imports)
- [Variables and Constants](#variables-and-constants)
- [Print and Input](#print-and-input)
- [Data Types and Conversion](#data-types-and-conversion)
- [Null Values](#null-values)
- [Strings](#strings)
- [Collections: Lists](#collections-lists)
- [Collections: Tuples](#collections-tuples)
- [Collections: Dictionaries](#collections-dictionaries)
- [Collections: Sets](#collections-sets)
- [Operators](#operators)
- [Control Flow: Conditions](#control-flow-conditions)
- [Control Flow: Loops](#control-flow-loops)
- [Ranges](#ranges)
- [Functions](#functions)
- [Destructuring](#destructuring)
- [Spread Syntax](#spread-syntax)
- [Async/Await](#asyncawait)
- [Structs and Classes](#structs-and-classes)
- [Operator Overloading](#operator-overloading)
- [Enums and Unions](#enums-and-unions)
- [Error Handling](#error-handling)
- [Modules](#modules)
- [Type Inspection](#type-inspection)
- [File I/O](#file-io)
- [Data Visualization](#data-visualization)
- [Concurrency](#concurrency)
- [Built-in Functions](#built-in-functions)
- [Examples](#examples)

## Basic Syntax

### Comments

```ore
// Single-line comment (C-style)

# Single-line comment (Python-style)

/*
Multi-line comment
spanning multiple lines
*/
```

## Imports

```ore
import math                     // Import entire module
from math import sin, cos       // Import specific items
import math as m                // Import with alias
from math import *              // Import all (use with caution)
```

## Variables and Constants

### Variable Declaration

```ore
let name = "Dhruv"              // String
let char = 'c'                  // Character
let age = 30                    // Integer (type inferred)
let active = true               // Boolean
let pi = 3.14159                // Float (type inferred)

// Explicit type annotations
let count: int = 10
let version: float = 1.0
let message: string = "Hello"
let isEnabled: bool = false
```

### Constants

```ore
const PI = 3.14159
const MAX_USERS: int = 1000
```

## Print and Input

### Basic Output

```ore
print("Hello, World!")          // Print with no newline
println("Hello, World!")        // Print with newline

// Print with formatted values
print("Value: ${count}")        // String interpolation
print(f"Value: {count}")        // f-string style interpolation
```

### Input

```ore
let user_input = input("Enter your name: ")              // Get user input as string
let age_num = int(input("Enter your age: "))            // Input with type conversion
let height = float(input("Enter your height in m: "))    // Input with type conversion
```

## Data Types and Conversion

### Basic Types

```ore
let int_val = 42                // Integer
let float_val = 3.14            // Float
let str_val = "hello"           // String
let bool_val = true             // Boolean
let char_val = 'A'              // Character
```

### Type Conversion

```ore
// Python-style conversion functions
let string_value = str(42)           // "42"
let integer_value = int("42")        // 42
let float_value = float("3.14")      // 3.14
let boolean_value = bool("true")     // true
let list_from_other = list((1, 2, 3)) // [1, 2, 3]
let tuple_from_other = tuple([1, 2, 3]) // (1, 2, 3)
let set_from_other = set([1, 2, 2, 3]) // {1, 2, 3}
let frozen_set = frozenset({1, 2, 3}) // immutable set
let dict_from_entries = dict([["name", "John"], ["age", 30]])

// Alternative constructor syntax
let str_val2 = String(42)            // "42"
let int_val2 = Integer("42")         // 42
let float_val2 = Float("3.14")       // 3.14
let bool_val2 = Boolean(1)           // true
let list_val = List((1, 2, 3))       // [1, 2, 3]
let set_val = Set([1, 2, 2, 3])      // {1, 2, 3}
```

## Null Values

```ore
// Different ways to represent null (all equivalent)
let v1 = null                  // Primary null syntax
let v2 = NULL                  // Alternate syntax 
let v3 = None                  // Python-style null
let v4 = undefined             // JavaScript-style undefined

// Nullable type declaration
let email: string? = null      // Can hold string or null

// Null checking
if (v1 == null) { ... }        // Standard equality check
if (v1 === null) { ... }       // Strict equality check
if (v1 is null) { ... }        // Type checking

// Null coalescing
let username = input ?? "guest"  // Default if null

// Safe navigation (optional chaining)
let city = user?.address?.city   // null if user or address is null
```

## Strings

### String Creation

```ore
let greeting = "Hello, World!"              // Double quotes
let single_quote = 'Single quotes work too' // Single quotes

// String interpolation
let message = "Hello, ${name}!"      // Variable interpolation

// f-strings (Python-style)
let f_message = f"Hello, {name}!"    // Alternative interpolation
let f_expr = f"1 + 1 = {1 + 1}"      // With expressions
let f_format = f"{pi:.2f}"           // With formatting: "3.14"

// Raw strings (no escape sequences)
let path = r"C:\Users\dhruv\Documents"

// Multi-line strings
let multiline = """
    This is a multi-line string
    that preserves whitespace
    and formatting
"""
```

### String Operations

```ore
let upper = greeting.toUpper()                // "HELLO, WORLD!"
let lower = greeting.toLower()                // "hello, world!"
let trimmed = "  hello  ".trim()              // "hello"
let parts = greeting.split(", ")              // ["Hello", "World!"]
let joined = ["Hello", "World"].join(", ")    // "Hello, World"
let replaced = greeting.replace("World", "Ore") // "Hello, Ore!"
let contains = greeting.contains("World")     // true
let starts = greeting.startsWith("Hello")     // true
let ends = greeting.endsWith("!")             // true
```

### String Indexing and Slicing

```ore
let first_char = greeting[0]         // 'H'
let last_char = greeting[-1]         // '!'
let substr1 = greeting[0..4]         // "Hello"
let substr2 = greeting[7..]          // "World!"
let substr3 = greeting[..-2]         // "Hello, World"
let substr4 = greeting[::2]          // "Hlo ol!"    (step by 2)
let reversed = greeting[::-1]        // "!dlroW ,olleH" (reverse)
let part = greeting[0..10:2]         // "Hlo W"      (slice with step)
```

## Operators

### Arithmetic Operators

```ore
let a = 10
let b = 3

a + b        // 13 (addition)
a - b        // 7 (subtraction)
a * b        // 30 (multiplication)
a / b        // 3.33333 (division)
a % b        // 1 (modulo/remainder)
a // b       // 3 (integer division)
a ** b       // 1000 (exponentiation)

// Increment/decrement
a++          // Increment by 1
b--          // Decrement by 1
```

### Comparison Operators

```ore
a == b       // false (equal to)
a != b       // true (not equal to)
a > b        // true (greater than)
a < b        // false (less than)
a >= b       // true (greater than or equal to)
a <= b       // false (less than or equal to)
a === b      // false (strict equality - same type and value)
a !== b      // true (strict inequality)
```

### Logical Operators

```ore
true && false    // false (logical AND)
true || false    // true (logical OR)
!true            // false (logical NOT)
```

### Identity Operators

```ore
// Check if two variables reference the same object
let x = [1, 2, 3]
let y = x
let z = [1, 2, 3]

x is y       // true (same object)
x is z       // false (different objects)
x is not z   // true (different objects)
```

### Membership Operators

```ore
// Check if a value exists in a collection
let nums = [1, 2, 3, 4, 5]
let user = {"name": "Dhruv", "age": 25}

3 in nums            // true
6 in nums            // false
6 not in nums        // true
"name" in user       // true
"email" in user      // false
```

### Type Checking Operators

```ore
let value = 42

value is int         // true
value is string      // false
value is not string  // true
```

### Bitwise Operators

```ore
let a = 5            // 101 in binary
let b = 3            // 011 in binary

a & b                // 1 (bitwise AND)
a | b                // 7 (bitwise OR)
a ^ b                // 6 (bitwise XOR)
~a                   // -6 (bitwise NOT)
a << 1               // 10 (left shift by 1)
a >> 1               // 2 (right shift by 1)
```

### Assignment Operators

```ore
let x = 10           // Simple assignment
x += 5               // 15 (add and assign)
x -= 3               // 12 (subtract and assign)
x *= 2               // 24 (multiply and assign)
x /= 4               // 6 (divide and assign)
x %= 4               // 2 (modulo and assign)
x **= 2              // 4 (exponentiate and assign)
```

### Special Operators

```ore
// Ternary operator
let age = 20
let status = age >= 18 ? "adult" : "minor"    // "adult"

// Null coalescing
let display_name = user_name ?? "Anonymous"   // Default if null

// Pipeline operator
let result = data |> filter(x => x > 0) |> map(x => x * 2) |> sum()

// Spread operator
let combined = [...arr1, ...arr2]

// Range operators
1..10        // Inclusive range: 1, 2, 3, ..., 10
1..<10       // Exclusive range: 1, 2, 3, ..., 9
```

## Control Flow: Conditions

### Conditionals

```ore
if (x > 10) {
    print("x is greater than 10")
} elif (x < 5) {
    print("x is less than 5")
} else {
    print("x is between 5 and 10")
}

// Ternary operator
let status = age >= 18 ? "adult" : "minor"
```

### Switch Statement

```ore
switch (day) {
    case "Monday":
        startWorkWeek()
        break
    case "Saturday":
    case "Sunday":
        weekend()
        break
    default:
        regularDay()
}
```

### Pattern Matching

```ore
match (value) {
    0 => print("zero"),
    1 | 2 => print("one or two"),
    x if x > 10 => print("large number: ${x}"),
    _ => print("default case")
}
```

## Control Flow: Loops

### While and Do-While Loops

```ore
// While loop
while (condition) {
    // Code
    if (errorCondition) break       // Exit loop
    if (skipCondition) continue     // Skip to next iteration
}

// Do-while loop
do {
    print(i)
    i++
} while (i < 5)
```

### For Loops

```ore
// C-style for loop
for (let i = 0; i < 10; i++) {
    print(i)
}

// For-in loop (collections)
for (item in collection) {
    print(item)
}

// For-in with index
for (item, idx in collection) {
    print("${idx}: ${item}")
}

// Python-style range-based loop
for (i in range(1, 10)) {          // 1, 2, ..., 9
    print(i)
}

for (i in range(1, 10, 2)) {       // 1, 3, 5, 7, 9 (with step)
    print(i)
}
```

## Ranges

### Range Syntax

```ore
// Inclusive range: 1, 2, 3, ..., 10
for (i in 1..10) {
    print(i)
}

// Exclusive range: 1, 2, 3, ..., 9
for (i in 1..<10) {
    print(i)
}

// Alternative exclusive range: 1, 2, 3, ..., 9
for (i in 1 until 10) {
    print(i)
}

// Range with step: 1, 3, 5, 7, 9
for (i in 1..10 step 2) {
    print(i)
}

// Descending range: 10, 9, 8, ..., 1
for (i in 10..1 step -1) {
    print(i)
}

// Combining range features: 5, 10, 15, 20, 25
for (i in 5 until 30 step 5) {
    print(i)
}
```

### Range Function (Python-style)

```ore
// Using range() function
for (i in range(10)) {              // 0, 1, 2, ..., 9
    print(i)
}

for (i in range(5, 10)) {           // 5, 6, 7, 8, 9
    print(i)
}

for (i in range(0, 10, 2)) {        // 0, 2, 4, 6, 8
    print(i)
}
```

## Functions

### Basic Functions

```ore
// Function declaration
fn add(a: int, b: int): int {
    return a + b
}

// Function call
let sum = add(5, 10)
```

### Arrow Functions

```ore
let square = (x) => x * x
let multiply = (a, b) => { return a * b }
```

### Default Parameters

```ore
fn greet(name: string, greeting: string = "Hello") {
    print("${greeting}, ${name}!")
}

greet("Dhruv")            // "Hello, Dhruv!"
greet("Dhruv", "Hi")      // "Hi, Dhruv!"
```

### Named Parameters

```ore
fn createUser(name: string, age: int, email: string?) {
    // Function body
}

// Call with named parameters (order doesn't matter)
createUser(
    name: "Dhruv",
    email: "dhruv@example.com",
    age: 25
)
```

### Required Parameters (Dart-style)

```ore
// Required parameters are marked with 'required' keyword
fn greet({required name, greeting = "Hello"}) {
    print("${greeting}, ${name}!")
}

// The 'name' parameter must be provided
greet(name: "Dhruv")                 // "Hello, Dhruv!"
greet(name: "Dhruv", greeting: "Hi") // "Hi, Dhruv!"
// greet(greeting: "Hi")             // Error! Missing required parameter 'name'

// Combined with positional parameters
fn process(positional1, {required name, required age, email = null}) {
    // Function body
}

process("value", name: "Dhruv", age: 25)
```

### Rest Parameters / Spread Syntax

```ore
// Rest parameter (variadic function)
fn sum(...numbers) {
    let total = 0
    for (n in numbers) {
        total += n
    }
    return total
}

let total = sum(1, 2, 3, 4, 5)  // Accepts any number of arguments

// Spread syntax
let numbers = [1, 2, 3]
sum(...numbers)  // Same as sum(1, 2, 3)
```

### Args and Kwargs (Python-style)

```ore
// *args captures remaining positional arguments as array
// **kwargs captures remaining named arguments as dictionary
fn process(required, *args, **kwargs) {
    print("Required: ${required}")
    
    // Access positional arguments
    for (arg, i in args) {
        print("args[${i}]: ${arg}")
    }
    
    // Access keyword arguments
    for (key, value in kwargs) {
        print("${key}: ${value}")
    }
}

// Usage examples
process("required", 1, 2, 3)                      // With positional args
process("required", x: 10, y: 20)                 // With keyword args
process("required", 1, 2, 3, x: 10, y: 20)        // Both types
```

### Function Overloading

```ore
fn add(a: int, b: int): int {
    return a + b
}

fn add(a: string, b: string): string {
    return a + b
}

let num_sum = add(1, 2)           // Calls int version
let str_concat = add("a", "b")    // Calls string version
```

### Generics

```ore
fn identity<T>(value: T): T {
    return value
}

let num = identity<int>(42)
let str = identity<string>("hello")
```

### Decorators

```ore
@deprecated("Use newFunction instead")
fn oldFunction() {
    // Function body
}

@memoize  // Caches function results
fn fibonacci(n: int): int {
    if (n <= 1) return n
    return fibonacci(n-1) + fibonacci(n-2)
}
```

## Data Structures

### Basic Types

```ore
// Lists (arrays)
let numbers = [1, 2, 3, 4, 5]

// Tuples
let person = ("John", 30, true)

// Dictionaries (maps)
let user = {"name": "John", "age": 30}

// Sets
let uniqueNumbers = {1, 2, 3, 4, 5}
```

### List Comprehensions

```ore
let evens = [x for x in numbers if x % 2 == 0]
let squares = [x*x for x in 1..10]
```

### Destructuring

### Tuple Destructuring

```ore
// Tuple destructuring
let (name, age, active) = ("John", 30, true)
```

### List Destructuring

```ore
// List destructuring
let [first, second, ...rest] = [1, 2, 3, 4, 5]
// first = 1, second = 2, rest = [3, 4, 5]
```

### Object Destructuring

```ore
// Object destructuring
let { name: userName, age: userAge } = user
// userName = user.name, userAge = user.age

// Shorthand when variable names match keys
let { name, age } = user
// name = user.name, age = user.age
```

### In Function Parameters

```ore
// Destructuring in function parameters
fn processUser({ name, age }) {
    print("Name: ${name}, Age: ${age}")
}

processUser({ name: "John", age: 30 })
```

### Structs

```ore
struct User {
    name: string
    age: int
    email: string?
    
    // Constructor using 'constructor' keyword
    constructor(name: string, age: int, email: string? = null) {
        this.name = name
        this.age = age
        this.email = email
    }
    
    // Alternative init method (also works)
    init(name: string, age: int, email: string? = null) {
        this.name = name
        this.age = age
        this.email = email
    }
    
    // Methods
    fn isAdult(): bool {
        return age >= 18
    }
    
    fn toString(): string {
        return "User(${name}, ${age})"
    }
}
```

### Creating Instances

```ore
// Object creation
let user1 = User("Alice", 30)                 // Using default constructor
let user2 = constructor User("Bob", 25)       // Explicit constructor call
let user3 = User(name: "Charlie", age: 35)    // Named parameters in constructor
```

### Generic Structs

```ore
struct List<T> {
    items: T[]
    
    fn add(item: T) {
        items.push(item)
    }
    
    fn get(index: int): T? {
        if (index >= 0 && index < items.length) {
            return items[index]
        }
        return null
    }
}

let numbers = List<int>()
numbers.add(42)
```

### Enums

```ore
enum Color { RED, GREEN, BLUE }

// Enum with values
enum HttpStatus {
    OK = 200,
    NOT_FOUND = 404,
    SERVER_ERROR = 500
}

let status = HttpStatus.OK
print(status)  // 200
```

### Unions

```ore
union IntOrString {
    int_val: int
    str_val: string
}

let val: IntOrString = IntOrString.int_val(42)

if (val is IntOrString.int_val) {
    print("int: ${val.int_val}")
} elif (val is IntOrString.str_val) {
    print("str: ${val.str_val}")
}
```

### Type Aliases

```ore
type ID = int | string          // Union type alias
let userId: ID = 42
let productId: ID = "prod-123"
```

### Generic Collections

```ore
struct List<T> {
    items: T[]
    
    fn add(item: T) {
        items.push(item)
    }
    
    fn get(index: int): T? {
        if (index >= 0 && index < items.length) {
            return items[index]
        }
        return null
    }
}

let numbers = List<int>()
numbers.add(42)
```

## Error Handling

### Exceptions

```ore
try {
    riskyOperation()
} catch (err) {
    print("Error: ${err}")
} finally {
    cleanup()
}
```

### Nullable Types and Safe Navigation

```ore
let user: User? = getUser(id)
let city = user?.address?.city  // Will be null if user or address is null

// Null coalescing
let name = user?.name ?? "Guest"
```

### Result Type

```ore
enum Result<T, E> {
    Ok(T),
    Err(E)
}

fn divide(a: int, b: int): Result<int, string> {
    if (b == 0) {
        return Result.Err("Division by zero")
    }
    return Result.Ok(a / b)
}

// Using the result
let result = divide(10, 2)
match (result) {
    Result.Ok(value) => print("Result: ${value}"),
    Result.Err(error) => print("Error: ${error}")
}

// Simplified error handling with try operator
fn compute(): Result<int, string> {
    let a = try! divide(10, 2)  // Unwraps Ok or returns Err
    let b = try! divide(a, 1)
    return Result.Ok(b)
}
```

## Modules

### Module Declaration

```ore
module math_utils {
    fn square(x: int): int {
        return x * x
    }
    
    fn cube(x: int): int {
        return x * x * x
    }
    
    // Private to module
    private fn helper() {
        // Implementation
    }
}
```

### Importing Modules

```ore
// Import and use
import math_utils
let squared = math_utils.square(5)

// Import specific functions
from math_utils import square, cube

// Import with alias
import math_utils as mu
let cubed = mu.cube(3)
```

## Type Inspection

### Basic Type Information

```ore
// typeof() returns the type name as a string
let type_name = typeof(x)       // Returns "int"

// type() returns the actual type object for reflection
let type_obj = type(x)          // Returns the type object
let same_type = type(x) == type(10)  // true
```

### Type Checking

```ore
// Type checking
let is_int = x is int           // Type checking, returns true
let is_num = x is number        // Type category checking
let is_instance = isinstance(42, int)  // Check if value is of type int
let is_subtype = issubclass(int, number)  // Check if int is a subtype of number 
let subtype_check = type(int).isSubtypeOf(type(number))  // Using type objects
```

### Reflection

```ore
// Reflection with type() function
let str_type = type(string)         // Get the type object for string
let methods = type_obj.methods()    // Get list of methods for a type
let properties = type_obj.properties() // Get list of properties
let is_numeric = type_obj.isNumeric()  // Check if type is numeric
let base_type = type_obj.baseType()    // Get parent type if any
let implements = type_obj.implements(Comparable) // Check interface implementation
```

## File I/O

### Reading Files

```ore
// Reading entire file as a string
let content = File.read("path/to/file.txt")

// Reading file as a list of lines
let lines = File.readLines("path/to/file.txt")
for (line in lines) {
    print(line)
}

// Reading file as bytes (binary data)
let bytes = File.readBytes("path/to/file.txt")
```

### Writing Files

```ore
// Writing to a file (overwrites existing content)
File.write("path/to/file.txt", "Hello, world!")

// Appending to a file
File.append("path/to/file.txt", "\nNew line of text")

// Writing a list of lines to a file
let dataLines = ["Line 1", "Line 2", "Line 3"]
File.writeLines("path/to/file.txt", dataLines)
```

### File Operations

```ore
// Opening a file with explicit open/close
let file = File.open("path/to/file.txt", "r")  // Open for reading
let text = file.readAll()                      // Read entire file
file.close()                                   // Close the file

// Using "with" statement (automatically closes file)
with (let file = File.open("path/to/file.txt", "w")) {
    file.write("Line 1\n")
    file.write("Line 2\n")
}  // File is automatically closed when block exits
```

### File Modes

```ore
// File open modes
let readFile = File.open("data.txt", "r")      // Read mode (default)
let writeFile = File.open("data.txt", "w")     // Write mode (truncates file)
let appendFile = File.open("data.txt", "a")    // Append mode
let readWriteFile = File.open("data.txt", "r+") // Read and write mode
let writeReadFile = File.open("data.txt", "w+") // Write and read mode (truncates)
let appendReadFile = File.open("data.txt", "a+") // Append and read mode

// Binary mode (add 'b' suffix)
let binaryFile = File.open("image.jpg", "rb")  // Binary read mode
```

### File Information

```ore
// Checking if a file exists
if (File.exists("path/to/file.txt")) {
    print("File exists!")
}

// Getting file information
let fileInfo = File.getInfo("path/to/file.txt")
let size = fileInfo.size                       // File size in bytes
let modTime = fileInfo.modificationTime        // Last modification time
let isReadable = fileInfo.isReadable           // Check if file is readable
let isWritable = fileInfo.isWritable           // Check if file is writable
```

### Directory Operations

```ore
// Listing files in a directory
let files = Directory.list("path/to/dir")
for (file in files) {
    print(file)
}

// Creating a directory
Directory.create("path/to/new/dir")

// Creating nested directories
Directory.createAll("path/to/nested/dirs")

// Removing a directory
Directory.remove("path/to/dir")                 // Remove empty directory
Directory.removeAll("path/to/dir")              // Remove directory and contents

// Getting and changing current directory
let currentDir = Directory.current()
Directory.change("path/to/other/dir")
```

### Path Operations

```ore
// Joining path components
let fullPath = Path.join("documents", "projects", "notes.txt")

// Getting path components
let extension = Path.extension("document.txt")   // "txt"
let filename = Path.basename("path/to/file.txt") // "file.txt"
let directory = Path.dirname("path/to/file.txt") // "path/to"

// Normalizing paths
let normalized = Path.normalize("path/../other/./file.txt") // "other/file.txt"

// Getting absolute path
let absolutePath = Path.absolute("relative/path")
```

## Data Visualization

### Inspecting Variables

```ore
// Print detailed information about variables
inspect(myVariable)                      // Outputs type, structure, and content
dump(complexObject)                      // Recursively dump object contents
```

### Pretty Printing

```ore
// Format JSON data for readability
let userData = {
    "name": "Alice",
    "age": 28,
    "skills": ["JavaScript", "Python", "Ore"]
}

// Formatted JSON output (with indentation)
print(JSON.stringify(userData, null, 2))

// Shorter alternative
print(JSON.pretty(userData))

// Display tabular data
let users = [
    {"id": 1, "name": "Alice", "role": "Admin"},
    {"id": 2, "name": "Bob", "role": "User"},
    {"id": 3, "name": "Charlie", "role": "User"}
]

Table.print(users)
// Output:
// ┌────┬─────────┬────────┐
// │ id │ name    │ role   │
// ├────┼─────────┼────────┤
// │ 1  │ Alice   │ Admin  │
// │ 2  │ Bob     │ User   │
// │ 3  │ Charlie │ User   │
// └────┴─────────┴────────┘
```

### Debugging Tools

```ore
// Debug expressions with values
debug(x + y)          // Outputs: "x + y = 15" (assuming x=10, y=5)

// Assertions
assert(user.age >= 18, "User must be at least 18 years old")

// Performance measurement
time(() => {
    // Code to measure
    for (i in 0..1000) {
        fibonacci(i)
    }
})  // Outputs: "Time elapsed: 45ms"
```

### Terminal Formatting

```ore
// Colored output
print(Terminal.red("Error: File not found"))
print(Terminal.green("Success: Data saved"))
print(Terminal.yellow("Warning: Low disk space"))

// Text styling
print(Terminal.bold("Important message"))
print(Terminal.underline("Emphasized text"))
print(Terminal.italic("Note: Read carefully"))

// Combined styling
print(Terminal.bold(Terminal.red("Critical error!")))
```

### Simple Charts

```ore
// Bar chart
Chart.bar(
    ["Mon", "Tue", "Wed", "Thu", "Fri"], 
    [120, 200, 150, 80, 190]
)

// Line chart
Chart.line(
    [1, 2, 3, 4, 5], 
    [10, 25, 15, 30, 45]
)

// Pie chart
Chart.pie(
    ["Product A", "Product B", "Product C"], 
    [30, 50, 20]
)
```

## Concurrency

### Futures and Promises

```ore
// Creating and working with futures
let future = Future.create()
future.resolve(42)                  // Resolve with a value
future.reject(new Error("Failed"))  // Reject with an error

// Consuming futures
future.then(
    value => print("Value: ${value}"),
    error => print("Error: ${error}")
)

// Chaining futures
future
    .then(value => value * 2)
    .then(value => print("Doubled: ${value}"))
    .catch(error => print("Error: ${error}"))
```

### Async/Await

```ore
// Using async/await with futures
async fn getData(url: string): string {
    try {
        let response = await http.get(url)
        return response.body
    } catch (err) {
        print("Error fetching data: ${err}")
        return ""
    }
}

// Calling async function
async fn main() {
    let data = await getData("https://api.example.com/data")
    print(data)
}
```

### Parallel Execution

```ore
// Running tasks in parallel
async fn fetchMultipleApis() {
    // Wait for all futures to complete
    let [users, products, orders] = await Future.all([
        getData("https://api.example.com/users"),
        getData("https://api.example.com/products"),
        getData("https://api.example.com/orders")
    ])
    
    // Process the results
    processData(users, products, orders)
}

// Race - get first result only
async fn fetchWithFallback() {
    let result = await Future.race([
        getData("https://api.example.com/primary"),
        getData("https://api.example.com/fallback")
    ])
    
    return result
}
```

### Worker Threads

```ore
// Spawning a worker thread
let worker = Worker.spawn("worker_script.ore")

// Send message to worker
worker.postMessage({
    command: "process",
    data: largeDataset
})

// Receive message from worker
worker.onMessage(message => {
    if (message.type == "result") {
        displayResult(message.data)
    } else if (message.type == "progress") {
        updateProgressBar(message.percent)
    }
})

// Handle errors
worker.onError(error => {
    print("Worker error: ${error}")
})

// Terminate worker when done
worker.terminate()
```

### Channels and CSP

```ore
// Creating a channel
let channel = Channel.create(10)  // Buffered channel with capacity 10

// Sending values (blocks if channel is full)
channel.send("Hello")

// Receiving values (blocks if channel is empty)
let message = channel.receive()

// Non-blocking operations
let sendSuccess = channel.trySend("data")  // Returns false if full
let receiveResult = channel.tryReceive()   // Returns null if empty

// Closing a channel
channel.close()

// Select statement (inspired by Go)
select {
    case value = channel1.receive():
        print("Received from channel1: ${value}")
    case channel2.send(data):
        print("Sent to channel2")
    case timeout(1000):
        print("Operation timed out")
    default:
        print("No channel ready")
}
```

### Synchronization Primitives

```ore
// Mutex for critical sections
let mutex = Mutex.create()

// Explicit locking/unlocking
mutex.lock()
try {
    // Critical section
    sharedResource.update()
} finally {
    mutex.unlock()  // Always unlock, even if exception occurs
}

// Helper function for automatic locking/unlocking
withLock(mutex, () => {
    // Critical section
    sharedResource.update()
})

// Read-write lock (multiple readers, exclusive writer)
let rwLock = RWLock.create()

// Multiple readers can read simultaneously
withReadLock(rwLock, () => {
    // Read shared resource
    let value = sharedResource.getValue()
})

// Only one writer at a time
withWriteLock(rwLock, () => {
    // Modify shared resource
    sharedResource.setValue(newValue)
})
```

## Built-in Functions

### General Functions

```ore
// Output and input
print("Hello")                      // Print to stdout
println("Hello with newline")       // Print with newline
let value = input("Enter value: ")  // Get user input with prompt

// Type inspection
let type_name = typeof(42)          // Returns "int" as string
let type_obj = type(42)             // Returns the actual type object
let collection_size = len(list)     // Length of collection

// Type conversion
let str_val = str(42)               // Convert to string: "42"
let int_val = int("42")             // Convert to int: 42
let float_val = float("3.14")       // Convert to float: 3.14
let bool_val = bool("true")         // Convert to boolean: true
```

### Math Functions

```ore
abs(-10)                            // 10
min(5, 10)                          // 5
max(5, 10)                          // 10
round(3.7)                          // 4
floor(3.7)                          // 3
ceil(3.2)                           // 4
random()                            // Random float between 0 and 1
randomInt(1, 10)                    // Random integer between 1 and 10
sin(3.14)                           // Sine
cos(3.14)                           // Cosine
tan(3.14)                           // Tangent
sqrt(16)                            // 4 (square root)
pow(2, 3)                           // 8 (same as 2**3)
log(100)                            // Natural logarithm
log10(100)                          // 2 (base-10 logarithm)
```

### List Functions

```ore
// Basic operations
list[0]                            // Get first element
list.push(6)                       // Add to end: [1, 2, 3, 4, 5, 6]
let popped = list.pop()            // Remove from end, returns 6
list.first()                       // Get first element: 1
list.last()                        // Get last element: 5
list.insert(0, 0)                  // Insert at position: [0, 1, 2, 3, 4, 5]
list.remove(3)                     // Remove by value: [0, 1, 2, 4, 5]
list.removeAt(2)                   // Remove by index: [0, 1, 4, 5]
list[1..3]                         // Get sublist: [1, 4]

// Transformations
list.join(", ")                    // "0, 1, 4, 5"
list.sort()                        // Sort in place
list.sorted()                      // Get sorted copy
list.reversed()                    // Get reversed copy

// Functional operations
list.map(x => x * 2)               // [0, 2, 8, 10]
list.filter(x => x > 2)            // [4, 5]
list.reduce((acc, x) => acc + x, 0) // Sum: 10
list.forEach(x => print(x))        // Iterate without returning

// Information
list.sum()                         // 10
list.average()                     // 2.5
list.min()                         // 0
list.max()                         // 5
list.count(x => x > 2)             // 2
list.indexOf(4)                    // 2
list.contains(3)                   // false
list.any(x => x > 4)               // true
list.all(x => x >= 0)              // true
```

### String Functions

```ore
let name = "dhruv rawat"

// Case conversion
name.toUpper()                    // "DHRUV RAWAT"
name.toLower()                    // "dhruv rawat"
name.capitalize()                 // "Dhruv rawat"
name.title()                      // "Dhruv Rawat"

// Trimming
"  hello  ".trim()                // "hello"
"  hello  ".trimLeft()            // "hello  "
"  hello  ".trimRight()           // "  hello"

// Splitting and joining
name.split(" ")                   // ["dhruv", "rawat"]
["dhruv", "rawat"].join(" ")      // "dhruv rawat"

// Searching and replacing
name.replace("d", "D")            // "Dhruv rawat"
name.replaceAll("a", "A")         // "dhruv rAwAt"
name.contains("dhruv")            // true
name.startsWith("dhruv")          // true
name.endsWith("rawat")            // true
name.indexOf("r")                 // 6
name.lastIndexOf("a")             // 9

// Extracting
name.charAt(0)                    // "d"
name.substring(0, 5)              // "dhruv"
name.slice(6)                     // "rawat"

// Formatting
"{} is {}".format(name, "cool")   // "dhruv rawat is cool"
```

### Dictionary Functions

```ore
let dict = {"name": "John", "age": 30}

// Information
dict.hasKey("name")               // true
dict.keys()                       // ["name", "age"]
dict.values()                     // ["John", 30]
dict.entries()                    // [["name", "John"], ["age", 30]]
dict.size()                       // 2
dict.isEmpty()                    // false

// Modification
dict.set("email", "john@example.com")  // Add or update
dict.remove("age")                     // Remove key
dict.clear()                           // Remove all entries
dict.merge({"city": "New York"})       // Combine dictionaries
```

### Set Functions

```ore
let set1 = {1, 2, 3, 4, 5}
let set2 = {4, 5, 6, 7}

// Set operations
set1.union(set2)                  // {1, 2, 3, 4, 5, 6, 7}
set1.intersection(set2)           // {4, 5}
set1.difference(set2)             // {1, 2, 3}
set2.difference(set1)             // {6, 7}
set1.symmetricDifference(set2)    // {1, 2, 3, 6, 7}

// Testing
set1.isSubset({1, 2})             // true
{1, 2, 3, 4, 5, 6}.isSuperset(set1) // true
set1.isDisjoint({6, 7, 8})        // true (no common elements)

// Modification
set1.add(6)                       // Add element
set1.remove(3)                    // Remove element
set1.clear()                      // Remove all elements
```

## Examples

### Simple Program

```ore
fn main() {
    print("Hello, Ore!")
    
    for (i in 1..5) {
        print("${i} squared is ${i*i}")
    }
}
```

### Fibonacci Sequence

```ore
@memoize
fn fibonacci(n: int): int {
    if (n <= 1) return n
    return fibonacci(n-1) + fibonacci(n-2)
}

fn main() {
    print("First 10 Fibonacci numbers:")
    for (i in 0..<10) {
        print("fibonacci(${i}) = ${fibonacci(i)}")
    }
}
```

### File Processing Example

```ore
fn processLogFile(path: string) {
    // Check if file exists
    if (!File.exists(path)) {
        print("Error: File not found")
        return
    }
    
    // Read the log file
    let lines = File.readLines(path)
    
    // Process and filter the lines
    let errorCount = 0
    let errorLines = []
    
    for (line, i in lines) {
        if (line.contains("ERROR")) {
            errorCount++
            errorLines.push("Line ${i+1}: ${line}")
        }
    }
    
    // Generate report file
    with (let reportFile = File.open("error_report.txt", "w")) {
        reportFile.write("Error Report for ${path}\n")
        reportFile.write("Total errors found: ${errorCount}\n\n")
        
        for (errorLine in errorLines) {
            reportFile.write("${errorLine}\n")
        }
    }
    
    print("Report generated: error_report.txt")
    print("Total errors found: ${errorCount}")
}

fn main() {
    processLogFile("application.log")
}
```

### Data Visualization Example

```ore
fn analyzeTemperatureData(filepath: string) {
    // 1. Load CSV data
    let lines = File.readLines(filepath)
    let temperatures = []
    let dates = []
    
    // Skip header line
    for (i in 1..<lines.length) {
        let parts = lines[i].split(",")
        dates.push(parts[0])
        temperatures.push(float(parts[1]))
    }
    
    // 2. Calculate statistics
    let min = temperatures.min()
    let max = temperatures.max()
    let avg = temperatures.average()
    
    // 3. Display results as text
    print(Terminal.bold("Temperature Analysis:"))
    print("Data points: ${temperatures.length}")
    print("Min: ${min}°C")
    print("Max: ${max}°C")
    print("Average: ${avg.toFixed(1)}°C")
    
    // 4. Create visualization
    print(Terminal.bold("\nTemperature Chart:"))
    Chart.line(
        dates,
        temperatures,
        {
            title: "Daily Temperatures",
            xLabel: "Date",
            yLabel: "Temperature (°C)"
        }
    )
    
    // 5. Display distribution as bar chart
    let distribution = {
        "< 0°C": temperatures.count(t => t < 0),
        "0-10°C": temperatures.count(t => t >= 0 && t < 10),
        "10-20°C": temperatures.count(t => t >= 10 && t < 20),
        "20-30°C": temperatures.count(t => t >= 20 && t < 30),
        "> 30°C": temperatures.count(t => t >= 30)
    }
    
    print(Terminal.bold("\nTemperature Distribution:"))
    Chart.bar(
        Object.keys(distribution),
        Object.values(distribution),
        { title: "Temperature Ranges" }
    )
}

fn main() {
    analyzeTemperatureData("temperature_data.csv")
}
```

### Concurrency Example

```ore
fn main() {
    // URL list to fetch data from
    let urls = [
        "https://api.example.com/users",
        "https://api.example.com/products",
        "https://api.example.com/orders",
        "https://api.example.com/analytics"
    ]
    
    // Progress tracking
    let completed = 0
    let mutex = Mutex.create()
    let progressBar = Terminal.progressBar(urls.length)
    
    // Create a channel for results
    let resultsChannel = Channel.create()
    
    // Process each URL in a separate worker thread
    for (url in urls) {
        // Launch a worker for each URL
        let worker = Worker.spawn("fetch_worker.ore")
        
        // Send the URL to the worker
        worker.postMessage({ url: url })
        
        // Handle the response
        worker.onMessage(result => {
            // Send result to the channel
            resultsChannel.send({
                url: url,
                data: result.data,
                time: result.time
            })
            
            // Update progress
            withLock(mutex, () => {
                completed++
                progressBar.update(completed)
            })
        })
        
        // Handle errors
        worker.onError(error => {
            print(Terminal.red("Error fetching ${url}: ${error}"))
            
            // Still need to update the progress
            withLock(mutex, () => {
                completed++
                progressBar.update(completed)
            })
            
            // Send error result to channel
            resultsChannel.send({
                url: url,
                error: error,
                time: 0
            })
        })
    }
    
    // Collect results asynchronously
    async fn collectResults() {
        let results = []
        
        // Collect all results from the channel
        for (i in 0..<urls.length) {
            let result = await resultsChannel.receive()
            results.push(result)
        }
        
        // Sort by response time
        results.sort((a, b) => a.time - b.time)
        
        // Display results
        println("\n" + Terminal.bold("Results:"))
        Table.print(results.map(r => {
            return {
                "URL": r.url,
                "Status": r.error ? "Error" : "Success",
                "Time (ms)": r.time,
                "Data Size": r.error ? 0 : r.data.length
            }
        }))
        
        // Display timing chart
        Chart.bar(
            results.map(r => r.url.split("/").pop()),
            results.map(r => r.time),
            { title: "Response Times (ms)" }
        )
    }
    
    // Start collecting results
    collectResults()
}
```

### HTTP Request

```ore
async fn main() {
    try {
        let url = "https://api.example.com/data"
        print("Fetching data from ${url}...")
        
        let data = await fetchData(url)
        let parsed = json.parse(data)
        
        print("Received ${parsed.items.length} items")
        
        for (item, i in parsed.items) {
            print("${i+1}. ${item.name}")
        }
    } catch (err) {
        print("Error: ${err}")
    }
}

async fn fetchData(url: string): string {
    let resp = await http.get(url)
    if (resp.status != 200) {
        throw "HTTP Error: ${resp.status}"
    }
    return resp.body
}
```

### Command Line Tool

```ore
fn main(argc, args[]) {
    if (argc < 2) {
        print("Usage: ${args[0]} <filename>")
        exit(1)
    }
    
    let filename = args[1]
    
    try {
        let content = fs.readFile(filename)
        let lines = content.split("\n")
        
        print("File ${filename} has ${lines.length} lines")
        
        let wordCount = 0
        for (line in lines) {
            let words = line.split(/\s+/).filter(w => w.length > 0)
            wordCount += words.length
        }
        
        print("Word count: ${wordCount}")
    } catch (err) {
        print("Error: ${err}")
        exit(1)
    }
}
```

## Collections: Lists

### List Creation

```ore
let numbers = [1, 2, 3, 4, 5]           // Basic list
let mixed = [1, "two", 3.0, true]       // Heterogeneous list
let empty_list = []                     // Empty list
let typed_list: int[] = [1, 2, 3]       // Typed list
```

### List Indexing and Slicing

```ore
let first = numbers[0]                  // 1
let last = numbers[-1]                  // 5
let sub_list = numbers[1..3]            // [2, 3, 4]
let every_other = numbers[::2]          // [1, 3, 5]
let reversed_list = numbers[::-1]       // [5, 4, 3, 2, 1]
```

### List Operations

```ore
numbers.push(6)                         // Add to end: [1, 2, 3, 4, 5, 6]
let popped = numbers.pop()              // Remove from end, returns 6
numbers.insert(0, 0)                    // Insert at position: [0, 1, 2, 3, 4, 5]
numbers.remove(3)                       // Remove by value
numbers.removeAt(2)                     // Remove by index
let sorted_list = numbers.sorted()      // Returns sorted copy
numbers.sort()                          // Sorts in place
let joined_str = numbers.join(", ")     // "0, 1, 4, 5"
```

### List Methods

```ore
let has_value = numbers.contains(4)     // true
let index = numbers.indexOf(4)          // 2
let is_empty = numbers.isEmpty()        // false
let size = numbers.length               // 4
```

### Functional Operations

```ore
let doubled = numbers.map(x => x * 2)   // [0, 2, 8, 10]
let filtered = numbers.filter(x => x > 2) // [4, 5]
let sum_val = numbers.reduce((acc, x) => acc + x, 0) // 10
numbers.forEach(x => print(x))          // Prints each item
```

### Statistical Methods

```ore
let sum = numbers.sum()                 // 10
let avg = numbers.average()             // 2.5
let min_val = numbers.min()             // 0
let max_val = numbers.max()             // 5
let count_val = numbers.count(x => x > 2) // 2
```

### List Comprehensions

```ore
let evens = [x for x in numbers if x % 2 == 0]
let squares = [x*x for x in 1..10]  // Using range
let matrix = [[i*j for i in 1..3] for j in 1..3]  // Nested comprehension
```

## Collections: Tuples

### Tuple Creation

```ore
let tuple = (1, "hello", 3.14)          // Basic tuple
let empty_tuple = ()                    // Empty tuple
let single_item_tuple = (1,)            // Note the comma
let nested_tuple = (1, (2, 3), 4)       // Nested tuple
```

### Tuple Indexing and Slicing

```ore
let tuple_first = tuple[0]              // 1
let tuple_last = tuple[-1]              // 3.14
let tuple_slice = tuple[1..]            // ("hello", 3.14)
let tuple_reverse = tuple[::-1]         // (3.14, "hello", 1)
```

### Tuple Methods

```ore
let tuple_length = tuple.length         // 3
let has_hello = tuple.contains("hello") // true
let hello_index = tuple.indexOf("hello") // 1
```

### Creating New Tuples (Immutable)

```ore
let extended_tuple = tuple.append(42)   // (1, "hello", 3.14, 42)
let combined_tuple = tuple.concat((5, 6)) // (1, "hello", 3.14, 5, 6)
let modified_tuple = tuple.replace(1, "world") // (1, "world", 3.14)
```

## Collections: Dictionaries

### Dictionary Creation

```ore
let user = {"name": "John", "age": 30}  // Basic dictionary
let empty_dict = {}                     // Empty dictionary
let typed_dict: Dictionary<string, int> = {"a": 1, "b": 2}  // Typed dictionary
```

### Dictionary Access

```ore
let user_name = user["name"]            // "John"
let user_age = user.age                 // 30 (dot notation)
```

### Dictionary Slicing

```ore
let subset = user["name".."age"]        // Get entries between "name" and "age"
```

### Dictionary Operations

```ore
user["email"] = "john@example.com"      // Add or update value
user.remove("age")                      // Remove key
let has_email = user.hasKey("email")    // true
let all_keys = user.keys()              // ["name", "email"]
let all_values = user.values()          // ["John", "john@example.com"]
let all_entries = user.entries()        // [["name", "John"], ["email", "john@example.com"]]
```
