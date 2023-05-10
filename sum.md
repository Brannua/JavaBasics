
[初学编程的常见误区](https://www.bilibili.com/video/BV1c54y1U7pp)

![image-20230330001856416](https://aliyun-oss-lpj.oss-cn-qingdao.aliyuncs.com/images/by-clipboard/image-20230330001856416.png)

## Module 1: Java Fundamentals

Variables: store data

Conditionals: control how your code runs

Arrays: store and work with many values

Loops: control how many times a piece of code needs to run

Functions: perform tasks

## Module 2: Object Oriented Programming

objects、immutable objects、list collections、map collections、exception handling、

package and import、static and final、enums、unit test、inheritance and polymorphism、

higher order functions、big decimal、interface、concurrency and multithreading

## Reasons to learn Java

Java is general-purpose, which means that Java powers a wide range of applications.
As a Java developer,
- you can build web applications using Spring boot,
- you can build applications on Android,
- you can automate tasks using Selenium,
- you can develop cloud native applications,
- you can integrate microservices,
- you can ...

Java can run on any machine, it's well known for its "write once, run anywhere"
  - This is because the Java Virtual Machine, the JVM, which is responsible for executing compiled Java code, can be installed on any platform

Java is the No.1 language for developing enterprise applications

## To run Java code, you need

1. A Java Compiler - to compile your code.

2. A Java Runtime - to run the compiled code.

	So, this is why JDK provides a Compiler、a Runtime、and a lot of other things.

	<img style="width: 12rem;" src="https://aliyun-oss-lpj.oss-cn-qingdao.aliyuncs.com/images/by-clipboard/20230307213835.png"></img>

## Roadmap

1. Install a JDK(Java Development Kit) on your machine => from Amazon Corretto

	Amazon Corretto is just a distribution which once installed, does the work of setting up a JDK on your machine.
	Basically all you need to do is install it and it's going to do the heavy lifting.

	```shell
	javac -version  # check compiler
	java -version   # check runtime
	```

	Finished ! you've just installed a JDK, now your computer can compile and run Java code.

2. Download a text editor to write code

	I use vim & vscode(the extension pack for java is must).

	Now you have everything you need to start building Java applications!

3. Write & Run your first Java code

	```shell
	# Every java file needs to follow the naming convention -> CamelCase
	touch HelloJava.java
	```
	```java
	// In java, you must write all of your code in a class.
	// And the ClassName needs to be the same as your FileName.
	// So here we create a class.
	public class HelloJava {
	}
	
	/* Notice:
		the [public] exposes current class to other classes that may exist inside your workspace,
		but since now we have only one class,
		so it's optional.
	*/
	```
	
	All right, so what's next is the `main()` method, which is the entry point of a Java application.
	
	And inside main, we're going to print the message "Hello Java"
	
	```java
	public class HelloJava {
		public static void main(String[] args) {
			System.out.println("Hello Java");
		}
	}
	
	/* Notice:
		the semicolon is really important, which means end of statement.
		every statement in Java, every line of code, needs a semicolon at the end.
		so if you forget your semicolon, your code is not gonna run.
	*/
	```
	
	Now we're ready to compile and run our Java code.
	
	```shell
	# The javac command compiles your javaCode into byteCode
	javac <FileName>.java
	
	# The java command executes the compiled code
	java <FileName>
	```
	
	For example

	![image-20230331230902548](https://aliyun-oss-lpj.oss-cn-qingdao.aliyuncs.com/images/by-clipboard/image-20230331230902548.png)

See you in workbook 1.1
## Variable

> Store data inside variable.

### Java is strongly typed

which means that variables can only store values of their type.

### Java is case sensitive

eg: `people` is not the same as `People`

### The convention to naming a variable

**lowerCamelCase**

eg: `int peopleOnBus = 20;`

### Update the value inside a variable

Just set it equal to a new value, or use `+=`、`-=`、...

See you in workbook 2.1

## Use variables to store numeric data

### Types: int and long

We can use `int` and `long` variables to store whole numbers.

You should know the difference between `int` and `long` and when to use `int` vs `long`.

```java
int numberOfFans = 5000;

// 如下两行等价，但显然第二行的可读性更好
long population = 7000000000L;
long population = 7_000_000_000L;
```

思考一下：为什么要在 7000000000 这个数后面加个 L ？

如果你不加 L，那么 Java 就只会看到这是一个很大的数，它并不知道你这个开发者要将这个数存到什么地方，所以 Java 就会向你抱怨：“你怎么写了这么大的一个数 ？！！！”

因此，你只需在这个数后面加个 L 来告诉 Java：“放松啦～ 咱们要存的地方存得下这个数的。”，然后 Java 就平静了。

### Type: double

We can use `double` variables to store decimal numbers, which are given so much size in memory that a double value can reach 15 [significant digits](https://zh.wikipedia.org/wiki/有效数字).

```java
double percentage = 55.7;
```

Avoid just using integers for math calculations,

because if you multiply or divide two integers, the result will always be an integer,

because Java's going to cut off all the decimals.

```
integer * integer => integer
integer / integer => integer
```

eg

```java
int people = 3;
int wallet = 20;
System.out.println(wallet / people); // 6, which is not the result we want.

// So we need to make sure that at least one of these values is stored as a decimal,
// then Java's going to know to return a decimal result.
int people = 3;
double wallet = 20;
System.out.println(wallet / people); // 6.666666666666667, this is the result we want.
```

### Golden Rule

If precision is important, use `double` for math calculations.


### Type: String

We can use the type `String` to store text.

```java
String sentence = "Hello world !";
```

If you want to update String varibles, just let the variable equals to a new value.

```java
sentence = "Good morning !";
```

String unlike int in memory, 

no matter what you store in the integer variable, it's always 4 bytes,

but with String, empty text alone takes up 24 bytes,

and the more text that you add to a string, the more memory it takes up.

---

You can use the `+` operator to join two String values.

```java
String sentence = "His name is: ";
String placeholder = "Harry";
System.out.println(sentence + placeholder);
```

You can use the `+` operator to blend values into a string.

```java
double points = 50;
String announcement = " points for Gryffindor";
System.out.println(points + announcement); // 50.0 points for Gryffindor
```


### Type: char

We can use the `char` type to store single characters.

```java
char gender = 'F';
```

We can join a String value with a char value using the `+` operator.

```java
System.out.println("Gender: " + 'F');
```

---

```java
String gender = "F";
```

It seems that String is more flexible than char,

so why not always use String ?

The answer is【memory】and【performance】!

char consumes less memory, and char is faster than String !

### Summarize

There are 6 core data types (we didn't cover `boolean` yet).

| Data Type | Value                    | Amount of Memory (Bytes)         | Valid Range of Values                              |
| --------- | ------------------------ | -------------------------------- | -------------------------------------------------- |
| int       | Whole numbers            | 4                                | From: -2147483648 To: 2147483647                   |
| long      | Very large whole numbers | 8                                | From: -9223372036854775808 To: 9223372036854775807 |
| double    | Decimals                 | 8                                | Decimal can reach 15 significant digits            |
| char      | A single character       | 2                                | -                                                  |
| String    | Text                     | Varies, 24 bytes for empty text. | -                                                  |

平时开发我基本不使用 `byte, short, float`

See you in workbook 2.2


## Math operators

So far you've learned about: `int`、`long`、`double`、`char`、`String`.

You can use math operators shown as below to play with these values.

`+, -, *, /, %, ++, --, +=, -=, ...`

### Pattern

An operation between whole numbers returns a whole number.

An operation between decimals will always perserve the decimal.

### Think about that why do we care about the remainder ?

It's very useful if you want to identify odd or even numbers.

```java
int remainder = 10 % 2; // 0
```

See you in workbook 2.3


## Type casting

In Java, we can cast variables from one type to another.

```java
// Cast double to int
// Just telling Java the type that we're casting to.
double decimal = 4.3;
int integer = (int)decimal;
```

See you in workbook 2.4

## Scanner

Scanner contains many methods that we can use to scan for user input.

| method       | scan for  | explaination                                       |
| ------------ | --------- | -------------------------------------------------- |
| nextInt()    | integers  | skips the whiteSpace and picks up the next Integer |
| nextLong()   | integers  | skips the whiteSpace and picks up the next Long    |
| nextDouble() | decimals  | skips the whiteSpace and picks up the next Double  |
| next()       | text      | skips the whiteSpace and picks up the next String  |
| nextLine()   | text      | picks up a line of data                            |
| ...          | ...       | ...                                                |

> The default delimiter is white space.

### Usage

1、Create an instance of Scanner which can receive input from the `System.in`.

```java
import java.util.Scanner;
Scanner sc = new Scanner(System.in);
```

2、Use Scanner's methods to pick up (integers、decimals、text、...) from user input.

```java
int coffeeAmount    = sc.nextInt();
double coffeePrice  = sc.nextDouble();
String name         = sc.nextLine();
...
```

3、Once you are done with Scanner, always close it, otherwise you're going to get a resource leak.

```java
sc.close();
```
### Debugging

Fixing bugs in your code is called debugging, which is a must have skill for any programmer.

Debugging involves tracing the runTime step by step.

Please do not clutter your code with print statements to understand what's going on,

use breakpoints instead !
## the trap of nextLine()

### 表面现象

`nextLine()` gets skipped when placed after
- `nextInt()`
- `nextLong()`
- `nextDouble()`
- `next()`

### recap

| method       | scans for | explaination                                       |
| ------------ | --------- | -------------------------------------------------- |
| next()       | text      | skips the whiteSpace and picks up the next String  |
| nextLine()   | text      | picks up a line of data                            |

[what's-the-difference-between-next-and-nextline-methods-from-scanner-class](https://stackoverflow.com/questions/22458575/whats-the-difference-between-next-and-nextline-methods-from-scanner-class)

### 看清本质

当我看完了本节视频，我突然意识到，这不就是我在大一学 C 语言的时候，那个曾经让我头疼万分的所谓“没有吃回车”的问题嘛,

当时我还浅浅了解了一下什么是 Shell，什么是 Shell 的缓冲区,

并写下了文字版的总结，See [here](http://liupj.top/2022/05/09/single-char-io&shell-buffer/).

### 解决方案

显而易见，用 `nextLine()` “吃一下残留在 Shell 的缓冲区中的回车”呗～

即：place a throwaway nextLine before the 'real' nextLine

See you in workbook 2.5
# Booleans and Conditionals

In this section, you will gain full control over how your code runs.

### Roadmap

1. Use conditions to control which parts of your code run.

2. Execute code by comaring a [value] against a list of [cases].
## boolean

```java
boolean bool1 = true;
boolean bool2 = false;
```

### Summarize

| Data Type | Value                    | Amount of Memory (Bytes)         | Valid Range of Values                              |
| --------- | ------------------------ | -------------------------------- | -------------------------------------------------- |
| int       | Whole numbers            | 4                                | From: -2147483648 To: 2147483647                   |
| long      | Very large whole numbers | 8                                | From: -9223372036854775808 To: 9223372036854775807 |
| double    | Decimals                 | 8                                | a decimal can reach 15 significant digits          |
| char      | A single character       | 2                                | -                                                  |
| String    | Text                     | Varies, 24 bytes for empty text. | -                                                  |
| boolean   |                          | 1                                | true or false                                      |

## Comparison Operators

`>`, Greater than, returns `true` if the value on the left is greater than the value on the right.

`<`, Less than, returns `true` if the value on the left is less than the value on the right.

`>=`, Greater than or equal to, returns `true` if the value on the left is greater than or equal to the value on the right.

`<=`, Less than or equal to, returns `true` if the value on the left is less than or equal to the value on the right.

`==`, returns `true` if two values are equal.

`!=`, returns `true` if two values are not equal.

### Comparing Strings

Do not use `==` or `!=` to compare strings.

Instead, you can compare one string to another by calling `equals()` from one of them.

```java
String str1 = "hello";
String str2 = "hello";

str1.equals(str2);  // true
!str1.equals(str2); // false
```

<!-- You should know about how memory is being allocated. but 目前老师并没有讲 -->

See you in workbook 3.1

## if - else

Goal: Use if - else to run specific code blocks based on various conditions.

```java
if (condition) {
    // Code runs if the condition is true
} else {
    // Code runs if the condition is false
}
```

The condition is usually the result of a comparison that returns true or false.

See you in workbook 3.2

---

Not only can we test only one condition, but also many conditions by embedding a series of `else if (condition)` statements.

```java
if (condition) {
    // Code
} else if (condition) {
    // Code
} else if (condition) {
    // Code
} else {
    // Code
}
```

See you in workbook 3.3 and 3.4

## Logical Operators

We can use logical operators to make our conditionals a little more complex.

There are 3 types of logical operators,

---

`&&` returns true only if both comparisons are true.

( comparison1 && comparison2 )

---

`||` returns true if either one of the comparison is true.

( comparison1 || comparison2 )

---

`!` reverses the value of a boolean expression.

---

See you in workbook 3.5
## Switch Statements

whenever you're comparing one variable against a long list of values, such as

```java
if (weather.equals("sunny")) {
    // code
} else if (weather.equals("cloudy")) {
    // code
} else if (weather.equals("rainy")) {
    // code
} else {
    // code
}
```

you should avoid having a long list of `else if` statements, because this looks so disgusting !

Instead, you should favor using a switch statement which was designed to compare one variable against a list of cases.

```java
switch (weather) {
    case "sunny":   // code     break;
    case "cloudy":  // code     break;
    case "rainy":   // code     break;
    default:        // code
}
```

Then you might be asking that when to use `if` vs `switch` ?

---

The only thing you can really do with `switch` is compare one variable against a list of values.

---

`if` statement is more flexible so that suitable for complex conditions, such as when you need to compare multiple variables, they give you the flexibility to evaluate compound conditions using logical operators.

```java
if (temperature >= 80 && humidity >= 60) {
    System.out.println("It's too hot and humid\n");
} else {
    System.out.println("It's comfortable\n");
}
```

---

See you in workbook 3.6 and 3.7

As you write more and more code inside `main()`, you'll notice that it becomes increasingly cluttered and messy.

And the more code you write, the more unreadable that it becomes.

### Functions

A function is a grouping of code, it performs a task, and obviously it's reusable.

Some functions rely on parameters to perform their task.

Some functions will return a final value.

![image-20230423202020449](https://aliyun-oss-lpj.oss-cn-qingdao.aliyuncs.com/images/by-clipboard/image-20230423202020449.png)

Instead of writing all of your code inside of a single code block,

you can split it up into functions and call them as needed.

Let's begin organizing your code using functions!


## Define functions and call them

See video on udemy.

### Notice

Functions' name needs to represent the task it's performing.

### Notice

`public` means the function can be publicly accessed from any package or subfolder,

but because we've got only one package with a single class in it,

it doesn't really matter what level of access you specify.

### Notice

You can notice that `main()` is also a function, it has a very similar signature to our functions.

Every function has a specific task that it performs, the `main()` function performs the task of running our application.

The `main()` function has a very specific signature that the JVM looks for when you run your app, when it finds `main()` function, it executes it.


## Parameters

Functions with parameters expect to receive values.(these functions rely on parameters to perform their task)

Functions【without】parameters【do not expect】to receive values.

Parameters are essentially just variables.

## Arguments

A value that you pass into a function is known as an argument.

**Parameters and Arguments makes functions completely reusable**!

## Notice

When a function defines parameters, then in order to call it,

you need to pass in a matching number of arguments based on the position of these parameters.


## Return Values

> You can return values from a function.

## Notice

Bad practice: Your function handles the final result.

Good practice: Your function return the final result.

## Notice

Whenever you specify a return type,

you need to make sure that something gets returned no matter what gets passed in.

## Terminate the runTime

```java
System.exit(0);
```

See you in workbook 4.3


## Doc Comments

> Can be used to describe what a function does.

**If you're working in a team of developers, you should have a document for every function.**

## How to write Doc Comments ?

See udemy

See you in workbook 4.4


## Scope

> The scope of a variable determines its life span.

The take home message is:
    You can never access a variable outside the scope that it was defined in.

## Global Scope

Please against using global variables,

instead, you should keep everything local and use parameters,

because when you have too many global variables, you start losing track of what's really going on(such as from your debugger in vscode).

> Please watch the video on udemy.


## Built-in Functions

The JDK provides so many built-in functions that you can call out of the box.

But to be honest, a good developer never memorizes code!

Instead, a good developer uses the internet!
    to read documentation.
    to find resources.

See you in workbook 4.5

