# The Ore Programming Language

Ore is a modern, developer-friendly programming language combining the best features from multiple programming paradigms. It's designed to be expressive, powerful, and easy to learn. Ore is a compiled language built using LLVM and C++.

**Version:** 1.0.0  
**Author:** Dhruv Rawat

## Key Features

- **Compiled Performance**: Ore is compiled to native code using LLVM for high performance
- **Static Typing with Type Inference**: Strong static typing with intuitive type inference
- **Multi-paradigm**: Supports procedural, functional, and object-oriented programming styles
- **Memory Safety**: Automatic memory management without garbage collection overhead
- **Modern Syntax**: Clean, expressive syntax inspired by Python, JavaScript, Rust, and Swift
- **First-class Functions**: Functions as values, closures, and higher-order functions
- **Pattern Matching**: Powerful pattern matching capabilities
- **Comprehensive Standard Library**: Rich standard library covering common programming needs
- **Interoperability**: Seamless interoperability with C/C++ code

```ore
// A simple example of the Ore programming language
import math

fn main(argc, args) {
    // argc contains the number of arguments
    // args[0] is the program filename
    
    // Variable declarations
    let name = "World"
    let numbers = [1, 4, 9, 16, 25]
    
    // String interpolation
    println(f"Hello, {name}!")
    
    // Functional operations on collections
    let squares = numbers.map(n => math.sqrt(n))
    
    // Looping with for-in
    println("First 5 square roots:")
    for (num, i in squares) {
        println(f"{i+1}. √{numbers[i]} = {num}")
    }
    
    // Using with statement for file operations
    with (let file = File.open("welcome.txt", "w")) {
        file.write(f"Welcome to Ore, {name}!")
    }
}
```

## Table of Contents

- [Key Features](#key-features)
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
- [Collections: Frozen Sets (Immutable)](#collections-frozen-sets-immutable)
- [Collection Types Comparison](#collection-types-comparison)
- [Collection Examples](#collection-examples)
- [Operators](#operators)
- [Control Flow: Conditions](#control-flow-conditions)
- [Control Flow: Loops](#control-flow-loops)
- [Ranges](#ranges)
- [Functions](#functions)
- [Destructuring](#destructuring)
- [Spread Syntax](#spread-syntax)
- [Async/Await](#asyncawait)
- [Structs](#structs)
- [Operator Overloading](#operator-overloading)
- [Enums and Unions](#enums-and-unions)
- [Error Handling](#error-handling)
- [Importing Modules](#importing-modules)
- [Type Inspection](#type-inspection)
- [File I/O](#file-io)
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
let user1 = User("Alice", 30)                 // Using struct name directly like C++
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

## Importing Modules

```ore
// Import and use
import math_utils
let squared = math_utils.square(5)

// Import specific functions
from math_utils import square, cube

// Import with alias
import math_utils as mu
let cubed = mu.cube(3)

// Import all (use with caution)
from math_utils import *
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

## Built-in Functions

### General Functions

```ore
// Output and input
print(value)                                // Print to stdout (no newline)
println(value)                              // Print with newline
let input_value = input("Enter value: ")    // Get user input with prompt

// Type inspection and conversion
let type_name = typeof(42)                  // Returns "int" as string
let type_obj = type(42)                     // Returns the actual type object
let collection_size = len(list)             // Length of collection
let is_instance = isinstance(value, type)   // Check if value is instance of type

// Type conversion functions
let str_val = str(42)                       // Convert to string: "42"
let int_val = int("42")                     // Convert to int: 42
let float_val = float("3.14")               // Convert to float: 3.14
let bool_val = bool("true")                 // Convert to boolean: true
let list_val = list((1, 2, 3))              // Convert to list: [1, 2, 3]
let tuple_val = tuple([1, 2, 3])            // Convert to tuple: (1, 2, 3)
let set_val = set([1, 2, 2, 3])             // Convert to set: {1, 2, 3}
let dict_val = dict([["a", 1], ["b", 2]])   // Convert to dict: {"a": 1, "b": 2}

// JSON functions
let json_str = JSON.stringify(obj)          // Convert object to JSON string
let parsed = JSON.parse(json_str)           // Parse JSON string to object
let formatted = JSON.pretty(obj)            // Format object as readable JSON

// System functions
exit(0)                                     // Exit program with code
sleep(milliseconds)                         // Pause execution
getEnv("PATH")                              // Get environment variable
setEnv("DEBUG", "true")                     // Set environment variable
```

### Math Functions

```ore
abs(-10)                            // 10 (absolute value)
min(5, 10)                          // 5 (minimum value)
max(5, 10)                          // 10 (maximum value)
round(3.7)                          // 4 (round to nearest integer)
floor(3.7)                          // 3 (round down)
ceil(3.2)                           // 4 (round up)
trunc(3.7)                          // 3 (truncate decimal part)
random()                            // Random float between 0 and 1
randomInt(1, 10)                    // Random integer between 1 and 10
sin(3.14)                           // Sine
cos(3.14)                           // Cosine
tan(3.14)                           // Tangent
asin(0.5)                           // Arc sine
acos(0.5)                           // Arc cosine
atan(1.0)                           // Arc tangent
sqrt(16)                            // 4 (square root)
cbrt(27)                            // 3 (cube root)
pow(2, 3)                           // 8 (same as 2**3)
log(100)                            // Natural logarithm
log10(100)                          // 2 (base-10 logarithm)
log2(8)                             // 3 (base-2 logarithm)
exp(1)                              // e^1 (exponential)
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
name.find(/\w+/)                  // Find using regex
name.findAll(/a/g)                // Find all occurrences with regex
name.match(/[a-z]+/)              // Match pattern

// Extracting
name.charAt(0)                    // "d"
name.substring(0, 5)              // "dhruv"
name.slice(6)                     // "rawat"

// Formatting
"{} is {}".format(name, "cool")   // "dhruv rawat is cool"
name.padStart(15, "-")            // "----dhruv rawat"
name.padEnd(15, "-")              // "dhruv rawat----"
name.repeat(2)                    // "dhruv rawatdhruv rawat"
```

### Array/List Functions

```ore
// Create arrays
let arr = [1, 2, 3, 4, 5]
let filled = Array.fill(5, 0)             // [0, 0, 0, 0, 0]
let ranged = Array.range(1, 6)            // [1, 2, 3, 4, 5]
let fromString = Array.fromString("abc")  // ['a', 'b', 'c']
let spreadCopy = [...arr]                 // Copy array with spread

// Array operations
array.at(-1)                      // Get element with support for negative indices
array.includes(value)             // Check if array includes value (alias for contains)
array.findLast(predicate)         // Find last element that matches predicate
array.findLastIndex(predicate)    // Find index of last matching element
array.with(index, value)          // Return new array with value at index
array.toSorted()                  // Get sorted copy (same as sorted)
array.toReversed()                // Get reversed copy
array.toSpliced(index, count)     // Get copy with elements removed
array.concat(otherArray)          // Combine arrays

// Advanced array methods
array.zip(otherArray)             // Combine corresponding elements
array.partition(predicate)        // Split into arrays of matching/non-matching
array.unique()                    // Get unique elements (same as distinct)
array.shuffle()                   // Randomize array order
array.sample()                    // Get random element
array.rotate(n)                   // Rotate elements by n positions
array.binarySearch(value)         // Binary search (on sorted array)
```

### Date and Time Functions

```ore
// Creating dates
let now = Date.now()                          // Current date and time
let date = Date.parse("2023-01-15")           // Parse from string
let specificDate = Date.create(2023, 1, 15)   // Year, month, day

// Date components
date.year                                     // Get year
date.month                                    // Get month
date.day                                      // Get day
date.hour                                     // Get hour
date.minute                                   // Get minute
date.second                                   // Get second
date.weekday                                  // Get day of week

// Formatting dates
date.format("YYYY-MM-DD")                     // Format as string
date.toISOString()                            // ISO format string
date.toUTCString()                            // UTC format string

// Date operations
date.add({days: 5, hours: 2})                 // Add time units
date.subtract({months: 1})                    // Subtract time units
date.startOf("month")                         // Beginning of month
date.endOf("day")                             // End of day
Date.diff(date1, date2, "days")               // Difference in days
```

### Regular Expression Functions

```ore
// Creating regular expressions
let regex = /pattern/flags
let regexObj = RegExp("pattern", "flags")

// Regex methods
regex.test("string")                         // Test if pattern matches
regex.exec("string")                         // Execute search, return match info
"string".match(regex)                        // Get matches
"string".replace(regex, replacement)         // Replace matches
"string".split(regex)                        // Split string by pattern

// Regex flags
// i - case insensitive
// g - global (all matches)
// m - multiline
// s - dotall (dot matches newlines)
```

### Cryptography and Hashing

```ore
// Hashing functions
let md5 = Crypto.md5("string")                // MD5 hash
let sha256 = Crypto.sha256("string")          // SHA-256 hash
let hash = Crypto.hash("string", "algorithm") // Generic hash

// Encoding/decoding
let base64 = Crypto.encodeBase64("string")    // Base64 encode
let decoded = Crypto.decodeBase64(base64)     // Base64 decode
let hex = Crypto.encodeHex(bytes)             // Hex encode
let fromHex = Crypto.decodeHex(hex)           // Hex decode

// Encryption/decryption
let encrypted = Crypto.encrypt(data, key, iv) // Encrypt data
let decrypted = Crypto.decrypt(encrypted, key, iv) // Decrypt data
```

## Collection Examples

### Practical List Examples

```ore
// Task: Process a list of student scores and find those who passed
let scores = [85, 42, 97, 65, 55, 73, 31, 79, 60]
let passingThreshold = 60

// Find passing scores and corresponding students
let studentNames = ["Alice", "Bob", "Charlie", "David", "Eve", "Frank", "Grace", "Hannah", "Ivy"]
let passedStudents = []

for (score, i in scores) {
    if (score >= passingThreshold) {
        passedStudents.push({
            name: studentNames[i],
            score: score
        })
    }
}

// Sort passed students by score (descending)
passedStudents.sort((a, b) => b.score - a.score)

// Print results
println("Passing students:")
for (student, i in passedStudents) {
    println(f"{i+1}. {student.name}: {student.score}")
}
```

### Practical Tuple Examples

```ore
// Task: Working with coordinate points (immutable)
let points = [
    (2, 3),    // Point 1 (x, y)
    (5, 1),    // Point 2
    (7, 8),    // Point 3
    (3, 7)     // Point 4
]

// Calculate distance from origin for each point
let distances = points.map(point => {
    let (x, y) = point  // Tuple destructuring
    return math.sqrt(x*x + y*y)
})

// Sort points by distance from origin
let sortedByDistance = [...points]  // Create a copy
sortedByDistance.sort((p1, p2) => {
    let d1 = math.sqrt(p1[0]*p1[0] + p1[1]*p1[1])
    let d2 = math.sqrt(p2[0]*p2[0] + p2[1]*p2[1])
    return d1 - d2
})

// Point to string utility function
fn pointToString(point) {
    let (x, y) = point
    return f"({x}, {y})"
}

// Print results
println("Points sorted by distance from origin:")
for (point, i in sortedByDistance) {
    let (x, y) = point
    let dist = math.sqrt(x*x + y*y)
    println(f"{i+1}. {pointToString(point)} - Distance: {dist.toFixed(2)}")
}
```

### Practical Dictionary Examples

```ore
// Task: Analyze a text and count word frequencies
let text = "the quick brown fox jumps over the lazy dog the fox was quick"
let words = text.toLowerCase().split(" ")
let wordCounts = {}

// Count word frequencies
for (word in words) {
    if (wordCounts.hasKey(word)) {
        wordCounts[word] += 1
    } else {
        wordCounts[word] = 1
    }
}

// Alternative using get with default
for (word in words) {
    wordCounts[word] = wordCounts.get(word, 0) + 1
}

// Sort words by frequency (descending)
let sortedWords = wordCounts.entries().sort((a, b) => b[1] - a[1])

// Print results
println("Word frequency:")
for (entry, i in sortedWords) {
    let [word, count] = entry
    println(f"{i+1}. '{word}': {count}")
}
```

### Practical Set Examples

```ore
// Task: Find common elements in multiple datasets
let datasetA = {1, 3, 5, 7, 9, 11, 13, 15}
let datasetB = {3, 6, 9, 12, 15, 18}
let datasetC = {2, 3, 5, 7, 11, 13, 15, 17, 19}

// Find elements common to all three datasets
let commonElements = datasetA.intersection(datasetB).intersection(datasetC)

// Find elements in A and B but not in C
let inAandBnotC = datasetA.intersection(datasetB).difference(datasetC)

// Find elements unique to each dataset
let uniqueToA = datasetA.difference(datasetB.union(datasetC))
let uniqueToB = datasetB.difference(datasetA.union(datasetC))
let uniqueToC = datasetC.difference(datasetA.union(datasetB))

// Print results
println(f"Common to all three: {commonElements}")
println(f"In A and B but not C: {inAandBnotC}")
println(f"Unique to A: {uniqueToA}")
println(f"Unique to B: {uniqueToB}")
println(f"Unique to C: {uniqueToC}")
```

### Practical FrozenSet Examples

```ore
// Task: Use immutable sets as dictionary keys
let employeesByDepartment = {
    frozenset({"Engineering", "Development", "Programming"}): [
        "Alice Johnson", 
        "Bob Smith",
        "Charlie Davis"
    ],
    frozenset({"Marketing", "Sales", "Communication"}): [
        "David Wilson",
        "Eve Brown"
    ],
    frozenset({"HR", "Recruitment", "People Operations"}): [
        "Frank Miller"
    ]
}

// Function to find department by tag
fn findDepartmentByTag(tag) {
    for (depTags, employees in employeesByDepartment) {
        if (depTags.contains(tag)) {
            return employees
        }
    }
    return []
}

// Print results
println("Employees in Development department:")
for (emp in findDepartmentByTag("Development")) {
    println(f"- {emp}")
}

println("\nEmployees in Marketing department:")
for (emp in findDepartmentByTag("Marketing")) {
    println(f"- {emp}")
}
```

## Async/Await

### Async Functions

```ore
// Define an async function
async fn fetchData(url: string): string {
    // Simulate HTTP request
    await sleep(100)  // Wait for 100ms
    return "Data from ${url}"
}

// Use async/await in another function
async fn processData() {
    print("Fetching data...")
    let data = await fetchData("https://api.example.com")
    print("Received: ${data}")
    return data
}
```

### Error Handling with Async/Await

```ore
async fn fetchWithErrorHandling(url: string): string {
    try {
        let response = await fetch(url)
        
        if (!response.ok) {
            throw "HTTP Error: ${response.status}"
        }
        
        return await response.text()
    } catch (err) {
        print("Error fetching data: ${err}")
        return ""
    }
}
```

### Parallel Execution

```ore
async fn fetchMultiple() {
    // Execute multiple async operations in parallel
    let data1 = fetchData("https://api.example.com/endpoint1")
    let data2 = fetchData("https://api.example.com/endpoint2")
    
    // Wait for both to complete
    let result1 = await data1
    let result2 = await data2
    
    print("Data 1: ${result1}")
    print("Data 2: ${result2}")
}
```

## Examples

### Basic Program

```ore
fn main(argc, args) {
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

fn main(argc, args) {
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

fn main(argc, args) {
    processLogFile("application.log")
}
```

### Command Line Tool

```ore
fn main(argc, args) {
    // argc contains the number of command line arguments
    // args is a list of all arguments, with args[0] being the program name
    
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

### Async HTTP Request

```ore
async fn main(argc, args) {
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

## Collections: Lists

### List Creation

```ore
let numbers = [1, 2, 3, 4, 5]           // Basic list
let mixed = [1, "two", 3.0, true]       // Heterogeneous list
let empty_list = []                     // Empty list
let typed_list: int[] = [1, 2, 3]       // Typed list
let from_range = list(1..5)             // Create from range
let from_set = list({1, 2, 3})          // Create from set
```

### List Indexing and Slicing

```ore
let first = numbers[0]                  // 1
let last = numbers[-1]                  // 5
let sub_list = numbers[1..3]            // [2, 3, 4]
let every_other = numbers[::2]          // [1, 3, 5]
let reversed_list = numbers[::-1]       // [5, 4, 3, 2, 1]
numbers[1] = 10                         // Modify: [1, 10, 3, 4, 5]
```

### List Operations

```ore
numbers.push(6)                         // Add to end: [1, 2, 3, 4, 5, 6]
numbers.pushAll([7, 8, 9])              // Add multiple: [1, 2, 3, 4, 5, 6, 7, 8, 9]
let popped = numbers.pop()              // Remove from end, returns value
numbers.insert(0, 0)                    // Insert at position: [0, 1, 2, 3, 4, 5]
numbers.insertAll(2, [10, 11])          // Insert multiple items at position
numbers.remove(3)                       // Remove by value (first occurrence)
numbers.removeAll(3)                    // Remove all occurrences of value
numbers.removeAt(2)                     // Remove by index
numbers.clear()                         // Remove all elements
let sorted_list = numbers.sorted()      // Returns sorted copy
let sorted_custom = numbers.sorted((a, b) => b - a)  // Custom sort (descending)
numbers.sort()                          // Sorts in place
numbers.reverse()                       // Reverse in place
let joined_str = numbers.join(", ")     // "0, 1, 4, 5"
```

### List Methods

```ore
let has_value = numbers.contains(4)     // true
let index = numbers.indexOf(4)          // 2
let last_index = numbers.lastIndexOf(4) // Find last occurrence
let is_empty = numbers.isEmpty()        // false
let size = numbers.length               // 4
let deep_copy = numbers.clone()         // Create a deep copy
let shallow_copy = numbers.slice()      // Create a shallow copy
let flattened = [[1,2],[3,4]].flatten() // [1,2,3,4]
```

### Functional Operations

```ore
let doubled = numbers.map(x => x * 2)   // [0, 2, 8, 10]
let filtered = numbers.filter(x => x > 2) // [4, 5]
let sum_val = numbers.reduce((acc, x) => acc + x, 0) // 10
let flat_mapped = numbers.flatMap(x => [x, x*2])    // [1, 2, 2, 4, 3, 6, ...]
numbers.forEach(x => print(x))          // Prints each item
let found = numbers.find(x => x > 10)   // First element matching condition or null
let found_index = numbers.findIndex(x => x > 10)  // Index of first matching element or -1
let all_match = numbers.all(x => x > 0)           // true if all elements satisfy condition
let any_match = numbers.any(x => x > 10)          // true if any element satisfies condition
let chunk_size_2 = numbers.chunk(2)     // [[1,2], [3,4], [5]]
let grouped = numbers.groupBy(x => x % 2)  // {0: [2,4], 1: [1,3,5]}
```

### Statistical Methods

```ore
let sum = numbers.sum()                 // 10
let avg = numbers.average()             // 2.5
let min_val = numbers.min()             // 0
let max_val = numbers.max()             // 5
let count_val = numbers.count(x => x > 2) // 2
let product = numbers.product()         // Product of all elements
let distinct = [1,2,2,3,3,3].distinct() // [1,2,3]
```

### List Comprehensions

```ore
let evens = [x for x in numbers if x % 2 == 0]
let squares = [x*x for x in 1..10]  // Using range
let matrix = [[i*j for i in 1..3] for j in 1..3]  // Nested comprehension
let zip_result = [(a,b) for a,b in zip(list1, list2)]  // Zip comprehension
```

## Collections: Tuples

### Tuple Creation

```ore
let tuple = (1, "hello", 3.14)          // Basic tuple
let empty_tuple = ()                    // Empty tuple
let single_item_tuple = (1,)            // Note the comma
let nested_tuple = (1, (2, 3), 4)       // Nested tuple
let from_list = tuple([1, 2, 3])        // Create from list
let typed_tuple: (int, string) = (1, "hello")  // Typed tuple
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
let tuple_count = tuple.count("hello")  // 1 (count occurrences)
let has_hello = tuple.contains("hello") // true
let hello_index = tuple.indexOf("hello") // 1
let as_list = tuple.toList()            // Convert to list
let tuple_string = tuple.toString()     // String representation
```

### Creating New Tuples (Immutable)

```ore
let extended_tuple = tuple.append(42)   // (1, "hello", 3.14, 42)
let combined_tuple = tuple.concat((5, 6)) // (1, "hello", 3.14, 5, 6)
let modified_tuple = tuple.replace(1, "world") // (1, "world", 3.14)
let without_item = tuple.remove("hello") // (1, 3.14)
let element_slice = tuple.slice(0, 2)   // (1, "hello")
```

### Tuple Unpacking

```ore
let (x, y, z) = tuple                   // x=1, y="hello", z=3.14
let (first, *rest) = (1, 2, 3, 4)       // first=1, rest=[2,3,4]
let (head, *middle, tail) = (1, 2, 3, 4) // head=1, middle=[2,3], tail=4
```

## Collections: Dictionaries

### Dictionary Creation

```ore
let user = {"name": "John", "age": 30}  // Basic dictionary
let empty_dict = {}                     // Empty dictionary
let from_entries = dict([("a", 1), ("b", 2)])  // From key-value pairs
let from_keys = dict.fromKeys(["a", "b"], 0)  // {"a": 0, "b": 0}
let typed_dict: Dictionary<string, int> = {"a": 1, "b": 2}  // Typed dictionary
```

### Dictionary Access

```ore
let user_name = user["name"]            // "John"
let user_age = user.age                 // 30 (dot notation)
let safe_get = user.get("email", "default@example.com")  // With default value
let multi_get = user.getMultiple(["name", "age"])  // Get multiple keys at once
```

### Dictionary Operations

```ore
user["email"] = "john@example.com"      // Add or update value
user.set("phone", "555-1234")           // Alternative way to set
user.update({"city": "New York", "country": "USA"})  // Update with multiple entries
user.remove("age")                      // Remove key
user.pop("email")                       // Remove and return value
user.popItem()                          // Remove and return last key-value pair
let has_email = user.hasKey("email")    // true
let has_value = user.hasValue("John")   // true
let all_keys = user.keys()              // ["name", "email"]
let all_values = user.values()          // ["John", "john@example.com"]
let all_entries = user.entries()        // [["name", "John"], ["email", "john@example.com"]]
```

### Dictionary Methods

```ore
let dict_size = user.size()             // 2
let dict_len = user.length              // 2 (alternative)
let is_dict_empty = user.isEmpty()      // false
user.clear()                            // Remove all entries
let merged = user.merge({"city": "New York"}) // Combine dictionaries
let deep_copy = user.clone()            // Deep copy
let flipped = user.flip()               // Swap keys and values
let filtered = user.filter((k, v) => v is string)  // Filter dictionary
let mapped = user.map((k, v) => v.toUpper() if v is string else v)  // Transform values
let deep_get = user.deepGet("contact.email", null)  // Get nested property or default
```

## Collections: Sets

### Set Creation

```ore
let unique_numbers = {1, 2, 3, 4, 5}    // Basic set
let empty_set = set()                   // Empty set (note: {} creates an empty dictionary)
let converted_set = set([1, 2, 2, 3])   // {1, 2, 3}
let from_string = set("hello")          // {'h', 'e', 'l', 'o'}
let typed_set: Set<int> = {1, 2, 3}     // Typed set
```

### Set Operations

```ore
unique_numbers.add(6)                   // {1, 2, 3, 4, 5, 6}
unique_numbers.addAll([7, 8, 9])        // Add multiple elements
unique_numbers.remove(3)                // {1, 2, 4, 5, 6}
unique_numbers.discard(10)              // Remove if present (no error if missing)
unique_numbers.pop()                    // Remove and return an arbitrary element
unique_numbers.clear()                  // Remove all elements
let has_five = unique_numbers.contains(5) // true
```

### Set Methods

```ore
let set_size = unique_numbers.size()    // 5
let set_len = unique_numbers.length     // 5 (alternative)
let is_set_empty = unique_numbers.isEmpty() // false
let as_list = unique_numbers.toList()   // Convert to list
let as_tuple = unique_numbers.toTuple() // Convert to tuple
let as_sorted = unique_numbers.sorted() // Get sorted list of elements
let max_value = unique_numbers.max()    // Largest element
let min_value = unique_numbers.min()    // Smallest element
```

### Set Algebra

```ore
let set1 = {1, 2, 3, 4, 5}
let set2 = {4, 5, 6, 7}
let union_set = set1.union(set2)        // {1, 2, 3, 4, 5, 6, 7}
let intersection_set = set1.intersection(set2) // {4, 5}
let difference_set = set1.difference(set2) // {1, 2, 3}
let symmetric_diff = set1.symmetricDifference(set2) // {1, 2, 3, 6, 7}
let is_subset = {1, 2}.isSubset(set1)   // true
let is_superset = set1.isSuperset({1, 2}) // true
let is_disjoint = set1.isDisjoint({6, 7, 8}) // true
set1.update(set2)                       // Modify set1 in place to include set2 elements
set1.intersectionUpdate(set2)           // Modify set1 to keep only elements in set2
set1.differenceUpdate(set2)             // Modify set1 to remove elements found in set2
set1.symmetricDifferenceUpdate(set2)    // Update set1 with symmetric difference
```

### Frozen Sets (Immutable)

```ore
let immutable_set = frozenset({1, 2, 3})  // Create a frozen set
let from_list = frozenset([1, 2, 3, 1])   // Create from list, duplicates removed
let from_set = frozenset(set1)            // Create from another set
let empty_frozen = frozenset()            // Empty frozen set

// Frozen sets have the same query methods as regular sets
let has_item = immutable_set.contains(2)  // true
let is_subset = immutable_set.isSubset({1, 2, 3, 4})  // true

// Creating new frozen sets from operations (doesn't modify original)
let combined = immutable_set.union({3, 4, 5})  // frozenset({1, 2, 3, 4, 5})
let common = immutable_set.intersection({2, 3, 4})  // frozenset({2, 3})

// Frozen sets can be used as dictionary keys (regular sets cannot)
let set_keys = { 
    immutable_set: "value1",
    frozenset({4, 5, 6}): "value2"
} 
```

## Collection Types Comparison

| Feature                | List           | Tuple           | Dictionary    | Set            | Frozen Set     |
|------------------------|----------------|-----------------|---------------|----------------|----------------|
| **Mutability**         | Mutable        | Immutable       | Mutable       | Mutable        | Immutable      |
| **Ordered**            | Yes            | Yes             | No            | No             | No             |
| **Indexable**          | Yes (by index) | Yes (by index)  | Yes (by key)  | No             | No             |
| **Heterogeneous**      | Yes            | Yes             | Keys: Yes<br>Values: Yes | Yes | Yes            |
| **Duplicates**         | Allowed        | Allowed         | No (unique keys) | No (unique elements) | No (unique elements) |
| **Hashable (as key)**  | No             | Yes             | No            | No             | Yes            |
| **Common Use Cases**   | Sequences, ordered data, iteration | Fixed collections, return multiple values | Key-value associations, lookups | Unique items, membership testing | Immutable set operations, dictionary keys |
| **Memory Usage**       | Medium         | Low             | High          | Medium         | Medium         |
| **Literal Syntax**     | [1, 2, 3]      | (1, 2, 3)       | {"a": 1}      | {1, 2, 3}      | frozenset({1, 2, 3}) |

## Operators

```ore
// ... existing code ...
```

---

Created by Dhruv Rawat
