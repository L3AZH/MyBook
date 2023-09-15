# Java Building Blocks

## OCA EXAM OBJECTIVES COVERED IN THIS CHAPTER:

### Java Basics

- Define the scope of variables
- Define the structure of a Java class
- Create executable Java applications with a main method; run a Java program from the command line; including console output
- Import other Java packages to make them accessible in your code
- Compare and contrast the features and components of Java such as platform independence, object orientation, encapsulation, etc.

### Wokring with Java Data Types

- Declare and initialize variables( including casting or primitive types)
- Differentiate between object reference variables and primitive variables
- Know how to read write to object fields
- Explain an Object's Lifecycle( creation, "dereference by reassignment" and garbage collection)

## Understanding the Java Class Structure

In Java programs, classes are the basic building blocks. When defining a _class_, you describe all the parts and characteristics of once of those building blocks. To use most classes, you have to create objects. An _Object_ is a runtime instance of a class in memory. All the various objects of all the different classes represent the state of your program.

In the following sections, we'll look at fields, methods, and comments. We'll also explore the relationship between classes and files.

### **Fields and Methods**

Java classes have two primary elements: _methods_, often called functions or procedures in other languages, and _fields_, more generally known as variables. Together these are called the _members_ of the class. Variables hold the state of the program, and method operate on that state. If the change is important to remember, a variable stores that change. That's all classes really do. It's the programmer who creates and arranges these elements in such a way that resulting code is useful and, ideally, easy for other programmers to understand.

The simplest Java class you can write looks like this:

```java
1: public class Animal {
2:
3: }
```

Java calls a word with special meaning a _keyword_. The `public` keyword on line 1 means the class can be used by other classed. The `class` keyword indicates you're defining a class. `Animal` gives the name of the class. Granted, this isn't very insteresting class, so add your first field:

```java
1: public class Animal {
2:     String name;
3: }
```

On line 2, we define a variable named `name`. We also define the type of that variable to be a `String`. A `String` is a value that we can put text input, such as **"this is a string"**. `String` is also a class supplied with Java. Next you can add methods:

```java
1: public class Animal{
2:     String name;
3:     public String getName(){
4:         return name;
5:     }
6:     public void setName(String newName){
7:         name = newName;
8:     }
9: }
```

On line 3-5, you've defined your first method. A method is an operation that can be called. Agian, `public` is used to signify that this method may be called from other classes. Next comes the `return` type- in this case, the method returns a `String`. On line 6-8 is another method. This one have special return type called _void_. `void` means that no value at all returned. This method requires information be supplied to it from the calling method; this information is called _parameter_. `setName` has one prameter named _newName_, and it is of type `String`. This mean the caller should pass in one `String` parameter and expect nothing to be returned.  
The full declaration of a method is call a _method signature_. In this example, can you identify the return type and parameters?

```java
public int numberVisitors(int month)
```

The return type is `int`, which is a numeric type. There's one parameter named _month_, which is of type int as well.

### **Comments**

Another common part of the code is called a _comment_. Because comments aren't executable code, you can place them anywhere. Comments make your code easier to read. You won't see many comments on the exam-the exam creators are trying to make the code difficult to read-but you'll see them in book as we explain the code. And we hope you use them in your own code. There are three types of comments in Java. The first is called a single-line comment:

```java
// comment util end of line
```

A single-line comment begins with two slashes. Anything you type after that on the same line is ignored by the complier. Next comes the multiple-line comment:

```java
/* Multiple
* line comment
*/
```

A multiple comment( also know as a multiple comment) includes anything starting from the symbol `/*` until the symbol `/*`. People often type an asterisk (\*) at the beginning of each line of multiline comment to make it easier to read, but you don't have to. Finnally, we have a `Javadoc` comment:

```java
/**
* Javadoc multiple-line comment
* @author Jeanne and L3azh
*/
```

This comment is similar to a multiline comment except it starts with `/**`. This special syntax tells the Javadoc tool to pay attention to the comment. Javadoc comments have a specific struture that the Javadoc tool know how to read. You won't see a Javadoc comment on the exam-just remember it exists so you can read up on it online when you start writing programs for others to use.  
As a bit of practice, can you identify which type of comment each of these five words is in? Is it a single-line or a multiline comment?

```java
/*
* //anteater
*/
// bear
// // cat
// /* dog */
/* eleplant */
/*
* /* ferret */
*/
```

Did you look closely? Some of these are tricky. Even though comments technically aren't on the exam, it is good to practice to look at code carefully.

Okay, on to the answers. `anteater` is in a multiline comment. Everything between `/*` and `*/` is part of a multiline comment--even if it includes a single-line comment within it! `bear` is your basic single-line comment. `cat` and `dog` are also single-line comments.  
Everything from `//` to the end of the line is part of the comment, even if it is another type of comment. `eleplant` is your basic multiline comment.  
The line with `ferret` is interesting in that it doesn't compile. Everything from the first `/*` to the first `*/` is part of the comment, which means the compiler sees somthing like this:

```java
/* */ */
```

We have a problem. there is an extra `*/`. That's not valid syntax--a fact the compiler is happy to inform you about.

### **Classes vs. File**

Most of the time, each Java class is defined in its own `*.java` file. It is usually `public`, which means any code can call it. Interestingly, Java does not require that the class be `public`. For Example, this class is just fine:

```java
1: class Animal{
2:     String name;
3: }
```

You can even put two classes in the same file. When you do so, at most one of the classes in the file is allowed to be public. That means a file containing the following is also fine:

```java
1: public class Animal{
2:     private String name;
3: }
4: class Animal2{
5: }
```

If you do have a public class, it needs to match the filename. `public class Animal2` would not compile in a file named `Animal.java`.
