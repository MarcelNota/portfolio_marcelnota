# Personal Portfolio

A personal portfolio website built with **Java, Spring Boot and Thymeleaf** to showcase my professional background, technical skills, education and software development projects.

This project was also used as a practical exercise to understand how a Spring Boot application is built, packaged and deployed to a cloud environment.

## 🚀 Technologies

* Java 21
* Spring Boot
* Thymeleaf
* Maven
* HTML5
* CSS3
* Bootstrap
* Docker
* Git / GitHub

## 📌 Features

* Personal introduction
* Professional experience
* Technical skills
* Projects
* Education and certifications
* Contact information
* Responsive interface

## 🏗️ Architecture

The application follows the **Spring Boot MVC** architecture.

The general request flow is:

```text
Browser
   ↓
HTTP Request
   ↓
Spring Boot Controller
   ↓
Model
   ↓
Thymeleaf Template
   ↓
HTML Response
   ↓
Browser
```

For example, the controller maps the home page:

```java
@GetMapping({"/", "", "/home"})
public String showHomePage(Model model) {
    model.addAttribute("title", "Home");
    return "master";
}
```

The controller receives the HTTP request, adds data to the model and returns the Thymeleaf view that should be rendered.

## 📂 Project Structure

```text
src/
└── main/
    ├── java/
    │   └── com.marcelnota.portfolio/
    │       └── controller/
    │           └── HomeController.java
    │
    └── resources/
        ├── static/
        │   ├── css/
        │   ├── js/
        │   └── images/
        │
        └── templates/
            ├── master.html
            └── ...
```

### Controller

The controller is responsible for handling HTTP requests and selecting the appropriate view.

### Thymeleaf

Thymeleaf is used as the server-side template engine. It allows data provided by Spring Boot to be inserted dynamically into HTML.

Example:

```html
<h1 th:text="${title}"></h1>
```

## 📦 Build Process

The application uses **Maven** to compile the source code, run the build lifecycle and package the Spring Boot application.

The Maven Wrapper can be used to build the project:

```bash
./mvnw clean package
```

For the deployment build, tests were skipped:

```bash
./mvnw clean package -DskipTests
```

The result is an executable Spring Boot **JAR file**, which can be run with Java.

```text
Source Code
     ↓
   Maven
     ↓
 Spring Boot JAR
```

## 🐳 Why Docker Was Used

Docker was introduced during deployment because the deployment platform I selected did **not provide a direct deployment option for Java/Spring Boot applications**.

Instead of deploying the Spring Boot application through a native Java runtime option, the application was packaged into a Docker image.

This allowed the deployment platform to run the application as a container.

The resulting deployment flow was:

```text
Spring Boot Application
          ↓
         Maven
          ↓
       JAR File
          ↓
      Dockerfile
          ↓
     Docker Image
          ↓
   Docker Container
          ↓
      Deployment
```

Docker was therefore used as a **deployment and portability solution**, allowing the Java application to run in an environment that supported containerized applications.

## 🐳 Docker

A Docker image contains the application and the instructions required to run it.

A container is a running instance of that image.

For this project, the important distinction is:

```text
Dockerfile
    ↓
Docker Image
    ↓
Docker Container
```

The **Dockerfile** defines how the image is created.

The **image** is the packaged application.

The **container** is the running application based on that image.

## ▶️ Running Locally

Clone the repository:

```bash
git clone https://github.com/MarcelNota/<repository-name>.git
```

Enter the project directory:

```bash
cd <repository-name>
```

Run the application using Spring Boot:

```bash
./mvnw spring-boot:run
```

The application will be available at:

```text
http://localhost:8080
```

## 🧱 Building the JAR

```bash
./mvnw clean package
```

The generated JAR will be placed inside:

```text
target/
```

It can then be executed with:

```bash
java -jar target/<application-name>.jar
```

## 🐳 Running with Docker

Build the Docker image:

```bash
docker build -t portfolio .
```

Run a container:

```bash
docker run -p 8080:8080 portfolio
```

Then access:

```text
http://localhost:8080
```

The `-p 8080:8080` option maps port `8080` from the Docker container to port `8080` on the local machine.

## ☁️ Deployment

The application was deployed using a container-based deployment approach.

Because the selected deployment platform did not offer native Java/Spring Boot deployment, Docker was used to package the application in a format supported by the platform.

The deployment process can be summarized as:

```text
GitHub Repository
       ↓
Build Spring Boot Application
       ↓
Create Docker Image
       ↓
Push/Deploy Container
       ↓
Application Available Online
```

## 🎯 Purpose of the Project

The main purpose of this project was to create my personal developer portfolio while gaining practical experience with the complete application lifecycle:

* Developing a Spring Boot application
* Understanding MVC architecture
* Using Thymeleaf for server-side rendering
* Managing dependencies and builds with Maven
* Packaging a Java application as a JAR
* Understanding Docker images and containers
* Deploying a containerized Java application

## 👨‍💻 About Me

I am a **Backend Engineer** focused on developing backend applications using **Java, Spring Boot, REST APIs, databases and microservices**.

This portfolio presents my professional background, technical skills and software development projects.

## 📫 Contact

**GitHub:**
https://github.com/MarcelNota

---

⭐ Feel free to explore the repository and check out my other software development projects.
