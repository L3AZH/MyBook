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

## Understanding Package Declarations and Imports

Java comes with thousands of built-in classes, and there are countless more from developers like you. With all those classes, Java needs a way to organize them. It handles this in a way similar to a file cabinet. You pull all your pieces of paper in folders. Java puts classes in _packages_. These are logical groupings for classes.  
We wouldn't put you in front of a file cabinet and tell you to find a specific paper. Instead, we'd tell you which folder to look in. Java works the same way. It needs you to tell it which packages to look in to find code.  
Suppose you try to compile this code:

```java
public class ImportExample{
    public static void main(String[] args){
        Random r = new Random(); // DOES NOT COMPILE
        System.out.println(r.nextInt(10));
    }
}
```

The Java compiler helpfully gives you an error that looks like this:

```
Random cannot be resolved to a type
```

This error could mean you made a typo in the name of the class. You double-check and discover that you didn't. The other cause of this error is omitting a needed _import_ statement. Import statements tell Java which packages to look in for classes. Since you didn't tell Java where to look for `Random`, it has no clue.  
Trying this again with the import allows you to compile:

```java
import java.util.Random;
public class ImportExport{
    public static void main(String[] args){
        Random r = new Random();
        System.out.Println(r.nextInt(10)); // print a number between 0 and 9
    }
}
```

Now the code runs; it prints out a random number between 0 and 9. Just like arrays, Java likes to begin counting with 0.  
Java classes are grouped into packages. The import statement tells the compiler which package to look in to find a class. This is similar to how mailing a letter works.

Imagine you are mailing a letter to 123 Main St., Apartment 9. The mail carrier first brings the letter to 123 Main st. Then she looks for the mailbox for apartment number 9. The address is like the package name in Java. The apartment number is like the class name in Java. Just as the mail carrier only looks at apartment numbers in the building, Java only looks ofr class names in the package.  
Package names are hierarchical like the mail as well. The postal service starts with the top level, looking at your country first. You start reading a package name at the beginning too. If it begins with `java` or `javax`, this means it came with the JDK. If it starts with something else, it likely shows where it came from using the website name in reserve. From example, `com.amazon.Java8book` tell us the code came from amazon.com. After the website name, you can add whatever you want. For example, `com.amazon.java8.my.name` also came from amazon.com. Java calls more detailed packages _child packages_. `com.amazon.java8book` is a child package of com.amazon. You can tell because it's longer and thus more specific.  
You'll see package names on the exam that don't follow this convention. Don't be surprised to see package name like `a.b.c`. The rule for package names is that they are mostly letters or numbers seperated by dots. Technically, you're allowed a couple of other characters between the dots. The rules are the same as for variable names, which you'll see later in the chapter. The exam may try to trick you with invalid variable names. Luckily. it doesn't try to trick you by giving invalid package names.  
In the following sections. we'll look at import with wildcards, naming conflicts with imports, how to create a package of your own, and how the exam formats code.

### **Wildcards**

Classes in the same package are often imported together. You can use a shortcut to import all the classes in a package:

```java
import java.util.*; // imports java.util.Random among other things
public class ImportExample {
    public static void main(String[] args){
        Random r = new Random();
        System.out.Println(r.nextInt(10));
    }
}
```

In this example, we imported `java.util.Random` and pile of other classes. The `*` is a wildcard that matches all classes in the package. Every class in the `java.util` package is available to this program when Java compiles it. It doesn't import child packages, fields, or methods; it imports only classes. (Okay, it's only classes for now, but there's a special type of import called the "static import" that imports other types.)  
You might think that including so many classes slows down your program, but it doesn't. The compiler figures out what's actually needed. Which approach you choose is personal preference.  
Listing the classes used makes the code easier to read, especially for new programmers. Using the wildcard can shorten the import list. You'll see both approaches on the exam.

### **Redundant Imports**

Wait a minnute! We've been referring to `System` without an import and Java found it just fine. There's one special package in the Java world called `java.lang`. This package is special in that it is automatically imported. You can still type this package in an `import` statement, but you don't have to. In the following code, how many of the imports do you think are redundant?

```java
1: import java.lang.System;
2: import java.lang.*;
3: import java.util.Random;
4: import java.util.*;
5: public class ImportExport {
6:     public static void main(String[] args){
7:         Random r = new Random();
8:         System.out.Println(r.nextInt(10));
9:     }
10: }
```

The answer is that three of the imports are redundant. Lines 1 and 2 are redundant because everything in `java.lang` is automatically considered to be importe. Line 4 is also redundant in this example because `Random` is already imported from `java.util.Random`. If line 3 wasn't present, `java.util.*` wouldn't be redundant, thouhgt, since it would cover importing `Random`.  
Another case of redundancy involves importing a class that is in the same package as the class importing it. Java automatically looks in the current package for other classes.  
Let's take a look at one more example to make sure you understand the edge cases for imports. For this example, `Files` and `Paths` are both in the package `java.nio.file`. You don't need to memorize this package for the OCA exam( but you should know it for the OCP exam). When testing your understanding of packages and imports, the OCA exam willuse packages you may never have seen before. The question will let you know which package the class is in if you need to know that in order to answer the question.  
What imports do you thing would work to get this code to compile?

```java
public class InputImport {
    public void read(Files files) {
        Paths.get("name");
    }
}
```

There are two possible answers. The shorter one is to use a wildcard to import both at the same time:

```java
import java.nio.file.*;
```

The other answer is to import both classes explicitly:

```java
import java.nio.file.Files;
import java.nio.file.Paths;
```

Now let's consider some imports that don't work:

```java
import java.nio.*; // NO GOOD - a wilcard only matches class names, not "file.*Files"
import java.nio.*.*; // NO GOOD - you can only have on wildcard and it must be at the end
import java.nio.files.Paths.*; // NO GOOD - you cannot import methods, only class names
```

### **Naming Conflicts**

One of the reasons for using packages is so that class names don't have to be unique across all of Java. This means you'll sometimes want to import a class that can be found in multiple places. A common exmaple of this is the `Date` class. Java provides implementations of `java.util.Date` and `java.sql.Date`. This is another example where you don't need to know thw package names for the OCA exam--they waill be providedto you. What import could we use if we want the `java.util.Date` version?

```java
public class Conflicts {
    Date date;
    // some more code
}
```

The answer should be easy by now. You can write either `import java.util.*;` or `import java.util.Date;`. The tricky cases come about when other imports are present:

```java
import java.util.*;
import java.sql.*; //DOES NOT COMPILE
```

When the class is found in multiple packages, Java gives you the compiler error:
`The type Date is ambiguous`
In our example, the solutions is easy--remove the `java.sql.Date` import that we don't need. But what do we do if we need a whole pile of orther classes in the `java.sql` package?

```java
import java.util.Date;
import java.sql.*;
```

Ah, now it works. If you explicitly import a class name, it takes precedence over any wildcards present. Java thinks, "Okay! The programmer really wants me to assume use of the `java.util.Date` class."  
One more example. What does Java do with "ties" for precedence?

```java
import java.util.Date;
import java.sql.Date;
```

Java is smart enough to detect that this code is no good. As a programmer, you've claimed to explicitly want the default to be both the `java.util.Date` and `java.sql.Date` implementations. Because there can't be two defaults. the compiler tell you:
`The import java.sql.Date collides with another import statement`

## <span style="background-color: #f2a552">**If You Really Need to Use Two Classes with the Same Name..**</span>

Sometimes you really do want to use `Date` from two different packages. When this happens, you can pick one to use in the import and use the other's fully qualified class name( the package name, a dot, and the class name) to specify that it's special. For example:

```java
import java.util.Date;

public class Conflicts {
    Date date;
    java.sql.Date sqlDate;
}
```

Or you could have neither with an import and always use the fully qualified class name:

```java
public class Conflicts {
    java.util.Date date;
    java.sql.Date sqldate;
}
```

### **Creating a New Package**

Up to now, all the code we've written in this chapter has been in the _default package_. This is a special unnamed that you should use only for throwaway code. You can tell the code in the default package, because there's no package name. On the exam, you'll see the default package used a lot to save space in code listings. In real life, always name your packages to avoid naming conflicts and to allow orthers to reuse your code.  
Now it's time to create new package. The directory structure on your computer is related to the package name. Suppose we have these two classes:  
`C:\temp\packagea\ClassA.java`

```java
package packagea;
public class ClassA{
}
```

`C:\temp\packageb\ClassB.java`

```java
package packageb;
import packagea.ClassA;
public class ClassB {
    public static void main(String[] args) {
        ClassA a;
        System.out.println("Got it");
    }
}
```

When you run a Java program, Java knows where to look for those package names. In this case, running from `C:\temp` works because both `packagea` and `packageb` are underneath it

## <span style="background-color: #f2a552">**Compile Code with Packages**</span>

You'll learn Java much more easily by using the command line to compile and test your examples. Once you know the Java syntax well, you can switch to an integrated development environment( IDE) like Eclipse. An IDE will save you time in coding. But for the exam, your goal is to know details about the language and not have the IDE hide them for you.  
Follow this example to make sure you know how to use the command line. If you have any problems following this procedure, post a questing in the Beginning Jave forum at [CodeRanch](www.coderanch.com/forum/f-33/java). Decribe what you tried and what the error said.

### **Window setup**

Create two files:

- `C:\temp\packagea\ClassA.java`
- `C:\temp\packageb\ClassB.java`

Then type this command:

```
cd C:\temp
```

### **Mac/Linux setup**

Create two files:

- `/tmp/packagea/ClassA.java`
- `/tmp/packageb/ClassB.java`

Then type this command:

```
cd /tmp
```

### **To Compile**

Type this command:

```
javac packagea/ClassA.java packageb/ClassB.class
```

If this command doesn't work, you'll get an error message. Check your files carefully for typos agianst the provide files. If the command does work, two new files will be created:
`packagea/ClassA.class` and `packageb/ClassB.java`

### **To Run**

Type this command:

```
java packageb.ClassB
```

If it works, you'll see `Got it` printed. You might have noticed we type `ClassB` rather than `ClassB.class`. In Java you don't pass the extension when running a program.

### **Class Paths and JARs**

You can also specify the location of the other files explicitly using a class path. This technique is usefull when the class files are located elsewhere or in special JAR file. A JAR file is like a zip file of mainly Java class files. This goes beyond what you'll need to do on version 8 of the exam, althought it appears on older versions.  
On Windows, you type the following:

```
java -cp ".;C:\temp\someOtherLocation;c:\temp\myJar.jar" myPackage.MyClass
```

And on Mac OS/Linux, you type this:

```
java -cp ".:/tmp/someOtherLocation:/tmp/myJar.jar" myPackage.MyClass
```

The dot indicates you want to include the current directory in the class path. The rest of the command says to look for loose class files (or packages) in `someOtherLocation` and within `myJar.jar`. Windows uses semicolons to separate parts of the class path; other operating systems use colons.

Finally, you can use a wildcard (\*) to match all the JARs in a directory. Here's an example:

```
java -cp "C:\temp\directoryWithJars\*" myPackage.MyClass
```

This command will add all JARs to the class path that are in `directoryWithJars`. It won't include any JARs in the class path are in a subdirectory of `directoryWithJars`.

### **Code Formatting on the Exam**

Not all questions will include the imports. If the exam isn't asking about imports in the question, it will often omit the imports to save space. You'll see examples with line numbers that don't begin with 1 in this case. The question is telling you, "Don't worry--imagine the code we omitted is correct; just focus on what I'm giving you." This means when you see the line number 1 or no line numbers at all, you have to make sure imports aren't missing. Another thing the exam does to save space is to merge code on the same line. You should expect to see code like the following and to be asked whether it compiles. ( You'll learn about `ArrayList` in Chapter 3--asume that part is good for now.)

```java
6: public void method(ArrayList list) {
7:    if( list.isEmpty()) { System.out.println("e");
8:    } else { System.out.println("n");
9:    }}
```

The answer here is that it does compile because the code starts below the imports. Now, what about this one? Does it compile?

```java
1: public class LineNumbers {
2: public void method(ArrayList list){
3:  if(list.isEmpty()) { System.out.println("e");
4: } else { System.out.println("n");
5:  }}}
```

For this one, you would answer "Does not compile." Since the code begins with line 1, you don't get to assume that valid imports were provided earlier. The exam will let you know what package classes are in unless they're covered in the objectives. You'll be expected to know that `ArrayList` is in `java.util`--at least you will once you get to Chapter 3 of this book!  
You'll als0 see code that doesn't have `main()` method. When this happens, assume the `main()` method, class definition, and all necessary imports are present. You're just being asked if the part of the code you're shown compiles when dropped into valid surrounding code.

## Creating Objects

Our programs wouldn't be able to do anything useful if we didn't have the ability to create new objects. Remember that an object is an instance of a class. In the following sections, we'll look at constructors, object fields, instance initializers, and the order in which values are initialized.

### Constructors

To create an instance of a class, all you have to do is write `new` before it. For example:

```java
Random r = new Random();
```

First you declare the type that you'll be creating `(Random)` and give the variable a name `(r)`. This gives Java a place to store a reference to the object. Then you write `new Random()` to actually create the object.  
`Random()` looks like a method since it is followed by parentheses. It's called a _constructor_, which is special type of method that creates new object. Now it's time to define a constructor of your own:

```java
public class Chick {
    public Chick(){
        System.out.println("in constructor");
    }
}
```

There are two key points to note about the constructor: the name of the constructor matches the name of the class, and there's no return type. You'll likely see a method like this on the exam:

```java
public void Chick() {} // NOT A CONSTRUCTOR
```

When you see a method name beginning with a capital letter and having a return type, pay special attention to it. It is _not_ a constructor since there's a return type. It's a regular method that won't be called when you write `new Chick()`.  
The purpose of a constructor is to initialize fields, althought you can put any code in there. Another way to initialize fields is to do so directly on the line on which they're declared. This example shows both approaches:

```java
public class Chicken {
    int numEggs = 0; // initialize on line
    String name;
    public Chicken() {
        name = "Duke" // initialize in constructor
    }
}
```

For most classes, you don't have to code a constructor--the compiler will supply a "do nothing" default constructor for you. There's one scenario that requires you to declare a constructor that you'll learn about Chapter 5.

### Reading and Writing Object Fields

It's possible to read and write instance variables directly from the caller. In this exmaple, a mother swan lay eggs:

```java
public class Swan {
    int numberEggs; // instance variable
    public static void main(String[] arg) {
        Swan mother = new Swan();
        mother.numberEggs = 1; // set variable
        System.out.println(mother.numberEggs); //read variable
    }
}
```

Reading a variable is known as _getting_ it. The class gets `numberEggs` directly to print it out. Writing to a variable is known _setting_ it. This class sets `numberEggs` to 1.  
In Chapter 4, you'll learn how to protect the `Swan` class from having someone set a negative number of eggs.  
You can even read and write fields directly on the line declaring them:

```java
1: public class Name {
2:     String first = "Theodore";
3:     String last = "Moose";
4:     String full = first + last;
5: }
```

Lines 2 and 3 both write to fields. Line 4 does both. It reads the fields `first` and `last`. It then writes the field `full`.
