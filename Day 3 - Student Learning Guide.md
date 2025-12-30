# Day 3 - Student Learning Guide
## Creating Your First Spring Boot REST API

### 🎯 **What You'll Learn Today**
- What Spring Boot is and why it's amazing for building APIs
- How to create a complete Spring Boot project from scratch
- Building REST API endpoints that handle HTTP requests
- Testing your APIs professionally with Postman
- Connecting everything you learned on Days 1 & 2

---

## 📚 **Theory: Understanding Spring Boot & REST APIs**

### **What is Spring Boot?**

**Think of building an API like cooking in a kitchen:**

**Without Spring Boot** (Traditional Java):
- You need to buy and set up every single kitchen appliance
- Configure the stove, oven, refrigerator separately
- Wire the electricity and plumbing yourself
- Then finally start cooking

**With Spring Boot**:
- You get a fully equipped, ready-to-use kitchen
- Everything is pre-configured and working together
- You can start cooking (building features) immediately!

### **Why Companies Love Spring Boot:**

**Real-World Usage:**
- **Netflix:** Uses Spring Boot for their recommendation system
- **Airbnb:** Powers their booking and payment APIs  
- **Uber:** Handles millions of ride requests daily
- **LinkedIn:** Manages user profiles and connections

**Benefits for Developers:**
```
✅ Reduces development time by 70%
✅ Auto-configures everything for you
✅ Built-in security features
✅ Easy testing capabilities
✅ Production-ready monitoring
✅ Massive community support
```

### **REST API Concepts Review**

**From Day 2, remember:**
- **REST:** A style of building APIs that uses HTTP methods
- **Endpoint:** A specific URL where your API can be accessed
- **HTTP Methods:** GET (retrieve), POST (create), PUT (update), DELETE (remove)

**Today's Focus: GET Endpoints**
```
GET /hello              → Returns a simple greeting
GET /hello/{name}       → Returns personalized greeting  
GET /student/{id}       → Returns student information
GET /greet?name=John    → Returns greeting using query parameter
```

---

## 🛠 **Practical: Building Your First Spring Boot API**

### **Step 1: Create Spring Boot Project**

#### **Using Spring Boot Initializer (Recommended Method):**

**1. Go to Spring Boot Initializer:**
- Open browser: https://start.spring.io
- This is the official tool used by millions of developers worldwide

**2. Configure Your Project:**
```
Project: Maven Project
Language: Java
Spring Boot: 3.4.x (latest stable version)

Project Metadata:
├── Group: com.learning
├── Artifact: my-first-api
├── Name: my-first-api  
├── Description: My first Spring Boot REST API
├── Package name: com.learning.myfirstapi
├── Packaging: Jar
└── Java: 21
```

**3. Add Dependencies:**
Click "ADD DEPENDENCIES" and search for:
- **Spring Web** - For building REST APIs
- **Spring Boot DevTools** - For automatic restarts during development

**4. Generate Project:**
- Click "GENERATE" button
- Download will start automatically (file: my-first-api.zip)

**5. Extract and Open Project:**
```bash
# Extract the downloaded zip file
unzip my-first-api.zip

# Open in IntelliJ IDEA
# File → Open → Select the my-first-api folder
```

#### **Understanding Your Project Structure:**

```
my-first-api/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/learning/myfirstapi/
│   │   │       └── MyFirstApiApplication.java    # 🚀 Main application class
│   │   └── resources/
│   │       ├── static/                           # 📁 For CSS, JS, images
│   │       ├── templates/                        # 📄 For HTML templates
│   │       └── application.properties            # ⚙️ Configuration file
│   └── test/                                     # 🧪 Test files
├── target/                                       # 📦 Compiled files (auto-generated)
├── pom.xml                                       # 📋 Dependencies list
└── README.md                                     # 📖 Project documentation
```

**Key Files Explained:**
- **MyFirstApiApplication.java:** Starting point of your application
- **application.properties:** Configure database, port, etc.
- **pom.xml:** Lists all libraries your project needs (like package.json in Node.js)

### **Step 2: Understanding the Main Application Class**

Open `MyFirstApiApplication.java` and you'll see:

```java
package com.learning.myfirstapi;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MyFirstApiApplication {

    public static void main(String[] args) {
        SpringApplication.run(MyFirstApiApplication.class, args);
    }
}
```

**What this code does:**
- **@SpringBootApplication:** Magic annotation that configures everything automatically
- **main method:** Entry point - when you run this, your API starts
- **SpringApplication.run():** Starts the embedded web server and your application

### **Step 3: Create Your First REST Controller**

**A Controller is like a receptionist at a hotel:**
- Receives requests from visitors (HTTP requests)
- Decides what to do with each request
- Sends back appropriate responses

**Create New File:** `src/main/java/com/learning/myfirstapi/controller/HelloController.java`

```java
package com.learning.myfirstapi.controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {
    
    // Endpoint 1: Basic hello world
    @GetMapping("/hello")
    public String sayHello() {
        return "Hello World! Welcome to Spring Boot! 🎉";
    }
    
    // Endpoint 2: Personalized greeting with path variable
    @GetMapping("/hello/{name}")
    public String sayHelloToName(@PathVariable String name) {
        return "Hello " + name + "! Great to see you learning Spring Boot! 🚀";
    }
    
    // Endpoint 3: Greeting with query parameter
    @GetMapping("/greet")
    public String greetWithParameter(@RequestParam(defaultValue = "Student") String name) {
        return "Greetings " + name + "! You're doing amazing in this course! ⭐";
    }
}
```

**Annotation Explanations:**

**@RestController:**
- Tells Spring this class will handle HTTP requests
- Automatically converts return values to JSON
- Combines @Controller + @ResponseBody

**@GetMapping("/hello"):**
- Maps HTTP GET requests to this method
- When someone visits http://localhost:8080/hello, this method runs
- Think of it as "when someone knocks on the /hello door, run this code"

**@PathVariable:**
- Captures values from the URL path
- `/hello/{name}` - the {name} part becomes a variable
- `/hello/Alice` → name = "Alice"

**@RequestParam:**
- Captures query parameters from the URL
- `/greet?name=John` → name = "John"
- `defaultValue = "Student"` means if no name is provided, use "Student"

### **Step 4: Add Advanced Endpoint with Java Records**

**Remember Java Records from Day 2? Let's use them in our API!**

Add this to your `HelloController.java`:

```java
// Add after the imports
import java.util.List;
import java.util.Map;

// Add this Record definition inside the HelloController class
public record Student(Long id, String name, String course, int age) {}

// Add these methods to HelloController class

@GetMapping("/student/{id}")
public Student getStudent(@PathVariable Long id) {
    // In real applications, this data would come from a database
    // For learning, we'll return sample data using Java 21 switch expressions
    return switch (id.intValue()) {
        case 1 -> new Student(1L, "Alice Johnson", "Full-Stack Development", 23);
        case 2 -> new Student(2L, "Bob Smith", "Full-Stack Development", 25);
        case 3 -> new Student(3L, "Carol Davis", "Full-Stack Development", 22);
        case 4 -> new Student(4L, "David Wilson", "Full-Stack Development", 24);
        case 5 -> new Student(5L, "Emma Brown", "Full-Stack Development", 26);
        default -> new Student(id, "Unknown Student", "Not Enrolled", 0);
    };
}

@GetMapping("/students")
public List<Student> getAllStudents() {
    return List.of(
        new Student(1L, "Alice Johnson", "Full-Stack Development", 23),
        new Student(2L, "Bob Smith", "Full-Stack Development", 25),
        new Student(3L, "Carol Davis", "Full-Stack Development", 22),
        new Student(4L, "David Wilson", "Full-Stack Development", 24),
        new Student(5L, "Emma Brown", "Full-Stack Development", 26)
    );
}

@GetMapping("/api/status")
public Map<String, Object> getApiStatus() {
    return Map.of(
        "status", "running",
        "version", "1.0.0",
        "message", "My First Spring Boot API is working perfectly!",
        "endpoints", List.of("/hello", "/hello/{name}", "/greet", "/student/{id}", "/students")
    );
}
```

**What's Happening Here:**

1. **Student Record:** Uses Java 21 Records for clean data structure
2. **Switch Expression:** Modern Java 21 syntax for conditional logic
3. **List.of():** Creates immutable lists easily
4. **Map.of():** Creates key-value pairs for JSON responses

### **Step 5: Configure Application (Optional)**

Edit `src/main/resources/application.properties`:

```properties
# Server Configuration
server.port=8080
server.servlet.context-path=/api

# Application Information
spring.application.name=my-first-api
management.endpoints.web.exposure.include=health,info

# Development Configuration
spring.devtools.restart.enabled=true
spring.output.ansi.enabled=always
```

**Configuration Explained:**
- **server.port:** Which port your API runs on (default: 8080)
- **context-path:** Adds /api prefix to all endpoints
- **devtools.restart:** Automatically restarts app when you change code
- **ansi.enabled:** Colored console output for better readability

### **Step 6: Run Your Spring Boot Application**

#### **Method 1: Using IntelliJ IDEA (Easiest)**
1. Right-click on `MyFirstApiApplication.java`
2. Select "Run 'MyFirstApiApplication.main()'"
3. Watch the console for startup messages

#### **Method 2: Using Maven Command Line**
```bash
# Navigate to your project directory
cd my-first-api

# Run using Maven
mvn spring-boot:run

# Alternative: Build and run JAR
mvn clean package
java -jar target/my-first-api-0.0.1-SNAPSHOT.jar
```

#### **Successful Startup Indicators:**
Look for these messages in the console:
```
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::                (v3.4.x)

INFO 12345 --- [main] c.l.myfirstapi.MyFirstApiApplication: Started MyFirstApiApplication in 2.341 seconds
INFO 12345 --- [main] o.s.b.w.embedded.tomcat.TomcatWebServer: Tomcat started on port(s): 8080 (http)
```

**🎉 Success! Your API is running on http://localhost:8080**

---

## 🧪 **Testing Your API**

### **Step 1: Browser Testing (Quick Verification)**

Open your web browser and test these URLs:

```
http://localhost:8080/hello
Expected: Hello World! Welcome to Spring Boot! 🎉

http://localhost:8080/hello/YourName
Expected: Hello YourName! Great to see you learning Spring Boot! 🚀

http://localhost:8080/greet?name=Developer
Expected: Greetings Developer! You're doing amazing in this course! ⭐

http://localhost:8080/student/1
Expected: {"id":1,"name":"Alice Johnson","course":"Full-Stack Development","age":23}
```

### **Step 2: Professional Testing with Postman**

#### **Setting Up Postman Workspace:**

1. **Open Postman**
2. **Create New Collection:**
   - Click "New Collection"
   - Name: "Day 3 - My First API"
   - Description: "Testing my first Spring Boot REST API"

3. **Create Requests:**

**Request 1: Basic Hello**
```
Method: GET
URL: http://localhost:8080/hello
Headers: (none needed)
Body: (none needed)
```

**Request 2: Hello with Name**
```
Method: GET  
URL: http://localhost:8080/hello/{{name}}
Path Variables: 
  - name: Alice (or any name you prefer)
```

**Request 3: Greet with Query Parameter**
```
Method: GET
URL: http://localhost:8080/greet
Query Parameters:
  - name: Developer (or your name)
```

**Request 4: Get Student by ID**
```
Method: GET
URL: http://localhost:8080/student/{{studentId}}
Path Variables:
  - studentId: 1 (try values 1-5)
```

**Request 5: Get All Students**
```
Method: GET
URL: http://localhost:8080/students
Expected: Array of all 5 students
```

**Request 6: API Status**
```
Method: GET
URL: http://localhost:8080/api/status
Expected: API information and available endpoints
```

#### **Understanding HTTP Response Formats:**

**Text Response Example:**
```
GET /hello
Response: Hello World! Welcome to Spring Boot! 🎉
Content-Type: text/plain
```

**JSON Response Example:**
```
GET /student/1
Response: 
{
  "id": 1,
  "name": "Alice Johnson", 
  "course": "Full-Stack Development",
  "age": 23
}
Content-Type: application/json
```

### **Step 3: Testing Different Scenarios**

**Valid Requests:**
```
✅ GET /student/1     → Returns Alice Johnson
✅ GET /student/5     → Returns Emma Brown  
✅ GET /hello/World   → Returns personalized greeting
✅ GET /greet         → Uses default value "Student"
```

**Edge Cases:**
```
🔍 GET /student/999   → Returns "Unknown Student" 
🔍 GET /greet?name=   → Uses default value "Student"
🔍 GET /hello/        → Should return error (empty name)
```

---

## 🎯 **Understanding What You Built**

### **Architecture Overview:**

```
Browser/Postman  →  HTTP Request  →  Spring Boot API  →  Response
     │                    │              │                 │
     │                    │              │                 │
   Client              Network         Your Code         Data
```

**Step-by-Step Request Flow:**
1. **Client sends request:** GET /student/1
2. **Spring Boot receives:** Routes to HelloController
3. **@GetMapping matches:** Finds method with /student/{id}
4. **Method executes:** Creates Student record with switch expression
5. **Response returned:** JSON representation of Student object
6. **Client receives:** JSON data to display or process

### **Key Concepts You've Mastered:**

**1. Dependency Injection:**
- Spring Boot automatically manages object creation
- No need to manually instantiate controllers
- Framework handles the "plumbing" for you

**2. Convention over Configuration:**
- Follow naming conventions = less configuration needed
- @RestController automatically handles JSON conversion
- Project structure follows standard Maven layout

**3. Annotations-Driven Development:**
- @RestController, @GetMapping guide Spring's behavior
- Declarative programming style
- Less boilerplate code, more focus on business logic

**4. RESTful Design:**
- URLs represent resources (/student/1)
- HTTP methods indicate actions (GET = retrieve)
- Stateless communication between client and server

---

## 🔧 **Customization & Extensions**

### **Add More Endpoints (Practice Exercises):**

**Exercise 1: Add Course Information**
```java
public record Course(String id, String name, String instructor, int duration) {}

@GetMapping("/course/{courseId}")
public Course getCourse(@PathVariable String courseId) {
    return switch (courseId.toLowerCase()) {
        case "fs" -> new Course("FS", "Full-Stack Development", "John Doe", 30);
        case "ds" -> new Course("DS", "Data Science", "Jane Smith", 45);
        case "ai" -> new Course("AI", "Artificial Intelligence", "Bob Johnson", 60);
        default -> new Course(courseId, "Unknown Course", "TBD", 0);
    };
}
```

**Exercise 2: Add Calculator Endpoints**
```java
@GetMapping("/calculator/add")
public Map<String, Object> addNumbers(@RequestParam int a, @RequestParam int b) {
    int result = a + b;
    return Map.of(
        "operation", "addition",
        "operand1", a,
        "operand2", b,
        "result", result,
        "timestamp", java.time.LocalDateTime.now()
    );
}

@GetMapping("/calculator/multiply/{a}/{b}")
public Map<String, Object> multiplyNumbers(@PathVariable int a, @PathVariable int b) {
    return Map.of(
        "operation", "multiplication",
        "operand1", a,
        "operand2", b, 
        "result", a * b
    );
}
```

**Exercise 3: Add Personal Information**
```java
public record PersonalInfo(String name, String hobby, String favoriteLanguage, String goal) {}

@GetMapping("/me")
public PersonalInfo getPersonalInfo() {
    return new PersonalInfo(
        "Your Name",
        "Learning to Code", 
        "Java",
        "Become a Full-Stack Developer"
    );
}
```

### **Configuration Customization:**

**Custom Port Configuration:**
```properties
# application.properties
server.port=8081  # Change port if 8080 is busy
```

**Custom Messages:**
```properties
# application.properties
app.welcome.message=Welcome to My Amazing API!
app.version=1.0.0
```

**Use in your code:**
```java
@Value("${app.welcome.message}")
private String welcomeMessage;

@GetMapping("/info")
public Map<String, String> getAppInfo() {
    return Map.of(
        "message", welcomeMessage,
        "version", "1.0.0"
    );
}
```

---

## 🚨 **Troubleshooting Guide**

### **Common Issues & Solutions:**

#### **Issue 1: Application Won't Start**

**Symptoms:**
```
Error: Could not find or load main class
Port 8080 already in use
```

**Solutions:**
```bash
# Check if Java is properly installed
java -version

# Check if port 8080 is occupied
# Windows:
netstat -ano | findstr :8080

# Mac/Linux:  
lsof -i :8080

# Change port in application.properties:
server.port=8081

# Kill process using port 8080:
# Windows: taskkill /PID <PID> /F
# Mac/Linux: kill -9 <PID>
```

#### **Issue 2: Endpoints Return 404 Not Found**

**Symptoms:**
```
GET /hello → 404 Not Found
Whitelabel Error Page
```

**Solutions:**
```java
// Check controller annotations
@RestController  // Must be present
@GetMapping("/hello")  // Path must match exactly

// Check package structure
// Controller must be in same package or sub-package as main application class
com.learning.myfirstapi.MyFirstApiApplication
com.learning.myfirstapi.controller.HelloController ✅

// Verify application started without errors
// Check console for "Started MyFirstApiApplication" message
```

#### **Issue 3: JSON Not Displaying Properly**

**Symptoms:**
```
Browser shows: {"id":1,"name":"Alice"} (plain text)
Postman shows formatted JSON
```

**Solutions:**
```
This is normal! 
✅ Browsers display JSON as plain text
✅ Use Postman for formatted JSON viewing
✅ Install JSON browser extension for formatting

Chrome Extension: "JSON Viewer Pro"
Firefox Extension: "JSONView"
```

#### **Issue 4: Maven Dependencies Not Downloading**

**Symptoms:**
```
Cannot resolve symbol 'SpringApplication'
ClassNotFoundException: org.springframework...
```

**Solutions:**
```bash
# Refresh Maven project in IntelliJ
# View → Tool Windows → Maven → Refresh

# Clear Maven cache and reinstall
mvn clean install

# Check internet connection
# Verify Maven settings in IntelliJ:
# File → Settings → Build → Build Tools → Maven
```

#### **Issue 5: Application Keeps Restarting**

**Symptoms:**
```
DevTools detected change, restarting...
Application restarts every few seconds
```

**Solutions:**
```properties
# Disable DevTools in application.properties
spring.devtools.restart.enabled=false

# Or exclude certain directories
spring.devtools.restart.exclude=static/**,templates/**
```

### **Advanced Troubleshooting Commands:**

```bash
# Check Spring Boot version
mvn dependency:tree | grep spring-boot

# Verify Java compilation  
mvn clean compile

# Run with debug logging
mvn spring-boot:run -Dspring-boot.run.arguments="--debug"

# Check application health (if actuator enabled)
curl http://localhost:8080/actuator/health
```

---

## ❓ **Common Questions & Answers**

### **Q: What's the difference between @Controller and @RestController?**
**A:** 
- **@Controller:** Returns view names (HTML pages)
- **@RestController:** Returns data directly (JSON/XML)
- @RestController = @Controller + @ResponseBody

### **Q: Can I change the port my API runs on?**
**A:** Yes! Add this to `application.properties`:
```properties
server.port=8081
```

### **Q: How do I stop my Spring Boot application?**
**A:** 
- **IntelliJ:** Click the red square (Stop) button
- **Terminal:** Press Ctrl+C
- **Programmatically:** POST to /actuator/shutdown (if enabled)

### **Q: What happens if I access /student/999 (non-existent ID)?**
**A:** Our switch expression has a `default` case that returns "Unknown Student" - this is good error handling!

### **Q: Can I return HTML instead of JSON?**
**A:** Yes! Change return type to String and return HTML:
```java
@GetMapping("/welcome")
public String getWelcomePage() {
    return "<h1>Welcome to Spring Boot!</h1><p>Your API is running!</p>";
}
```

### **Q: Why do I need Maven/pom.xml?**
**A:** Maven manages dependencies (libraries) your project needs. It's like package.json in Node.js or requirements.txt in Python.

### **Q: Can I add more complex data structures?**
**A:** Absolutely! You can return Lists, Maps, or complex nested objects:
```java
public record University(String name, List<Course> courses, Address address) {}
public record Address(String street, String city, String country) {}
```

---

## 📚 **Additional Learning Resources**

### **Official Documentation:**
- **Spring Boot Reference:** https://docs.spring.io/spring-boot/docs/current/reference/html/
- **Spring Web MVC:** https://docs.spring.io/spring-framework/docs/current/reference/html/web.html
- **Spring Boot Guides:** https://spring.io/guides

### **Video Tutorials:**
- **"Spring Boot Tutorial" by Amigoscode** (YouTube)
- **"Spring Boot Crash Course" by Traversy Media** (YouTube)  
- **"Spring Framework 6 & Spring Boot 3" by Chad Darby** (Udemy)

### **Books:**
- **"Spring Boot in Action" by Craig Walls**
- **"Learning Spring Boot 3.0" by Greg L. Turnquist**
- **"Pro Spring Boot 2" by Felipe Gutierrez**

### **Practice Websites:**
- **Spring Academy:** https://spring.academy/
- **Baeldung:** https://www.baeldung.com/category/spring/
- **DZone Spring Zone:** https://dzone.com/spring-framework

---

## 🎉 **Congratulations!**

You've successfully completed Day 3! Here's what you've accomplished:

### **✅ Skills Mastered:**
- Created a complete Spring Boot project from scratch
- Built multiple REST API endpoints with different parameter types
- Used Java 21 Records in a real application
- Applied modern Java switch expressions
- Tested APIs professionally with Postman
- Understood Spring Boot project structure and configuration
- Learned fundamental REST API concepts

### **✅ Real-World Capabilities:**
- You now have a functional API that can handle HTTP requests
- Your endpoints return both simple text and complex JSON data
- You understand how modern web applications communicate
- You can debug and troubleshoot basic API issues
- You have the foundation to build complex business logic

### **✅ Portfolio Addition:**
You now have a working REST API that you can:
- Add to your GitHub portfolio
- Show to potential employers
- Extend with additional features
- Connect to a frontend application (coming tomorrow!)

---

## 🚀 **What's Next? Day 4 Preview**

Tomorrow we'll connect everything together by:
- **Creating your first Angular application**
- **Building a user interface that calls your API**
- **Connecting frontend (Angular) to backend (Spring Boot)**
- **Creating your first full-stack application!**

### **Tonight's Practice Assignment:**
1. **Extend your API** with a new endpoint about your favorite hobby
2. **Experiment** with different path variables and query parameters  
3. **Test all endpoints** thoroughly with Postman
4. **Keep your API running** - we'll connect to it tomorrow!

**Example Practice Endpoint:**
```java
@GetMapping("/hobby/{hobbyName}")
public Map<String, Object> getHobbyInfo(@PathVariable String hobbyName) {
    return Map.of(
        "hobby", hobbyName,
        "description", "I love " + hobbyName + " because it's amazing!",
        "experience", "Started learning recently",
        "goal", "Become really good at it!"
    );
}
```

**Remember:** Every professional developer started exactly where you are now. You're building real skills that companies value highly! 🌟

**See you tomorrow for Day 4: Building Your First Angular App!** 🎯
