SBT stands for **Simple Build Tool**. SBT is a very popular and most used build tool in the Scala community for a while. Its broad acceptance and range of features make it the clear choice for any Scala project. One big reason SBT is popular is that the build definition is in Scala.

## SBT Installation

Just like **Maven**, you can download SBT as a compressed folder. Installation is only about uncompressing it. Aside from unzipping, SBT can also be installed using various tools depending on your platform. ForMac: use brew and for Debian Linux use SDKMAN. On Windows use the MSI installer to install SBT.

First Project
You can create a basic project using giter8 after installing SBT on your computer.

To begin, run the command −

```
sbt new scala/scala-seed.g8

```

According to giter8 instructions, a new project directory is generated. The project directory consists −

```

myProject/
   project/
      build.properties
   src/
      main/
         resources/
         scala/
      test/
         resources/
         scala/
   build.sbt

```

To view project/build.properties file, open the file with: `$ cat project/build.properties`

The content should be −

```
sbt.version = 1.8.2

```

You can also modify `sbt.version` to change the SBT version for your project's build. So, you ensure that everyone collaborating on the project uses the same SBT version for their builds. Next, run the sbt launcher and check the sbt version. If the SBT version 1.8.2 was available locally, the SBT launcher will download it automatically.

## SBT Workflow

To execute SBT commands, either enter SBT shell with SBT command or prefix each command with sbt. We will use second approach and prefix each command with sbt here. We will discuss most frequent SBT tasks.

### Compile

For compiling and checking for errors, use the `compile` command. For example,

```
sbt compile
[info] welcome to sbt 1.8.2 (AdoptOpenJDK Java 11.0.12)
// more logs
[success] Total time: 2 s, completed Nov 9, 2023, 3:30:15 PM

```

### Test Compile

You can compile test classes using test:compile command. SBT compiles the non-test classes before test classes. Run the test:compile command −

```
sbt test:compile
[info] welcome to sbt 1.8.2 (AdoptOpenJDK Java 11.0.12)
[info] compiling 1 Scala source to /myProject/target/scala-2.13/classes ...
[info] compiling 1 Scala source to /myProject/target/scala-2.13/test-classes ...
[success] Total time: 3 s, completed Nov 9, 2023, 3:35:20 PM

```

### Test

As in the above directory structure, /src/test/scala/ is the standard place for test sources. The giter8 template already includes a HelloSpec. For example,

```

sbt test
[info] welcome to sbt 1.8.2 (AdoptOpenJDK Java 11.0.12)
// more logs
[info] HelloSpec:
[info] The Hello object
[info] - should say hello
[info] Run completed in 212 milliseconds.
[info] Total number of tests run: 1
[info] Suites: completed 1, aborted 0
[info] Tests: succeeded 1, failed 0, canceled 0, ignored 0, pending 0
[info] All tests passed.
[success] Total time: 1 s, completed Nov 9, 2023, 3:40:35 PM

```

### Run

You can use the run command to execute the main function of the project. You can configure the main function with the mainClass property or extend scala.App trait. The giter8 template includes a class that extends scala.App trait. For example,

```
sbt run
[info] welcome to sbt 1.8.2 (AdoptOpenJDK Java 11.0.12)
// more logs
[info] running com.example.MyApp 
Hello, Scala!
[success] Total time: 0 s, completed Nov 9, 2023, 3:45:20 PM

```

Software engineers put tools through various tests. They will run commands from multiple main classes. For example,

```
sbt run
[info] welcome to sbt 1.8.2 (AdoptOpenJDK Java 11.0.12)
// more logs
Multiple main classes detected. Select one to run:
 [1] com.example.MyApp
 [2] com.example.AnotherApp

Enter number: 2
[info] running com.example.AnotherApp 
Greetings from AnotherApp!
[success] Total time: 278 s (04:38), completed Nov 9, 2023, 4:15:45 PM

```

### Clean

You can use the `clean` command to delete the previously generated target directories. For example,

```
sbt clean
[info] welcome to sbt 1.8.2 (AdoptOpenJDK Java 11.0.12)
// more logs
[success] Total time: 0 s, completed Nov 9, 2023, 4:20:15 PM

```

---

## The build.sbt File

The build.sbt file outlines everything in the build process.It is similar to Maven pom.xml for projects. We will discuss its most frequently used concepts.

### Library Dependencies

You can use zzlibraryDependencies key to include more libraries. For example,

```
// Single library
libraryDependencies += "org.scalatestplus.play" %% "scalatestplus-play" % "5.0.0" % Test

// Multiple libraries
libraryDependencies ++= Seq(
   "org.scalatestplus.play" %% "scalatestplus-play" % "5.0.0" % Test,
   "org.mockito" % "mockito-core" % "3.5.13" % Test
)

```

### Tasks

Tasks give values and are referred to by a key. These can produce values of any Scala type. Consider this basic task that prints "hello" to the console −

```
lazy val greetWorld = taskKey[Unit]("Prints 'Hello, World!'")

greetWorld := println("Hello, World!")

```

Now, run this greetWorld task −

```
sbt greetWorld
[info] welcome to sbt 1.8.2 (AdoptOpenJDK Java 11.0.12)
// more logs
Hello, World!
[success] Total time: 0 s, completed Nov 9, 2023, 5:00:15 PM

```

Tasks can take other tasks and attributes as input. For example, create a task that multiplies the value of another task −

```
lazy val two = taskKey[Int]("two")
two := 2

lazy val twoTimesThree = taskKey[Unit]("two times three")
twoTimesThree := println(s"2 * 3 = ${2 * three.value}")

```

Now, run this twoTimesThree task −

```
sbt twoTimesThree
[info] welcome to sbt 1.8.2 (AdoptOpenJDK Java 11.0.12)
// more logs
2 * 3 = 6
[success] Total time: 0 s, completed Nov 9, 2023, 5:20:45 PM

```

### Commands

Commands are named operations that take the current build state as argument and calculate new state. Although command and task definitions seem similar. But commands are more powerful. They can access and even modify state.

Create a command that alters the state and adds another command to it −

```
lazy val greetCommand = Command.command("greetCommand") { state =>
   println("Greetings from custom command!")
   state
}

lazy val addGreetCommand = Command.command("addGreetCommand") { state =>
   println("Adding greetCommand to defined commands.")
   state.copy(definedCommands = state.definedCommands :+ greetCommand)
}

lazy val root = (project in file("."))
.settings(
   // other settings ..
   commands ++= Seq(addGreetCommand)
)

```

Note that greetCommand is not included in the project commands. This means helloCommand is not accessible until after calling addGreetCommand. For example, use the SBT shell to ensure the state is preserved −

```
sbt
[info] welcome to sbt 1.8.2 (AdoptOpenJDK Java 11.0.12)
// more logs
sbt:myProject> greetCommand
[error] Not a valid command: greetCommand (similar: addGreetCommand, reload)
[error] Not a valid project ID: greetCommand
[error] Expected ':'
[error] Not a valid key: greetCommand (similar: watchBeforeCommand, commands, addGreetCommand)
[error] greetCommand
[error]             ^
sbt:myProject> addGreetCommand
Adding greetCommand to defined commands.
sbt:myProject> greetCommand
Greetings from custom command!

```

### Command Aliases

If you want to run a group of tasks or commands together. You can use command aliases. For example, create alias that calls both compile and test −

```
addCommandAlias("buildAndTest", ";compile;test")

```
Now, run the sbt buildAndTest alias −

```
sbt buildAndTest
[info] welcome to sbt 1.8.2 (AdoptOpenJDK Java 11.0.12)
// compile logs
[success] Total time: 0 s, completed Nov 9, 2023, 6:15:20 PM
// test logs
[info] All tests passed.
[success] Total time: 3 s, completed Nov 9, 2023, 6:15:23 PM

```

### Resolvers
You can use the resolvers setting for adding repositories for SBT to find dependencies. For example, add Typesafe and Maven2 repositories −

```
resolvers ++= Seq(
   "Typesafe" at "https://repo.typesafe.com/typesafe/releases/",
   "Java.net Maven2 Repository" at "https://download.java.net/maven/2/"
)

```

### Plugins

SBT plugins primarily consist of build definitions. In simpler terms, plugins let us reuse code in our builds. You can include a new plugin in a project, define it in the project/plugins.sbt file. For example, add the scalafmt plugin to our project −

```
addSbtPlugin("org.scalameta" % "sbt-scalafmt" % "2.4.6")

```
