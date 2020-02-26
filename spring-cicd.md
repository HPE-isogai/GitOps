## Prepare Java Program
http://10.0.0.130/tetsuya.isogai/spring-demo/tree/master

<details>
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

</details>

## Change Java Code


## Java build
```
./gradlew build
```

* Confirm the result
```
$ java -jar build/libs/demo-0.0.1-SNAPSHOT.jar

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::  (v2.1.13.BUILD-SNAPSHOT)

2020-02-26 10:27:23.030  INFO 14860 --- [           main] l.t.o.apps.demo.DemoApplication          : Starting DemoApplication on bastion01 with PID 14860 (/home/newgen/spring-demo/build/libs/demo-0.0.1-SNAPSHOT.jar started by newgen in /home/newgen/spring-demo)
2020-02-26 10:27:23.034  INFO 14860 --- [           main] l.t.o.apps.demo.DemoApplication          : No active profile set, falling back to default profiles: default
2020-02-26 10:27:25.556  INFO 14860 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port(s): 8080 (http)
2020-02-26 10:27:25.624  INFO 14860 --- [           main] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2020-02-26 10:27:25.628  INFO 14860 --- [           main] org.apache.catalina.core.StandardEngine  : Starting Servlet engine: [Apache Tomcat/9.0.31]
2020-02-26 10:27:25.786  INFO 14860 --- [           main] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2020-02-26 10:27:25.786  INFO 14860 --- [           main] o.s.web.context.ContextLoader            : Root WebApplicationContext: initialization completed in 2655 ms
2020-02-26 10:27:26.334  INFO 14860 --- [           main] o.s.s.concurrent.ThreadPoolTaskExecutor  : Initializing ExecutorService 'applicationTaskExecutor'
2020-02-26 10:27:26.457  INFO 14860 --- [           main] o.s.b.a.w.s.WelcomePageHandlerMapping    : Adding welcome page: class path resource [static/index.html]
2020-02-26 10:27:26.752  INFO 14860 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port(s): 8080 (http) with context path ''
2020-02-26 10:27:26.759  INFO 14860 --- [           main] l.t.o.apps.demo.DemoApplication          : Started DemoApplication in 4.99 seconds (JVM running for 5.788)
```

## Create Dockerfile
```
FROM openjdk:11.0.5-jre
#RUN addgroup -S spring && adduser -S spring -G spring
#USER spring:spring
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```
* Make sure the proper jdk version from `dockerhub`

## Docker build
```
docker build --build-arg JAR_FILE=build/libs/*.jar -t springio/gs-spring-boot-docker .
```

* Confirm
```
$ docker image ls
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
springio/gs-spring-boot-docker          latest              3c0c9919a4d9        35 hours ago        285MB
openjdk                                 11.0.5-jre          0bf8ab4c4d20        8 weeks ago         267MB
```

## Push Docker image to registry
docker tag springio/gs-spring-boot-docker:latest 10.0.0.131:5000/gs-spring-boot-docker:0.1
docker push 10.0.0.131:5000/gs-spring-boot-docker:0.1

## Create CI yaml
```
$ cat .gitlab-ci.yml
stages:
  - deploy
  - test

variables:
  DOCKER_REG_URL: "10.0.0.131:5000"
  DOCKER_REG_USER: "<user>"
  DOCKER_REG_PASS: "<pass>"
  IMAGE_TAG_ID: "0.1"
  DOCKER_IMAGE_TAG: spring-demo:$IMAGE_TAG_ID

deploy:
  stage: deploy
  script:
    - oc version --client
    - oc --kubeconfig=/var/gitlab/cert/kubeconfig get node
    - oc new-app 10.0.0.131:5000/gs-spring-boot-docker:0.1 --insecure-registry=true --kubeconfig=/var/gitlab/cert/kubeconfig

test:
  stage: test
  script:
    - oc get dc gs-spring-boot-docker --kubeconfig=/var/gitlab/cert/kubeconfig
    - oc rollout status dc/gs-spring-boot-docker --kubeconfig=/var/gitlab/cert/kubeconfig
    - oc expose dc/gs-spring-boot-docker --port=8080 --kubeconfig=/var/gitlab/cert/kubeconfig
    - oc expose svc/gs-spring-boot-docker  --kubeconfig=/var/gitlab/cert/kubeconfig
    - oc get route gs-spring-boot-docker --kubeconfig=/var/gitlab/cert/kubeconfig
```

## Set kubeconfig in Gitlab server


## push code in Gitlab


## Tasks
Store Artifact into Nexus
https://medium.com/@simionrazvan/how-to-create-a-gradle-library-and-publish-it-on-nexus-34be19b520aa
https://blog.sonatype.com/using-nexus-3-as-your-repository-part-1-maven-artifacts
https://qiita.com/Toshimichi/items/fa17656f862ada2cfde4

1. Install `gradle`
https://linux4one.com/how-to-install-gradle-on-centos-7/
1. apply plugin
add `build.gradle`  
```
apply plugin: 'maven-publish'
```
add publish definition
```
publishing {
    publications {
        mavenJava(MavenPublication) {
            from components.java
            artifact sourceJar {
                classifier 'sources'
            }
        }
    }
    repositories {
        def properties = new Properties()
        file('secret.properties').withInputStream { properties.load(it) }
        maven {
            url properties.getProperty 'url'
            credentials {
                username = properties.getProperty 'username' 
                password = properties.getProperty 'password' 
            }
        }
    }
}
```
1. add property values into `secret.properties`
```
username=ユーザー名
password=パスワード
url=URL
```
1. Create Repository in Nexus
Create repository -> Maven2(group) -> "spring-demo" -> Add maven* to members 
