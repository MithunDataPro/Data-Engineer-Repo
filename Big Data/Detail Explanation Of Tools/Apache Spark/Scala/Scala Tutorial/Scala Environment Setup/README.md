# Installing Scala

Scala can be installed on any UNIX-flavored or Windows-based system. Before you start installing Scala on your machine, you must have **Java 1.8 or greater** installed on your computer.

---

## Steps to Install Scala

### Step 1: Verify Your Java Installation

First of all, you need to have the **Java Software Development Kit (SDK)** installed on your system. To verify this, execute any of the following two commands depending on the platform you are working on.

If the Java installation has been done properly, then it will display the current version and specification of your Java installation. A sample output is given in the following table.

| **Platform** | **Command**                  | **Sample Output**                                                                                                                                      |
|--------------|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Windows**  | Open Command Console and type − | `>java –version`                                                                                                                                       |
|              |                              | Java version "1.8.0_31"                                                                                                                                |
|              |                              | Java (TM) SE Run Time Environment (build 1.8.0_31-b31)                                                                                                  |
|              |                              | Java Hotspot (TM) 64-bit Server VM (build 25.31-b07, mixed mode)                                                                                        |
| **Linux**    | Open Command terminal and type − | `$java –version`                                                                                                                                       |
|              |                              | Java version "1.8.0_31"                                                                                                                                |
|              |                              | Open JDK Runtime Environment (rhel-2.8.10.4.el6_4-x86_64)                                                                                               |
|              |                              | Open JDK 64-Bit Server VM (build 25.31-b07, mixed mode)                                                                                                |


We assume that the readers of this tutorial have **Java SDK version 1.8.0_31** installed on their system.

In case you do not have Java SDK, download its current version from [Java SE Downloads](http://www.oracle.com/technetwork/java/javase/downloads/index.html) and install it.

---

### Example: For Windows

```windows
C:\Windows\System32>java --version

```

This will be the **output** if Java is installed on your computer −

```
Microsoft Windows [Version 10.0.22621.2283]
(c) Microsoft Corporation. All rights reserved.

C:\Windows\System32>java --version
java 21.0.1 2023-10-17 LTS
Java(TM) SE Runtime Environment (build 21.0.1+12-LTS-29)
Java HotSpot(TM) 64-Bit Server VM (build 21.0.1+12-LTS-29, mixed mode, sharing)

C:\Windows\System32>

```

![image](https://github.com/user-attachments/assets/32df998d-61ac-4cec-a193-017f8911bce8)

### For Linux

```linux
$ java -version

```

This will be the output, if Java is installed on your computer −

```
java version "11.0.11"
Java(TM) SE Runtime Environment (build 11.0.11+9-LTS)
Java HotSpot(TM) 64-Bit Server VM (build 11.0.11+9-LTS, mixed mode)

```

If the Java installation has been done properly, it will display the current version and specification of your Java installation. If Java is not already installed on your computer, then there will be an error message.

## Step 2: Set Your Java Environment
Set the environment variable JAVA_HOME to point to the base directory location where Java is installed on your machine. For example,
