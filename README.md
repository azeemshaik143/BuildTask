 Java Web Application: Build & Deploy Guide (Java 17 + Maven + Tomcat)

## Overview
This project is a **Java Web Application** designed to run on **Java 17**, built using **Maven**, and deployed on **Apache Tomcat**. The project demonstrates a basic Java web app structure, with a simple calculator implementation.

## Project Structure
```bash
JavaWebCalculator/
├── pom.xml
├── src/
│   ├── main/
│   │   ├── java/mypackage/Calculator.java
│   │   └── webapp/
│   │       ├── WEB-INF/web.xml
│   │       └── index.jsp
│   └── test/java/mypackage/CalculatorTest.java

```

- **pom.xml**: Maven project configuration.
- **Calculator.java**: Java class for your calculator logic.
- **index.jsp**: The homepage of the web application.
- **web.xml**: Web application configuration.
- **CalculatorTest.java**: Unit tests for the calculator.

## Prerequisites

creating servers for build and deploy

<img width="1307" height="506" alt="Image" src="https://github.com/user-attachments/assets/34f18af6-2154-4d55-8304-fab1dfcc8370" />
<img width="929" height="581" alt="Image" src="https://github.com/user-attachments/assets/8e67cc12-fff1-4236-8e7f-f2b01b7b3fda" />
<img width="957" height="472" alt="Image" src="https://github.com/user-attachments/assets/7a607877-3a22-43d8-a5f5-d49c80dee395" />
<img width="1320" height="515" alt="Image" src="https://github.com/user-attachments/assets/db33f384-cb3b-469b-ae5e-3e4feb54bcab" />
<img width="1051" height="468" alt="Image" src="https://github.com/user-attachments/assets/a53bf23d-9208-4d53-b19e-eece20bb2dd0" />

### Step 1: Install Java 17

To install Java 17, run the following commands (for Ubuntu/Debian):

```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
```
<img width="992" height="411" alt="Image" src="https://github.com/user-attachments/assets/9c0246a6-4dee-4dd5-aa92-b854e37c1e0e" />
<img width="1101" height="518" alt="Image" src="https://github.com/user-attachments/assets/0a2ab9b1-46b8-4423-8422-ea28efaa8e03" />
## java -version
### Output should be something like:
### openjdk version "17.0.x"...

## Install Maven
```bash
sudo apt install maven -y
```
<img width="878" height="496" alt="Image" src="https://github.com/user-attachments/assets/ebb2f9f5-ae90-41cc-8af9-0057f408f6e1" />
## Verify Maven installation
```bash
mvn -v
```

## Install Apache Tomcat
```bash
wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.110/bin/apache-tomcat-9.0.110.tar.gz
tar -xvzf apache-tomcat-9.0.110.tar.gz
```
<img width="711" height="432" alt="Image" src="https://github.com/user-attachments/assets/57945a3b-e95b-4c25-99b9-bf7df831e13e" />
<img width="1346" height="352" alt="Image" src="https://github.com/user-attachments/assets/a75c5861-a6fe-4660-9d28-1e12b4e4f5e1" />
## Add Tomcat User for Manager Access
```bash
sudo vi tomcat/conf/tomcat-users.xml
```
<img width="897" height="305" alt="Image" src="https://github.com/user-attachments/assets/1b013a57-b162-4d84-a583-e161453981f5" />
<img width="1329" height="428" alt="Image" src="https://github.com/user-attachments/assets/00ab1141-a0fd-4f3e-98b8-2d53872de5a5" />
## Add the following inside <tomcat-users>
```bash
<role rolename="manager-gui"/>
<role rolename="manager-script"/>
<user username="admin" password="admin123" roles="manager-gui,manager-script"/>
```
## Edit the context.xml file to allow remote access
```bash
sudo vi tomcat/webapps/manager/META-INF/context.xml
```
<img width="1084" height="584" alt="Image" src="https://github.com/user-attachments/assets/0500bef7-ab85-4846-a6f7-14e355487144" />
## Comment out the IP restriction
```bash
<!--
<Valve className="org.apache.catalina.valves.RemoteAddrValve"
       allow="127\.\d+\.\d+\.\d+|::1" />
-->
```
## Update pom.xml for Java 17 is available in the pom.xml file in this repository

## Clean and Package the Application
### Navigate to your project directory
```bash
cd JavaWebCalculator
```
### Run the following Maven command to clean and package your application
```bash
mvn clean package
```

## Deploy the WAR to Apache Tomcat
### Option 1: Deploy via Manager Web Interface

### Go to: http://localhost:8080/manager/html

### Login using your admin/admin123 credentials.

### In the Deploy section, upload the .war file: target/webapp-0.2.war.

### Click Deploy.

## Deploy the WAR to Apache Tomcat
Transfer the WAR File to the Deploy Server
<img width="1236" height="232" alt="Image" src="https://github.com/user-attachments/assets/f4a6454c-66f1-4b29-b72d-74adc31e72f4" />
<img width="1003" height="505" alt="Image" src="https://github.com/user-attachments/assets/c7aa6c81-391d-4b72-9f28-3d134a376763" />


## Test the Application
Open your browser and visit:

http://localhost:8080/webapp

<img width="934" height="641" alt="Image" src="https://github.com/user-attachments/assets/46559ae5-6554-4fdb-8d5d-b963f026cf8f" />

You should see the index.jsp page of your web application.

