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

## Writing a _main()_ Method

A Java program begins execution with it `main()` _method_. A `main()` method is the gateway between the startup of Java process, which is managed by the _Java Virtual Machine_ (JVM), and the beginning of the programmer's code. The JVM calls on the underlying system to allocate memory and CPU time, access files, and so on.  
The `main()` method lets us hook our code into this process, keeping it alive long enough to do the work we've coded. The simplest possible class with a `main()` method looks like this:

```java
1: public class Zoo{
2:    public static void main(String[] args) {
3:
4:     }
5:}
```

This code doesn't do anything usefull( or harmful). It has no instruction other than to declare the entry point. It does illustrate, in a sense, that what you can put in a `main()` method is arbitrary. Any legal Java code will do. In fact, the only reason we even need a class structure to start a Java program is because the language requires it. To compile and execite this code, type it into a file called `Zoo.java` and execute the following:

```bash
$ javac Zoo.java
$ java Zoo
```

If you don't get any error messages, you were succesful. If you do get error messages, check that you've installed Java Development Kit (JDK) and not a Java Runtime Environment (JRE), that you have added it to the `PATH`, and that you didn't make any typos in the example. If you have any of these problems and don't know what to do, post a question with the error message you received in the Beginning Java forum at [CodeRanch](wwww.coderanch.com/forum/f-33/java).  
To compile Java code, the file must have the extension `.java`. The name of the file must match the name of the class. The result is a file of _bytecode_ by the same name, but with a `.class` filename extension. Bytecode consists of instructions that the JVM knows how to execute. Notice that we must omit the `.class` extension to run `Zoo.java` because the peroid has a reserved meaning in the JVM.  
The rules for what a Java code file contains, and in what order, are more detailed than what we have explained so far( there is more on this topic later in the chapter). To keep things simple for now, we'll follow a subset of the rules:

- Each file can contain only one class.
- The filename must match the class name, includeing case, and have a `.java` extension.

Suppose we replace line 3 in `Zoo.java` with `System.out.Println("Welcome!");`. When we compile and run the code again, we'll get the line of output that matches what's between the quotes. In other word, the program will output `Welcome!`.  
Let's first review the words in the `main()` method's signature, one at a time. The keyword `public` is what's called an _access modifier_. It declares this method's level of exposure to potential callers in program. Naturally, `public` means anyplace in the program.  
The keyword `static` binds a method to its class so it can be called by just the class name, as in, for example, `Zoo.main()`. Java doesn't need to create an object to call the `main()` method--which is good since you haven't learned about creating objects yet! In fact, the JVM does this, more or less, when loading the class name given to it. If a `main()` method isn't present in the class we name with `.java` executable, the process will throw an error and terminate. Even if a `main()` method is present, Java will throw an exception if it isn't static. A nonstatic `main()` method might as well be invisible from the point of view of the JVM.  
The keyword `void` represents the _return type_. A method that returns no data returns control to the caller silently. In general, it's good practice to use `void` for methods that change and object's state. In that sense, the main() method changes the program state from started to finished.  
Finally we arrive ath the `main()` method's parameter list, represented as an array of `java.lang.String` objects. In practice, you can write `String[] args, String args[]` or `String... args;` the compiler accepts any of these. The variable name `args` hints that this list contains values that were read in (arguments) when JVM started. You can use any name you like, though. The characters `[]` are brackets and represent an array. An array is a fixed-size list of items that are all of the same type. The characters `...` are called varargs( variable argument lists).  
Let's see how to use the `args` parameter. First we modify the `Zoo` Program to print out the first two arguments passed in:

```java
public class Zoo {
    public static void main(String[] args){
        System.out.Println(args[0]);
        System.out.Println(args[1]);
    }
}
```

`args[0]` accesses the first element of the array. That;s right: array indexes begin with 0 in Java. To run it, type this:

```bash
$ javac Zoo.java
$ java Zoo Bronx Zoo
```

The output is what you might expect:

```
Bronx
Zoo
```

The program correctly identifies the first two "words" as the arguments. Spaces are used to seperate the arguments. If you want spaces inside an argument, you need to use quotes as in this example:

```bash
$ javac Zoo.java
$ java Zoo "San Diego" Zoo
```

Now we have a space in the output:

```
San Diego
Zoo
```

All command-loine arguments are treated as `String` objects, even if they represent another data type:

```bash
$ javac Zoo.java
$ java Zoo Zoo 2
```

No matter. You still get the values output as `String`s.

```
Zoo
2
```

Finally, what happends if you don't pass in enough arguments?

```bash
$ javac Zoo.java
$ java Zoo Zoo
```

Reading `args[0]` goes fine and Zoo is printed out. Then Java panics. There's no second argument! What to do? Java prints out an exception telling you it has no idea what to do with this argument at position 1.

```java
ZooException in thread "main" java.lang.ArrayIndexOutOfBoundsException: 1
 at mainmethod.Zoo.main(Zoo.java:7)
```

To review, you need to have a JDK to compile because it includes a compiler. You do not need to have a JDK to run the code--a JRE is enough. Java class files run on the JVM and therefore run on any machine with Java rather than just the machine or operating system they happened to have been compiled on.
