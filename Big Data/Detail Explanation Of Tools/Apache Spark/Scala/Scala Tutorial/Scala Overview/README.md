# Introduction to Scala

**Scala**, short for **Scalable Language**, is a hybrid functional programming language. It was created by **Martin Odersky**. Scala smoothly integrates the features of object-oriented and functional languages. Scala is compiled to run on the **Java Virtual Machine** (JVM). Many companies that depend on Java for business-critical applications are turning to Scala to boost their development productivity, application scalability, and overall reliability.

---

## Key Features of Scala

### 1. Scala is Object-Oriented
Scala is a pure object-oriented language in the sense that every value is an object. The types and behavior of objects are described by classes and traits, which will be explained in subsequent chapters.

- Classes are extended by subclassing.
- A flexible mixin-based composition mechanism serves as a clean replacement for multiple inheritance.

### 2. Scala is Functional
Scala is also a functional language, as every function is a value, and every value is an object, so ultimately every function is an object.

- Scala provides a lightweight syntax for defining **anonymous functions**.
- It supports **higher-order functions**.
- Functions can be **nested** and **curried**. These concepts will be covered in subsequent chapters.

### 3. Scala is Statically Typed
Unlike some other statically typed languages (C, Pascal, Rust, etc.), Scala does not expect you to provide redundant type information. In most cases, you don't have to specify a type, and you certainly don't have to repeat it.

### 4. Scala Runs on the JVM
Scala is compiled into **Java Byte Code**, which is executed by the **Java Virtual Machine (JVM)**. This means that Scala and Java share a common runtime platform, allowing for easy migration from Java to Scala.

- The Scala compiler compiles your Scala code into Java Byte Code.
- The `scala` command (similar to the `java` command) executes the compiled Scala code.

### 5. Scala Can Execute Java Code
Scala enables you to use all the classes of the **Java SDK**, as well as your own custom Java classes or your favorite Java open-source projects.

### 6. Scala Supports Concurrent and Synchronized Processing
Scala allows you to express general programming patterns effectively. It reduces the number of lines of code and enables the programmer to write type-safe code. Scala's immutability makes it easy to apply **concurrency** and **parallelism** (synchronization).

---

## Scala vs Java

Scala has a set of features that distinguish it from Java. Some of these are:

- **All types are objects**
- **Type inference**
- **Nested functions**
- **Functions are objects**
- **Domain-Specific Language (DSL) support**
- **Traits**
- **Closures**
- **Concurrency support inspired by Erlang**

---

## Scala Web Frameworks

Scala is widely used, especially in **enterprise web applications**. Below are some of the most popular Scala web frameworks:

- **The Lift Framework**
- **The Play Framework**
- **The Bowler Framework**
