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
