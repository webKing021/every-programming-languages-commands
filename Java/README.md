# Java Commands Reference

## Java Development Kit (JDK) Commands

### Compilation

```bash
# Compile a Java file
javac HelloWorld.java

# Compile with classpath
javac -cp lib/dependency.jar HelloWorld.java

# Compile with specific Java version
javac -source 11 -target 11 HelloWorld.java

# Compile with debug information
javac -g HelloWorld.java

# Compile multiple files
javac File1.java File2.java File3.java

# Compile all Java files in directory
javac *.java

# Compile with specific encoding
javac -encoding UTF-8 HelloWorld.java

# Compile with warnings
javac -Xlint HelloWorld.java

# Compile with specific warnings
javac -Xlint:unchecked HelloWorld.java
```

### Execution

```bash
# Run a Java program
java HelloWorld

# Run with classpath
java -cp .:lib/dependency.jar HelloWorld

# Run with memory settings
java -Xms512m -Xmx1024m HelloWorld

# Run with system property
java -Dproperty=value HelloWorld

# Run with assertions enabled
java -ea HelloWorld

# Run with verbose garbage collection
java -verbose:gc HelloWorld

# Run with remote debugging enabled
java -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 HelloWorld
```

### JAR Files

```bash
# Create a JAR file
jar cf app.jar *.class

# Create a JAR file with manifest
jar cfm app.jar manifest.txt *.class

# View contents of a JAR file
jar tf app.jar

# Extract a JAR file
jar xf app.jar

# Run an executable JAR file
java -jar app.jar

# Update a JAR file
jar uf app.jar NewFile.class
```

### Documentation

```bash
# Generate Javadoc
javadoc -d docs *.java

# Generate Javadoc with specific packages
javadoc -d docs com.example.package1 com.example.package2

# Generate Javadoc with private members
javadoc -private -d docs *.java
```

### Debugging and Profiling

```bash
# List running Java processes
jps

# Detailed list of Java processes
jps -lv

# Java VisualVM (profiling tool)
jvisualvm

# Java Mission Control
jmc

# Heap dump of a running Java process
jmap -dump:format=b,file=heap.bin <pid>

# Thread dump of a running Java process
jstack <pid>

# JConsole (monitoring tool)
jconsole
```

## Build Tools

### Maven

```bash
# Create a new Maven project
mvn archetype:generate -DgroupId=com.example -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

# Compile a Maven project
mvn compile

# Run tests
mvn test

# Package a Maven project
mvn package

# Install to local repository
mvn install

# Clean the project
mvn clean

# Clean and package
mvn clean package

# Run with specific profile
mvn -P profile-name package

# Skip tests
mvn package -DskipTests

# Show dependency tree
mvn dependency:tree

# Generate site documentation
mvn site
```

### Gradle

```bash
# Initialize a Gradle project
gradle init

# Build a Gradle project
gradle build

# Run tests
gradle test

# Clean the project
gradle clean

# Clean and build
gradle clean build

# Run a specific task
gradle taskName

# List available tasks
gradle tasks

# Show dependencies
gradle dependencies

# Run with specific profile
gradle -Pprofile=dev build

# Run with debug
gradle --debug build
```

## Spring Boot

```bash
# Create a Spring Boot project with Spring Initializr
curl https://start.spring.io/starter.zip -d dependencies=web,data-jpa -d type=maven-project -d bootVersion=2.7.0 -o demo.zip

# Run a Spring Boot application
./mvnw spring-boot:run

# Run with specific profile
./mvnw spring-boot:run -Dspring-boot.run.profiles=dev

# Package a Spring Boot application
./mvnw package

# Run the packaged application
java -jar target/myapp-0.0.1-SNAPSHOT.jar

# Run with specific profile
java -jar -Dspring.profiles.active=prod target/myapp-0.0.1-SNAPSHOT.jar
```

## JUnit

```bash
# Run JUnit tests with Maven
mvn test

# Run specific test class
mvn -Dtest=TestClassName test

# Run specific test method
mvn -Dtest=TestClassName#testMethodName test
```

## Java Enterprise Edition (Jakarta EE)

```bash
# Deploy WAR file to Tomcat
cp myapp.war /path/to/tomcat/webapps/

# Deploy to WildFly/JBoss
/path/to/jboss/bin/jboss-cli.sh --connect --command="deploy /path/to/myapp.war"
```

## Database Connectivity

```bash
# Run a SQL script with JDBC
java -cp .:mysql-connector-java.jar:. -Djdbc.drivers=com.mysql.jdbc.Driver SqlTool script.sql
```

## Code Quality

```bash
# Run Checkstyle
java -jar checkstyle.jar -c /sun_checks.xml MyClass.java

# Run PMD
pmd check -d src/ -R rulesets/java/basic.xml -f text

# Run SpotBugs
java -jar spotbugs.jar -textui -effort:max -low myapp.jar
```

## Version Management

```bash
# List installed JDKs (macOS/Linux with SDKMAN)
sdk list java

# Install specific JDK version (with SDKMAN)
sdk install java 17.0.2-open

# Switch Java version (with SDKMAN)
sdk use java 17.0.2-open

# Set default Java version (with SDKMAN)
sdk default java 17.0.2-open
```

## Miscellaneous

```bash
# Check Java version
java -version
javac -version

# Display system properties
java -XshowSettings:properties -version

# List available fonts
java -cp . ListFonts

# Run Java with assertions enabled
java -ea MyClass

# Run Java with security manager
java -Djava.security.manager MyClass
```