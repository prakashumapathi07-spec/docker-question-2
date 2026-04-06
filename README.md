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
***********************
apiVersion: apps/v1
kind: Deployment
metadata:
  name: java-app
spec:
  replicas: 1
  selector:
    matchLabels:
      app: java-app
  template:
    metadata:
      labels:
        app: java-app
    spec:
      containers:
      - name: java-app
        image: prakashraj007/java-app:latest
        ports:
        - containerPort: 8080

---
apiVersion: v1
kind: Service
metadata:
  name: java-service
spec:
  type: NodePort
  selector:
    app: java-app
  ports:
    - port: 80
      targetPort: 8080
      nodePort: 30007
      ******************
step 8: add all file in github
step 9 : kubernet CLI in jenkins 
Step 10: copy the file name **.Kube** in user to ProgramData//Jenkins -> **.Kube**
step 11: add crendential which is upoaded
final step : pipline script
************************

