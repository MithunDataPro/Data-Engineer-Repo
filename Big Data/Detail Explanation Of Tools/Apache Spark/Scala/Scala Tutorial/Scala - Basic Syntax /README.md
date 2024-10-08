If you have a good understanding of Java, then it will be very easy for you to learn Scala. The biggest syntactic difference between Scala and Java is that the ';' line end character is optional.

When we consider a Scala program, it can be defined as a collection of objects that communicate via invoking each other’s methods. Let us now briefly look into what class, object, methods, and instance variables mean.

- **Object** − Objects have states and behaviors. An object is an instance of a class.  
  Example − A dog has states - color, name, breed as well as behaviors - wagging, barking, and eating.

- **Class** − A class can be defined as a template/blueprint that describes the behaviors/states that are related to the class.

- **Methods** − A method is basically a behavior. A class can contain many methods. It is in methods where the logic is written, data is manipulated, and all the actions are executed.

- **Fields** − Each object has its unique set of instance variables, which are called fields. An object's state is created by the values assigned to these fields.

- **Closure** − A closure is a function, whose return value depends on the value of one or more variables declared outside this function.

- **Traits** − A trait encapsulates method and field definitions, which can then be reused by mixing them into classes. Traits are used to define object types by specifying the signature of the supported methods.

---

## First Scala Program

We can execute a Scala program in two modes: one is interactive mode and another is script mode.

### Interactive Mode

Open the command prompt and use the following command to open Scala.

```bash
>scala

```

If Scala is installed in your system, the following output will be displayed −

```python
Welcome to Scala version 2.9.0.1
Type in expressions to have them evaluated.
Type :help for more information.

```

Type the following text to the right of the Scala prompt and press the Enter key −

```scala
scala> println("Hello, Scala!");

```

It will produce the following result −

```

Hello, Scala!

```

---

## Script Mode
Use the following instructions to write a Scala program in script mode. Open notepad and add the following code into it.

**Example**

```scala
object HelloWorld {
   /* This is my first java program.  
   * This will print 'Hello World' as the output
   */
   def main(args: Array[String]) {
      println("Hello, world!") // prints Hello World
   }
}

```

Save the file as − **HelloWorld.scala**.

Open the command prompt window and go to the directory where the program file is saved. The **scalac** command is used to compile the Scala program and it will generate a few class files in the current directory. One of them will be called **HelloWorld.class**. This is a bytecode that will run on Java Virtual Machine (JVM) using the **Scala** command.

Use the following command to compile and execute your Scala program.

```bash
> scalac HelloWorld.scala
> scala HelloWorld

```

**Output**

```

Hello, World!


```

---

## Basic Syntax

The following are the basic syntaxes and coding conventions in Scala programming.

### Case Sensitivity
Scala is case-sensitive, which means the identifiers `Hello` and `hello` would have different meanings in Scala.

### Class Names
For all class names, the first letter should be in Upper Case. If several words are used to form the name of a class, each inner word's first letter should be in Upper Case.  
**Example** − `class MyFirstScalaClass`.

### Method Names
All method names should start with a Lower Case letter. If multiple words are used to form the name of the method, then each inner word's first letter should be in Upper Case.  
**Example** − `def myMethodName()`.

### Program File Name
The name of the program file should exactly match the object name. When saving the file, you should save it using the object name (remember Scala is case-sensitive) and append `.scala` to the end of the name.  
**Example** − Assume `HelloWorld` is the object name, then the file should be saved as `HelloWorld.scala`.

### `def main(args: Array[String])`
Scala program processing starts from the `main()` method, which is a mandatory part of every Scala Program.

---

# Scala Identifiers

All Scala components require names. Names used for objects, classes, variables, and methods are called identifiers. A keyword cannot be used as an identifier, and identifiers are case-sensitive. Scala supports four types of identifiers:

---

### Alphanumeric Identifiers
An alphanumeric identifier starts with a letter or an underscore, which can be followed by further letters, digits, or underscores. The `$` character is a reserved keyword in Scala and should not be used in identifiers.

#### Legal Alphanumeric Identifiers:
- `age`
- `salary`
- `_value`
- `__1_value`

#### Illegal Alphanumeric Identifiers:
- `$salary`
- `123abc`
- `-salary`

---

### Operator Identifiers
An operator identifier consists of one or more operator characters. Operator characters are printable ASCII characters such as `+`, `:`, `?`, `~`, or `#`.

#### Legal Operator Identifiers:
- `+`
- `++`
- `:::`
- `<?>`
- `:>`

---

### Mixed Identifiers
A mixed identifier consists of an alphanumeric identifier followed by an underscore and an operator identifier.

#### Legal Mixed Identifiers:
- `unary_+`
- `myvar_=`

Here, `unary_+` used as a method name defines a unary `+` operator, and `myvar_=` used as a method name defines an assignment operator (operator overloading).

---

### Literal Identifiers
A literal identifier is an arbitrary string enclosed in back ticks \(` . . . `).

#### Legal Literal Identifiers:
- `` `x` ``
- `` `<clinit>` ``
- `` `yield` ``

---

## Scala Keywords

The following list shows the reserved words in Scala. These reserved words may not be used as constant or variable or any other identifier names.

```kotlin
abstract    case    catch   class
def         do      else    extends
false       final   finally for
forSome     if      implicit import
lazy        match   new     Null
object      override package private
protected   return  sealed  super
this        throw   trait   Try
true        type    val     Var
while       with    yield   
-   :   =   =>
<-  <:  <%  >:
#   @       

```

---

## Comments in Scala

Scala supports single-line and multi-line comments very similar to Java. Multi-line comments may be nested but are required to be properly nested. All characters available inside any comment are ignored by the Scala compiler.

```scala
object HelloWorld {
   /* This is my first java program.  
    * This will print 'Hello World' as the output
    * This is an example of multi-line comments.
    */
   def main(args: Array[String]) {
      // Prints Hello World
      // This is also an example of single line comment.
      println("Hello, world!") 
   }
}

```

---

## Blank Lines and Whitespace

A line containing only whitespace, possibly with a comment, is known as a blank line, and Scala totally ignores it. Tokens may be separated by whitespace characters and/or comments.

---

## Newline Characters

Scala is a line-oriented language where statements may be terminated by semicolons (;) or newlines. A semicolon at the end of a statement is usually optional. You can type one if you want, but you don't have to if the statement appears by itself on a single line. On the other hand, a semicolon is required if you write multiple statements on a single line. Below syntax is the usage of multiple statements.

```scala
val s = "hello"; println(s)

```

---

## Scala Packages

A package is a named module of code. For example, the Lift utility package is **net.liftweb.util**. The package declaration is the first non-comment line in the source file as follows −

```scala
package com.liftcode.stuff

```

Scala packages can be imported so that they can be referenced in the current compilation scope. The following statement imports the contents of the scala.xml package −

```scala
import scala.xml._

```

You can import a single class and object, for example, HashMap from the scala.collection.mutable package −

```scala
import scala.collection.mutable.HashMap

```

You can import more than one class or object from a single package, for example, TreeMap and TreeSet from the **scala.collection.immutable** package −

```scala
import scala.collection.immutable.{TreeMap, TreeSet}

```

---

## Apply Dynamic

A marker trait that enables dynamic invocations. Instances **x** of this trait allow method invocations **x.meth(args)** for arbitrary method names **meth** and argument lists **args** as well as field accesses **x.field** for arbitrary field names **field**. This feature is introduced in Scala 2.10.

If a call is not natively supported by **x** (i.e. if type checking fails), it is rewritten according to the following rules −

```scss

foo.method("blah") ~~> foo.applyDynamic("method")("blah")
foo.method(x = "blah") ~~> foo.applyDynamicNamed("method")(("x", "blah"))
foo.method(x = 1, 2) ~~> foo.applyDynamicNamed("method")(("x", 1), ("", 2))
foo.field ~~> foo.selectDynamic("field")
foo.varia = 10 ~~> foo.updateDynamic("varia")(10)
foo.arr(10) = 13 ~~> foo.selectDynamic("arr").update(10, 13)
foo.arr(10) ~~> foo.applyDynamic("arr")(10)

```


