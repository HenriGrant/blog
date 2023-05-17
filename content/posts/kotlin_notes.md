---
title: "Kotlin Notes"
date: 2023-05-14T15:00:28-04:00
type: "post"
showTableOfContents: true
tags: ["Kotlin", "notes"]
---

# Kotlin
## Variables

Type    Bits      Value range 

Byte    8 bits    -128 to 127 

Short   16 bits   -32768 to 32767 

Int     32  bits  -2147483648 to 2147483647 

Long    64 bits   -huge to (huge - 1)


Every numeric type has the following conversion functions: 

` toByte() `, ` toShort() `, ` toInt() `, ` toLong() `, ` toFloat() ` and toDouble().



` var ` = variable, ` val ` = constant

for printing, ` println("$var") ` the ` $ ` tells Kotlin that it is a variable.

` var hugeNumber = 6L ` -- Long
` var binNum = 0b10 ` -- binary number
` var floatNum = 129.5F ` -- float
` var doubleNum = 123.0 ` double
` var letter = 'D' ` char
` var name = "Fido ` string
```Kotlin
var smallNum: Short // declare a short var
var tinyNum: Byte   // declare a Byte var
var z: Short = 6    // declare a short AND assign value
```

## Printing

` print() ` prints on the same line, while ` println() ` prints on a new line

## Expression Style If

while this is best practice, for some reason Kotlin can change this into an expression. I hear it is recommended to NOT put IF statements inside PRINTLN, because it READS BAD.
```Kotlin
if (x > y) {

    println("x is greater than y")

} else {

    println("x is not greater than y")

}
```
can be rewritten as

```Kotlin
println(if (x > y) "x is greater than y" else "x is not greater than y")
```

"Unlike the case of some other programming languages, Kotlin's if is an expression, not a statement. This means it can return a value as a result of computations. The result must be the last expression in the body." - hyperskill kotlin core thing.


## Arrays

```Kotlin
var myArray = arrayOf(1, 2, 3) 
println(myArray[0])
myArray.size // size of array
```

You can modify one of the array's values later too.

for example:

```Kotlin

var stringArray = arrayOf("Hi there", "Hello", "Goodbye")

stringArray[2] = "Hey"

```

Goodbye would be turned into Hey
You cannot change the type, though.

explicitly define array's type:

` var myArray: Array<Byte> = arrayOf(1, 2, 3) `


you can have a VAR array reference a new object:

```Kotlin
var myArray = arrayOf(1, 2, 3)

myArray = arrayOf(7, 9)
```

for a VAL array, you can only reference the same array, but you can change the individual values of the array.





## Strings

You can also use String templates to refer to an object’s properties, or call its functions. In this case, you enclose the expression in curly braces.

Griffiths, Dawn; Griffiths, David. Head First Kotlin (p. 142). O'Reilly Media. Kindle Edition. 

` var arraySize = "myArray has ${myArray.size} items `


## Functions

Func with no return value:
```Kotlin
fun printSum(int1: Int, int2: Int): Unit {
    val result = int1 + int2
    println(result)
 } 
```

you use unit to tell Kotlin that the function has no return value.

### single expression functions:
` fun sum(a: Int, b: Int): Int = a + b `
` fun sum(a: Int, b: Int) = a + b `

### Idiom:
These are the same:
```Kotlin
fun theAnswer() = 42   // short and clear
...
fun theAnswer(): Int { // equivalent common function
    return 42
}
```


## When
when is basically a C++ switch—case
```Kotlin
val number = 5

when (number) {
    1 -> println("One")
    2 -> println("Two")
    3 -> println("Three")
    4 -> println("Four")
    else -> println("Number is greater than four")
}

```

When can also be an expression:

```Kotlin
val number = 3
val message = when (number) {
    1 -> "One"
    2 -> "Two"
    3 -> "Three"
    4 -> "Four"
    else -> "Number is greater than four"
}

println(message) // Output: Three
```

When can also be used with ranges and conditions:


```Kotlin
val number = 15

when {
    number < 0 -> println("Negative number")
    number in 1..10 -> println("Number between 1 and 10")
    number % 2 == 0 -> println("Even number")
    else -> println("Odd number greater than 10")
}
```

## For loop

` until`, `downTo ` - will exclude the number given, but go until that number. either up or down


```Kotlin
for (x in 1..10) {
    // your code goes here
}
```

^ will include ten, while using ` until ` will not

## Init

If you need to initialize a property to something more complex than a simple expression, or if there’s extra code you want to run when each object is created, you can use one or more initializer blocks. Initializer blocks are executed when the object is initialized, immediately after the constructor is called, and they’re prefixed with the init keyword.


```Kotlin

init {
    println("Dog $name has been created.")
}

```

**you must initialize properties before you try to use them.**

## Empty Constructor

you can create a class without parameters.

```Kotlin

class Duck {
    
    fun quack() {
        println("Quack! Quack! Quack!")
    }
}

```
When you define a class with no constructor, the compiler secretly writes one for you. It adds an empty constructor (a constructor with no parameters) to your compiled code. (Head First)

## Getters and Setters (Validation Property Values)

If you want to tweak a property’s return value, or validate a value before it gets assigned to a property, you can write your own getters and setters. (Head First)

Also called accessors and mutators.

```Kotlin

val weightInKgs: Double
    get() = weight / 2.2

```

example of a setter:

```Kotlin

var weight = weight_param
    set(value) {
        if (value > 0) field = value
    }

```

this setter makes sure the number is positive.

you use field to prevent infinite loops.

## Recursion!!!

```Kotlin
// will add up numbers from the inputted number all the way to one. for example, if the user inputs 5,
// it will add up 5+4+3+2+1=15
// recursion function instead of for loop, fewer lines of code.
fun sumUp(num: Int): Int {
    if (num==1) return num else return num + sumUp(num - 1)
}

fun main(args: Array<String>) {
    var userInt: Int
    println("Please input an integer!")
    userInt= readln().toInt()
    println(sumUp(userInt))
}

```
this is a working example of recursion


# References:

https://hyperskill.org/tracks/18

Griffiths, Dawn; Griffiths, David. Head First Kotlin. O'Reilly Media. Kindle Edition. 

Documentation:

https://kotlinlang.org/docs/home.html
