<div align=center>

# [Hello World](https://github.com/ayohana/HelloWorld-Kotlin)

#### Basic Console App in Kotlin, 07.21.2020

#### By [**Adela Darmansyah**](https://github.com/ayohana/)

![GitHub last commit (branch)](https://img.shields.io/github/last-commit/ayohana/HelloWorld-Kotlin/master?color=%23DE98B2&style=for-the-badge) ![GitHub language count](https://img.shields.io/github/languages/count/ayohana/HelloWorld-Kotlin?color=%23DE98B2&style=for-the-badge) ![GitHub top language](https://img.shields.io/github/languages/top/ayohana/HelloWorld-Kotlin?color=%23DE98B2&style=for-the-badge)

</div>

## About

**A very basic console app that prints "Hello World!" using Kotlin.**

## Notes on Kotlin

### What is Kotlin?

* Kotlin is a cross-platform, statically typed, general-purpose programming language with type inference.
* Kotlin is an effective, modern programming language developed by JetBrains.
* **Cross-platform**
    * Knowledge of Kotlin allows developers to write mobile, server-side and desktop applications, as well as useful frameworks, and libraries.
    * A programming language for JVM (Java Virtual Machine), Android, browsers (JavaScript), and developers can compile Kotlin into native binaries, and can be run under Windows, Linux, iOS and MacOS.
* **General-purpose**
    * As a general-purpose language, it can be used in many spheres such as the financial service industry, telecommunications, embedded systems, medicine, development tools (like IntelliJ IDEA), and so on.
* **Type-inference**
    * Type inference refers to the automatic detection of the data type of an expression in a programming language.
* Kotlin is designed as a **pragmatic language**, which means, its main purpose is to solve real-world problems rather than completing research purposes.
* It is also important that **Kotlin supports multiple programming paradigms**, such as imperative programming, object-oriented programming, generic programming, functional programming, and more. 
* Kotlin is **a tool-friendly language**, which means all popular development tools such as IntelliJ IDEA, Eclipse, and Android Studio are compatible with it.

### Short History

* In July 2011, JetBrains unveiled the Kotlin Project, a new language for the Java Platform, which had been in development for a year. The name comes from Kotlin Island, near St. Petersburg, Russia. The primary goal of this project was to provide a safer and more concise alternative to Java in all the contexts where Java is currently used. 
* In 2016, the first official stable version was released (Kotlin v1.0). The developer community was already interested in using this language, especially on Android.

### Basic Literals

1. **Integer numbers**
    * Here are several examples of valid integer number literals separated by commas: `0`, `1`, `2`, `10`, `11`, `100`.
    * If an integer value contains a lot of digits, we can add **underscores** to divide the digits into blocks to make this number more readable: for example, `1_000_000` is easier to read than the same value written as `1000000`.
    
2. **Characters**
    * A single character can represent **a digit, a letter, or another symbol.**
    * To write a single character, we wrap a symbol in **single quotes** as follows: `'A'`, `'B'`, `'C'`, `'x'`, `'y'`, `'z'`, `'0'`, `'1'`, `'2'`, `'9'`.
    * A character **cannot** include two or more digits or letters, because it represents **a single symbol.**
    * The next two examples are _**incorrect**_: 'abc', '543' because these literals have too many characters.

3. **Strings**
    * Strings represent text information such as a text of an advertisement, an address of a web page, or a login to a website.
    * A string is a sequence of any individual characters.
    * To write strings we wrap characters in **double-quotes** instead of single ones.
    * Here are some valid examples: `"text"`, `"I want to learn Kotlin"`, `"123456"`, `"e-mail@gmail.com"`
    * A string can also contain only a single character, like `"A"`.
    * Do not confuse it with a character such as `'A'`, which is **not** a string.
    
#### Recap

Do not confuse these literals:

* `123` is an integer number, `"123"` is a string;
* `'A'` is a character, `"A"` is a string;
* `'1'` is a character, `1` is an integer number.

### Higher-Order Functions and Lambdas

* Kotlin functions are **first-class**, which means that they can be stored in variables and data structures, passed as arguments to and returned from other higher-order functions.
* You can operate with functions in any way that is possible for other non-function values.
* To facilitate this, Kotlin, as a **statically typed** programming language, uses a family of **function types** to represent functions and provides a set of specialized language constructs, such as lambda expressions.

#### Function Types

* Kotlin uses a family of function types like `(Int) -> String` for declarations that deal with functions: `val onClick: () -> Unit = ....`
* These types have a special notation that corresponds to the signatures of the functions, i.e. their parameters and return values:
    * **All function types have a parenthesized parameter types list and a return type:**
        * `(A, B) -> C` denotes _a type_ that represents functions taking two arguments of types A and B and returning a value of type C.
        * The parameter types list may be empty, as in `() -> A`.
        * The `Unit` return type cannot be omitted.
    * Function types can optionally have an additional **receiver** type, which is **specified before a dot in the notation**:
        * The type `A.(B) -> C` represents functions that can be called on a receiver object of `A` with a parameter of `B` and return a value of `C`.
        * Function literals with receiver are often used along with these types.
    * **Suspending functions** belong to function types of a special kind, which have a `suspend` modifier in the notation, such as `suspend () -> Unit` or `suspend A.(B) -> C`.
* The function type notation can _optionally_ include names for the function parameters: `(x: Int, y: Int) -> Point`. These names can be used for documenting the meaning of the parameters.

#### Higher Order Functions

* A **higher-order function** is a function that takes functions as parameters, or returns a function.
* In functional programming, **fold** (also termed reduce, accumulate, aggregate, compress, or inject) refers to **a family of higher-order functions** that analyze a recursive data structure and through use of a given combining operation, recombine the results of recursively processing its constituent parts, building up a return value.

#### `it` : implicit name of a single parameter

* It's very common that a lambda expression has only **one parameter**.
* It is **allowed** not to declare the only parameter and omit `->`.
* The parameter will be implicitly declared under the name `it`:
    ``````
    ints.filter { it > 0 }
    // this literal is of type '(it: Int) -> Boolean'
    ``````

### Nullable and Non-Null Types

In Kotlin, the type system distinguishes between references that can hold `null` (**nullable** references) and those that cannot (**non-null** references). For example, a regular variable of type `String` cannot hold `null`:
``````
var a: String = "abc" // Regular initialization means non-null by default
a = null // compilation error // Throws NPE (NullPointerException)
``````

**To allow nulls**, we can declare a variable as **nullable** string, written `String?`:
``````
var b: String? = "abc" // can be set null
b = null // ok
print(b)
``````

#### Safe (Null) Calls

Use the **safe call operator**, written `?.` :
``````
val a = "Kotlin"
val b: String? = null
println(b?.length)
println(a?.length)
``````
This returns `b.length` if `b` is not null, and null otherwise. The type of this expression is `Int?`.


**Safe calls are useful in chains.** For example, if Bob, an Employee, may be assigned to a Department (or not), that in turn may have another Employee as a department head, then to obtain the name of Bob's department head (if any), we write the following:
``````
bob?.department?.head?.name
``````
Such a chain returns `null` if _any_ of the properties in it is null.


A safe call can also be placed on the **left side of an assignment**. Then, if one of the receivers in the safe calls chain is null, the assignment is skipped, and the expression on the right is not evaluated at all:
``````
// If either `person` or `person.department` is null, the function is not called:
person?.department?.head = managersPool.getManager()
``````

#### Elvis Operator

When we have a nullable reference `b`, we can say "if `b` is not null, use it, otherwise use some non-null value":
``````
val l: Int = if (b != null) b.length else -1
``````
Along with the complete `if`-expression, this can be expressed with the **Elvis operator**, written `?:` :
``````
val l = b?.length ?: -1
``````
* **If the expression to the left of `?:` is not null, the elvis operator returns it, otherwise it returns the expression to the right.**
* Note that the right-hand side expression is evaluated only if the left-hand side is null.

Note that, since `throw` and `return` are expressions in Kotlin, they can also be used on the right hand side of the elvis operator. This can be very handy, for example, for checking function arguments:
``````
fun foo(node: Node): String? {
    val parent = node.getParent() ?: return null
    val name = node.getName() ?: throw IllegalArgumentException("name expected")
    // ...
}
``````

### The Nothing Type

**The type of the `throw` expression is the special type `Nothing`.** The type has no values and is used to mark code locations that can never be reached. In your own code, you can use `Nothing` to mark a function that never returns:
``````
fun fail(message: String): Nothing {
    throw IllegalArgumentException(message)
}
``````

When you call this function, the compiler will know that the execution doesn't continue beyond the call:
``````
val s = person.name ?: fail("Name required")
println(s)     // 's' is known to be initialized at this point
``````

Another case where you may encounter this type is **type inference**. **The nullable variant of this type, `Nothing?`, has exactly one possible value, which is `null`.** If you use `null` to initialize a value of an inferred type and there's no other information that can be used to determine a more specific type, the compiler will infer the `Nothing?` type:
``````
val x = null           // 'x' has type `Nothing?`
val l = listOf(null)   // 'l' has type `List<Nothing?>
``````


## Notes on IntelliJ

### Keyboard Shortcuts

* `Alt + J` : Selects multiple words
* `Alt + 1` : Shows/hides Project Structure navigation bar
* `Alt + F12` : Shows/hides Terminal

## Known Bugs

No known bugs at this time.

## Technologies Used

* [Kotlin](https://kotlinlang.org/)
* [IntelliJ IDEA](https://www.jetbrains.com/idea/download/#section=windows)
* Markdown

## Learning Resources

* [Getting Started with Kotlin](https://kotlinlang.org/docs/tutorials/getting-started.html)
* [Basic Console App Tutorial in Kotlin](https://kotlinlang.org/docs/tutorials/jvm-get-started.html)
* [Geting Started with IntelliJ: Setting up the environment](https://kotlinlang.org/docs/tutorials/jvm-get-started.html#setting-up-the-environment)
* [All Materials to Learn Kotlin](https://kotlinlang.org/docs/reference/)
* [Conditionals in Kotlin](https://kotlinlang.org/docs/tutorials/kotlin-for-py/conditionals.html)

## Contact and Support

Feel free to provide feedback via email: [adela.yohana@gmail.com](mailto:adela.yohana@gmail.com)