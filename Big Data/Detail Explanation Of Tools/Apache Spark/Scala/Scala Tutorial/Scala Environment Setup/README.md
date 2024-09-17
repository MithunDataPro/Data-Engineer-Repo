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

---

## Step 2: Set Your Java Environment

Set the environment variable `JAVA_HOME` to point to the base directory location where Java is installed on your machine. For example:

| Sr.No | Platform & Description                                         |
|-------|----------------------------------------------------------------|
| 1     | **Windows**: Set `JAVA_HOME` to `C:\ProgramFiles\java\jdk1.7.0_60` |
| 2     | **Linux**: Export `JAVA_HOME=/usr/local/java-current`           |

Append the full path of Java compiler location to the System Path.

| Sr.No | Platform & Description                                                      |
|-------|-----------------------------------------------------------------------------|
| 1     | **Windows**: Append the string `"C:\Program Files\Java\jdk1.7.0_60\bin"` to the end of the system variable PATH. |
| 2     | **Linux**: Export `PATH=$PATH:$JAVA_HOME/bin/`                              |

Execute the command `java -version` from the command prompt as explained above.

---

# Step 3: Install Scala

You can download Scala from [Scala Downloads](http://www.scala-lang.org/downloads). At the time of writing this tutorial, I downloaded `scala-2.11.5-installer.jar`. Make sure you have admin privileges to proceed. Now, execute the following command at the command prompt:

| Platform | Command & Output                                    | Description                                                                                                                 |
|----------|------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| **Windows** | `>java –jar scala-2.11.5-installer.jar`            | This command will display an installation wizard, which will guide you to install Scala on your Windows machine. During installation, it will ask for a license agreement; simply accept it and it will further ask for a path where Scala will be installed. I selected the default path `C:\Program Files\Scala`, but you can choose a suitable path according to your convenience. |
| **Linux**   | Command: `$java –jar scala-2.9.0.1-installer.jar`  | Output: Welcome to the installation of Scala 2.9.0.1! The homepage is at [Scala-lang.org](http://Scala-lang.org/). During installation, it will ask for a license agreement. To accept it, type `1` and it will ask for a path where Scala will be installed. I entered `/usr/local/share`, but you can select a suitable path as per your convenience. |


#### For example, in Windows −

![image](https://github.com/user-attachments/assets/cb61358a-8c49-47e3-b212-73cfbc8e80c3)

Finally, open a new command prompt and type Scala -version and press Enter. You should see the following −

| Platform | Command           | Output                                                                 |
|----------|-------------------|------------------------------------------------------------------------|
| **Windows** | \>scala -version  | Scala code runner version 2.11.5 -- Copyright 2002-2013, LAMP/EPFL     |
| **Linux**   | $scala -version   | Scala code runner version 2.9.0.1 – Copyright 2002-2013, LAMP/EPFL     |

---

For example, in **Windows**:

```
C:\Windows\System32>scala --version
Scala code runner version 3.3.1 -- Copyright 2002-2023, LAMP/EPFL

C:\Windows\System32>

```

![image](https://github.com/user-attachments/assets/87de5f59-4c5a-47d5-bd21-62d25b48f73d)


## Testing and Running Scala using Commands

You can open cmd and run these commands to execute them. For example, in Windows −

```
Microsoft Windows [Version 10.0.22621.2283]
(c) Microsoft Corporation. All rights reserved.

C:\Users\Jai Shree Mithlesh>scala --version
Scala code runner version 3.3.1 -- Copyright 2002-2023, LAMP/EPFL

C:\Users\Jai Shree Mithlesh>scala
Welcome to Scala 3.3.1 (21.0.1, Java Java HotSpot(TM) 64-Bit Server VM).
Type in expressions for evaluation. Or try :help.

scala> println("Hello, tutorialspoint")
Hello, tutorialspoint

scala> 4+5
val res0: Int = 9

scala> 10/6
val res1: Int = 1

scala>

```

**Note** that you can also use Scala on various IDEs, like IntelliJ and VSCode with metals.
