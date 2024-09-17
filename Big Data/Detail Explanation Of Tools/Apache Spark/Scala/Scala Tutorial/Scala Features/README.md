# Scala Programming Features

Scala Programming Language comes bundled with a lot of unique features. We have segregated these features into three sections:

- **Scala High-Level Programming Features**
- **Scala Low-Level Programming Features**
- **Scala Ecosystem Features**

Let's start with the high-level features of Scala.

---

## High-Level Programming Features

### 1. Scala Runs on Browsers and JVM
Scala runs on both **browsers** and the **Java Virtual Machine (JVM)**. It is used for server-side applications and can also be used in the browser with the **"scala.js"** file format.

### 2. Scala is a High-Level Programming Language
Scala is a high-level language, meaning you don't need to deal with low-level concepts like **memory management** and **pointers**. You can write code at a higher level using **lambda** and **higher-order functions**. The focus is on **"What"** and **"How"** to implement the code, which is a key characteristic of high-level languages.

---

## Example: Imperative Approach to Filter Even Numbers

```scala
val numbers = List(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

// Using an imperative approach to filter even numbers
def filterEvenNumbersImperative(numbers: List[Int]): List[Int] = {
   val evenNumbers = new ListBuffer[Int]()
   for (num <- numbers) {
      if (num % 2 == 0) {
         evenNumbers += num
      }
   }
   evenNumbers.toList
}

val evenNumbersImperative = filterEvenNumbersImperative(numbers)

```

Compiler will perform step by step according to instructions in the code. We use lambda functions and high-order functions to find the result.

```
// Using a functional approach with higher-order functions and lambdas to filter even numbers
val evenNumbersFunctional = numbers.filter(num => num % 2 == 0)

```

This code is easier to read and maintain. It is also much more concise.

### 3. Scala has a Concise Syntax
Syntax of Scala codes are much easier. For example, for creating variables and types, it is much easy to write, like this −

```scala
val message: String = "Hello, Scala!"
val numbers: Array[Int] = Array(1, 2, 3, 4, 5)
val personInfo: (String, Int, String) = ("Alice", 30, "Engineer")

```

We can also use lambda functions and higher-order functions for code readability and concise code.

```scala
val numbers = List(1, 2, 3, 4, 5)
val sum = numbers.reduce((a, b) => a + b)   // long form
val shortSum = numbers.reduce(_ + _)        // short form
println(s"Sum: $sum")
println(s"Short Sum: $shortSum")

val fruits = List("apple", "banana", "cherry", "date")
fruits.foreach(fruit => println(fruit))   // long form
fruits.foreach(println)                   // short form

```

Similarly, we can define traits, classes and methods in clean and light syntax −

```scala
trait Shape {
   def area(): Double
}

trait Color {
   def getColor(): String
}

class Circle(radius: Double, color: String) extends Shape with Color {
   def area(): Double = math.Pi * radius * radius
   def getColor(): String = color
}

```

Since developers spend more time reading than writing code, so it is important to write concise and readable code.

## Scala is a Statically-type Language but has a Dynamic Feel

This is because of type inference capabilities which make Scala as Dynamic, like Python and Ruby code.

```scala
val x = List(1, 2, 3, 4, 5)
val doubled = x.map(_ * 2)
val filtered = x.filter(_ % 2 == 0)
val sum = x.reduce(_ + _)

```

# Scala Programming Overview

According to **Heather Miller**, Scala is a strong and statically-typed programming language. Here are the benefits of a statically typed language:

- It catches errors early, i.e., at compile time.
- It has good IDE support with reliable code completion and easy, reliable refactoring.
- You can refactor your code.
- It is scalable and maintainable.
- Strong typing reduces boilerplate code.

---

## Scala Has an Expressive Type System

The type system of Scala improves safety and coherence through:

- **Inferred types**
- **Generic, Open, and Type classes**
- **Polymorphic methods**
- **Intersection and union types**
- **Variance annotations**
- **Type bounds (upper and lower)**
- **Type lambdas**
- **Opaque type aliases**
- **Match types**
- **Extension methods**
- **Multiversal equality**
- **Context bounds and functions**
- **Dependent and Polymorphic function types**
- **Inner classes and abstract type members** for safe programming abstractions.

---

## Scala is a Functional Programming Language

Functional programming languages provide various features. Functions are like other values and can be passed like any other values. Various functions are supported like lambda functions and high-order functions. In Scala, everything is treated as an expression.

- There are various **mutable and immutable collections** in the standard library.
- **Functional methods are not mutable**; they only return updated copies.

---

## Scala is an Object-Oriented Programming Language

In an object-oriented type language, values are instances of a class and operators are methods. In Scala, all types inherit from a top-level class:

- **`Any`** and **`AnyVal`** for value types like `Int`.
- **`AnyRef`** for reference types.

There is **no distinction between primitives and boxed types**. **Boxing/unboxing is transparent** to users.

---

## Scala Supports FP/OOP Fusion

Scala supports **Functional Programming (FP)** and **Object-Oriented Programming (OOP)** in a typed setting. For example, functions handle logic while objects handle modularity.

---

## Scala Introduced Clear Term Inference

Introduced in **Scala 3**, term inference creates a term from a given type. There are context parameters which lead to inferred arguments. This is useful for type classes, context, dependencies, etc.

---

## Scala is Used for Client/Server Systems

Scala code can run in the browser and on the JVM (Java Virtual Machine). The JVM provides:

- Security
- Performance
- Memory management
- Portability

---

## Scala Has Seamless Java Interaction

You can use **Java classes** and **Java libraries** in your Scala application, and vice-versa. Libraries like **Akka** and **Play Framework** work in both languages. It is easy to use Java classes like `BufferedReader`.

### Example:

```java
import java.io.*;

String filename = "example.txt";
try (BufferedReader br = new BufferedReader(new FileReader(filename))) {
   String line;
   while ((line = br.readLine()) != null) {
      // Process the line here
   }
} catch (IOException e) {
   e.printStackTrace();
}

```

Java collections are used in Scala with simple conversion.

```scala
import scala.jdk.CollectionConverters._

val scalaList: Seq[Integer] = JavaClass.getJavaList().asScala.toSeq

```

# Scala has a Rich Set of Libraries

Scala offers a wealth of libraries and frameworks −

- **Play Framework** is used for scalable web applications.
- **Lagom** is used for microservices and legacy system transformation.
- **Apache Spark** is used for big data analytics.
- Numerous open source tools on **Awesome Scala list**.
- **Scala.js** is used for strong, JavaScript-like coding with React, jQuery, etc.

---

# Low-Level Programming Features

The high-level features of **Scala 2** and **Scala 3** are almost the same. But in the case of low-level, Scala 3 improves upon Scala 2 with the following features −

- Concise algebraic data types (ADTs) using **enums**.
- More readable syntax and optional braces.
- Fewer symbols for better code clarity.
- Package objects replaced by simpler top-level definitions.
- Clearer grammar with explicit keywords.
- Extension methods for simplicity.
- **Open modifier** for controlled class modification.
- **Multiversal equality** to avoid nonsensical comparisons.
- Easier macro implementation.
- **Union and intersection** for flexible type modeling.
- **Trait parameters** for early initialization.
- **Opaque type aliases** for value class replacement.
- **Export clauses** for aggregation.
- Procedure and varargs syntax consistency.
- Annotations for method behavior and Java interoperability.

---

# Scala Ecosystem Features

Scala has a rich ecosystem which offers libraries and frameworks for various needs −

## Web Development

- **Play Framework** is used for scalable web apps.
- **Scalatra** is used for high-performance web frameworks.
- **Finatra** is used for Scala services.
- **Scala.js** is used for type-safe front-end apps.
- **ScalaJs-React** is used for Scala-friendly React.
- **Lagom** is used for microservices and legacy systems.

## Other Important Libraries

- **HTTP(S) Libraries**: Akka-http, Finch, Sttp, Http4s, etc.
- **JSON Libraries**: Argonaut, Circe, Json4s, Play-JSON, etc.
- **Serialization**: ScalaPB.
- **Science and Data Analysis**: Algebird, Spire, Squants, etc.
- **Big Data**: Apache Spark and Apache Flink.
- **AI and Machine Learning**: BigDL (Distributed Deep Learning Framework) and TensorFlow Scala.
- **Functional Programming & FRP**: FP: Cats, Zio and FRP: fs2, Monix.
- **Build Tools**: sbt, Gradle, and Mill.
