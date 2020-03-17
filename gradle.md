```
✔ ~/spring-demo [master L|✔]
22:28 $ gradle tasks
Starting a Gradle Daemon (subsequent builds will be faster)

> Task :tasks

------------------------------------------------------------
Tasks runnable from root project
------------------------------------------------------------

Application tasks
-----------------
bootRun - Runs this project as a Spring Boot application.

Build tasks
-----------
assemble - Assembles the outputs of this project.
bootJar - Assembles an executable jar archive containing the main classes and their dependencies.
build - Assembles and tests this project.
buildDependents - Assembles and tests this project and all projects that depend on it.
buildNeeded - Assembles and tests this project and all projects it depends on.
classes - Assembles main classes.
clean - Deletes the build directory.
jar - Assembles a jar archive containing the main classes.
testClasses - Assembles test classes.

Build Setup tasks
-----------------
init - Initializes a new Gradle build.
wrapper - Generates Gradle wrapper files.

Documentation tasks
-------------------
javadoc - Generates Javadoc API documentation for the main source code.

Help tasks
----------
buildEnvironment - Displays all buildscript dependencies declared in root project 'demo'.
components - Displays the components produced by root project 'demo'. [incubating]
dependencies - Displays all dependencies declared in root project 'demo'.
dependencyInsight - Displays the insight into a specific dependency in root project 'demo'.
dependencyManagement - Displays the dependency management declared in root project 'demo'.
dependentComponents - Displays the dependent components of components in root project 'demo'. [incubating]
help - Displays a help message.
model - Displays the configuration model of root project 'demo'. [incubating]
projects - Displays the sub-projects of root project 'demo'.
properties - Displays the properties of root project 'demo'.
tasks - Displays the tasks runnable from root project 'demo'.

Verification tasks
------------------
check - Runs all checks.
test - Runs the unit tests.

Rules
-----
Pattern: clean<TaskName>: Cleans the output files of a task.
Pattern: build<ConfigurationName>: Assembles the artifacts of a configuration.
Pattern: upload<ConfigurationName>: Assembles and uploads the artifacts belonging to a configuration.

To see all tasks and more detail, run gradle tasks --all

To see more detail about a task, run gradle help --task <task>

BUILD SUCCESSFUL in 28s
1 actionable task: 1 executed
✔ ~/spring-demo [master L|✔]
22:29 $
✔ ~/spring-demo [master L|✔]
22:29 $ ls -la
合計 44
drwxrwxr-x   7 newgen newgen  237  3月 17 22:28 .
drwx------. 45 newgen newgen 4096  3月 17 20:13 ..
drwxrwxr-x   8 newgen newgen  201  3月 17 20:13 .git
-rw-rw-r--   1 newgen newgen  341  3月 16 21:50 .gitignore
-rw-rw-r--   1 newgen newgen 1309  3月 17 19:43 .gitlab-ci.yml
drwxrwxr-x   5 newgen newgen   58  3月 17 22:29 .gradle
-rw-rw-r--   1 newgen newgen  188  3月 16 21:50 Dockerfile
-rw-rw-r--   1 newgen newgen   39  3月 17 20:13 README.md
drwxrwxr-x   3 newgen newgen   19  3月 16 21:50 bin
-rw-rw-r--   1 newgen newgen  606  3月 16 21:50 build.gradle
drwxrwxr-x   3 newgen newgen   21  3月 16 21:50 gradle
-rwxrwxr-x   1 newgen newgen 5296  3月 16 21:50 gradlew
-rw-rw-r--   1 newgen newgen 2176  3月 16 21:50 gradlew.bat
-rw-rw-r--   1 newgen newgen  308  3月 16 21:50 k8s.yaml
-rw-rw-r--   1 newgen newgen  384  3月 16 21:50 settings.gradle
drwxrwxr-x   4 newgen newgen   30  3月 16 21:50 src
✔ ~/spring-demo [master L|✔]
22:29 $ less build.gradle
✔ ~/spring-demo [master L|✔]
22:30 $
✔ ~/spring-demo [master L|✔]
22:30 $ gradle build

> Task :test
2020-03-17 22:31:37.767  INFO 21936 --- [       Thread-4] o.s.s.concurrent.ThreadPoolTaskExecutor  : Shutting down ExecutorService 'applicationTaskExecutor'

BUILD SUCCESSFUL in 39s
5 actionable tasks: 5 executed
✔ ~/spring-demo [master L|✔]
22:31 $ tree
.
├── Dockerfile
├── README.md
├── bin
│   └── local
│       └── tetsuya
│           └── oc4cluster
│               └── apps
│                   └── demo
│                       ├── DemoApplication.class
│                       └── DemoApplicationTests.class
├── build
│   ├── classes
│   │   └── java
│   │       ├── main
│   │       │   └── local
│   │       │       └── tetsuya
│   │       │           └── oc4cluster
│   │       │               └── apps
│   │       │                   └── demo
│   │       │                       ├── DemoApplication.class
│   │       │                       └── controllers
│   │       │                           └── HelloController.class
│   │       └── test
│   │           └── local
│   │               └── tetsuya
│   │                   └── oc4cluster
│   │                       └── apps
│   │                           └── demo
│   │                               └── DemoApplicationTests.class
│   ├── generated
│   │   └── sources
│   │       └── annotationProcessor
│   │           └── java
│   │               ├── main
│   │               └── test
│   ├── libs
│   │   └── demo-0.0.1-SNAPSHOT.jar
│   ├── reports
│   │   └── tests
│   │       └── test
│   │           ├── classes
│   │           │   └── local.tetsuya.oc4cluster.apps.demo.DemoApplicationTests.html
│   │           ├── css
│   │           │   ├── base-style.css
│   │           │   └── style.css
│   │           ├── index.html
│   │           ├── js
│   │           │   └── report.js
│   │           └── packages
│   │               └── local.tetsuya.oc4cluster.apps.demo.html
│   ├── resources
│   │   └── main
│   │       ├── application.properties
│   │       ├── static
│   │       │   └── index.html
│   │       └── templates
│   │           └── hello.html
│   ├── test-results
│   │   └── test
│   │       ├── TEST-local.tetsuya.oc4cluster.apps.demo.DemoApplicationTests.xml
│   │       └── binary
│   │           ├── output.bin
│   │           ├── output.bin.idx
│   │           └── results.bin
│   └── tmp
│       ├── bootJar
│       │   └── MANIFEST.MF
│       ├── compileJava
│       └── compileTestJava
├── build.gradle
├── gradle
│   └── wrapper
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
├── gradlew
├── gradlew.bat
├── k8s.yaml
├── settings.gradle
└── src
    ├── main
    │   ├── java
    │   │   └── local
    │   │       └── tetsuya
    │   │           └── oc4cluster
    │   │               └── apps
    │   │                   └── demo
    │   │                       ├── DemoApplication.java
    │   │                       └── controllers
    │   │                           └── HelloController.java
    │   └── resources
    │       ├── application.properties
    │       ├── static
    │       │   └── index.html
    │       └── templates
    │           └── hello.html
    └── test
        └── java
            └── local
                └── tetsuya
                    └── oc4cluster
                        └── apps
                            └── demo
                                └── DemoApplicationTests.java


```
