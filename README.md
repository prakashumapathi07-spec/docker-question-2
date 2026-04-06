# docker-question-2

enable docker desktop in Kubernetes
step 2:  install docker and docker pipline in jenkins
step 3:  create a floder in user in "simple-app-java"
step 4:  create a App.java and pom.xml in that
step 5:  
public class App {
 public static void main(String[] args) throws Exception {
 System.out.println("Java CI/CD Application Started...");
 while (true) {
 Thread.sleep(5000);
 System.out.println("Hello from Java CI/CD Pipeline!");
 }
 }
}
***********************
pom.xml
***********************
<project xmlns="http://maven.apache.org/POM/4.0.0"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
 http://maven.apache.org/xsd/maven-4.0.0.xsd">
 <modelVersion>4.0.0</modelVersion>
 <groupId>com.demo</groupId>
 <artifactId>simple-java-app</artifactId>
 <version>1.0</version>
 <build>
 <plugins>
 <plugin>
 <groupId>org.apache.maven.plugins</groupId>
 <artifactId>maven-compiler-plugin</artifactId>
 <version>3.10.1</version>
 <configuration>
 <source>17</source>
 <target>17</target>
 </configuration>
 </plugin>
 </plugins>
 </build>
</project>
***********************


step 6:  command on 2 files "mvn clean package"

step 7: ADD Dockerfile and Deployment
FROM eclipse-temurin:17-jdk
WORKDIR /app
COPY target/simple-java-app-1.0.jar app.jar
CMD ["java", "-jar", "app.jar"]
*******************
step 8 : add deployment


