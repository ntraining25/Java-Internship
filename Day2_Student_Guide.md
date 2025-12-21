# Day 2 - Student Learning Guide
## Java 21 Features & HTTP/REST Fundamentals

### 🎯 **What You'll Learn Today**
- Modern Java 21 features that make coding faster and cleaner
- How HTTP protocol works and why it's important
- REST API concepts and HTTP methods
- JSON data format and structure
- How to test APIs using Postman
- How frontend and backend communicate

---

## 📖 **Theory: Java 21 Modern Features**

### **Why Java 21 Matters**

Java 21 is the latest Long Term Support (LTS) version with revolutionary features that didn't exist just a few years ago. You're learning the LATEST Java, not outdated tutorials from 2010!

**Key Benefits:**
- ✅ **Records**: Reduce 30+ lines of code to 1 line
- ✅ **Text Blocks**: Write readable multi-line strings
- ✅ **Pattern Matching**: Code that reads like English
- ✅ **Performance**: Faster execution with Virtual Threads
- ✅ **Industry Standard**: Used by Netflix, Google, Amazon

### **1. Records - The Game Changer**

**Problem with Old Java:**
```java
// Old Java - TOO MUCH CODE! 😫
public class PersonOld {
    private String name;
    private int age;
    
    public PersonOld(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public String getName() { return name; }
    public int getAge() { return age; }
    
    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        PersonOld personOld = (PersonOld) o;
        return age == personOld.age && Objects.equals(name, personOld.name);
    }
    
    @Override
    public int hashCode() {
        return Objects.hash(name, age);
    }
    
    @Override
    public String toString() {
        return "PersonOld{name='" + name + "', age=" + age + "}";
    }
}
```

**Java 21 Solution - AMAZING! ✨**
```java
// Java 21 - ONE LINE DOES EVERYTHING! 🎉
public record Person(String name, int age) {}

// That's it! Java automatically generates:
// - Constructor
// - Getter methods (name(), age())
// - equals() method
// - hashCode() method
// - toString() method
// - Immutable (can't be changed after creation)
```

**Using Records:**
```java
public class RecordExample {
    public static void main(String[] args) {
        // Create person objects
        Person john = new Person("John Doe", 25);
        Person jane = new Person("Jane Smith", 28);
        
        // Access data using generated methods
        System.out.println("Name: " + john.name());     // John Doe
        System.out.println("Age: " + john.age());       // 25
        System.out.println(john);                       // Person[name=John Doe, age=25]
        
        // Equality works perfectly
        Person anotherJohn = new Person("John Doe", 25);
        System.out.println(john.equals(anotherJohn));   // true!
        
        System.out.println("🎉 Records make Java fun!");
    }
}
```

**Real-World Usage:**
```java
// Job Portal Examples using Records
public record Job(
    String title, 
    String company, 
    String location, 
    double salary,
    List<String> skills
) {}

public record JobApplication(
    String candidateName,
    String email,
    String resumeUrl,
    LocalDateTime appliedAt
) {}

public record Company(
    String name,
    String website,
    String industry,
    int employeeCount
) {}
```

### **2. Text Blocks - Readable Strings**

**Problem with Old Java:**
```java
// Old way - UGLY and error-prone! 😫
String html = "<html>\\n" +
             "  <head>\\n" +
             "    <title>JobConnect</title>\\n" +
             "  </head>\\n" +
             "  <body>\\n" +
             "    <h1>Welcome to JobConnect!</h1>\\n" +
             "    <p>Find your dream job here.</p>\\n" +
             "  </body>\\n" +
             "</html>";

String sql = "SELECT j.title, j.company, j.salary " +
            "FROM jobs j " +
            "WHERE j.location = 'Hyderabad' " +
            "AND j.salary > 500000 " +
            "ORDER BY j.created_date DESC";
```

**Java 21 Solution - BEAUTIFUL! ✨**
```java
// Java 21 way - Clean and readable! 🎉
String html = \"\"\"
        <html>
          <head>
            <title>JobConnect</title>
          </head>
          <body>
            <h1>Welcome to JobConnect!</h1>
            <p>Find your dream job here.</p>
          </body>
        </html>
        \"\"\";

String sql = \"\"\"
        SELECT j.title, j.company, j.salary 
        FROM jobs j 
        WHERE j.location = 'Hyderabad' 
          AND j.salary > 500000
        ORDER BY j.created_date DESC
        \"\"\";
```

**Text Block Rules:**
- Start with `\"\"\"` and a newline
- End with `\"\"\"` 
- Preserves formatting and indentation
- Perfect for SQL, HTML, JSON, XML

### **3. Pattern Matching - Code That Reads Like English**

**Old Java vs New Java:**
```java
// Old Java - repetitive and error-prone
Object data = "Hello World";
if (data instanceof String) {
    String str = (String) data;  // Manual cast needed!
    System.out.println("Length: " + str.length());
}

// Java 21 - clean and safe! ✨
if (data instanceof String str) {
    System.out.println("Length: " + str.length()); // str automatically available!
}
```

**Advanced Pattern Matching with Switch:**
```java
public class PatternMatchingDemo {
    public static void processData(Object data) {
        String result = switch (data) {
            case String str -> "Text: " + str.toUpperCase();
            case Integer num -> "Number: " + num * 2;
            case Double decimal -> "Decimal: " + String.format("%.2f", decimal);
            case null -> "No data provided";
            default -> "Unknown data type: " + data.getClass().getSimpleName();
        };
        System.out.println(result);
    }
    
    public static void main(String[] args) {
        processData("hello world");    // Text: HELLO WORLD
        processData(42);               // Number: 84
        processData(3.14159);          // Decimal: 3.14
        processData(null);             // No data provided
        processData(true);             // Unknown data type: Boolean
    }
}
```

**Practical Example - Job Application Processing:**
```java
public class JobApplicationProcessor {
    public static void processApplication(Object application) {
        switch (application) {
            case JobApplication app when app.experience() > 5 -> 
                System.out.println("🌟 Senior candidate: " + app.name());
            
            case JobApplication app when app.experience() > 2 -> 
                System.out.println("👨‍💻 Mid-level candidate: " + app.name());
            
            case JobApplication app -> 
                System.out.println("🎓 Junior candidate: " + app.name());
            
            case null -> 
                System.out.println("❌ Invalid application");
            
            default -> 
                System.out.println("🤔 Unknown application type");
        }
    }
}
```

---

## 🌐 **Theory: HTTP Protocol & REST APIs**

### **What is HTTP?**

HTTP (HyperText Transfer Protocol) is the foundation of web communication. Every time you use Instagram, WhatsApp, or any app, HTTP is working behind the scenes.

**Think of HTTP like a restaurant:**
- **Customer (Frontend)**: Orders food (sends requests)
- **Waiter (HTTP)**: Takes orders and brings food (carries messages)
- **Kitchen (Backend)**: Prepares food (processes requests)

### **HTTP Request-Response Cycle**

```
1. User Action: Click "View Jobs" button
   ↓
2. Frontend: Send HTTP GET request to backend
   GET /api/jobs HTTP/1.1
   Host: localhost:8080
   ↓
3. Backend: Process request, query database
   ↓
4. Database: Return job data
   ↓
5. Backend: Send HTTP response with job list
   HTTP/1.1 200 OK
   Content-Type: application/json
   [{"title": "Java Developer", "company": "TechCorp", ...}]
   ↓
6. Frontend: Display jobs to user
```

### **HTTP Methods (Verbs)**

**GET - Retrieve Data**
```
Purpose: "Please give me data"
Example: GET /api/jobs
Usage: View job listings, get user profile, search jobs
Safe: Yes (doesn't change anything on server)
```

**POST - Create New Data**
```
Purpose: "Here's new data, please save it"
Example: POST /api/jobs
Body: {"title": "Developer", "company": "TechCorp"}
Usage: Create job posting, register user, submit application
Safe: No (creates new data)
```

**PUT - Update Existing Data**
```
Purpose: "Replace this data completely"
Example: PUT /api/jobs/123
Body: Complete job object with changes
Usage: Update entire job posting, edit user profile
Safe: No (modifies existing data)
```

**DELETE - Remove Data**
```
Purpose: "Delete this item"
Example: DELETE /api/jobs/123
Body: Usually empty
Usage: Remove job posting, delete user account
Safe: No (removes data permanently)
```

### **HTTP Status Codes**

**Success Codes (2xx) 🟢**
```
200 OK - "Everything worked, here's your data"
201 Created - "New item successfully created"
204 No Content - "Action completed, nothing to return"
```

**Client Error Codes (4xx) 🟡**
```
400 Bad Request - "Your request doesn't make sense"
401 Unauthorized - "You need to log in first"
403 Forbidden - "You're not allowed to do this"
404 Not Found - "This item doesn't exist"
422 Unprocessable Entity - "Data format is wrong"
```

**Server Error Codes (5xx) 🔴**
```
500 Internal Server Error - "Our server crashed"
502 Bad Gateway - "Server communication problem"
503 Service Unavailable - "Server is temporarily down"
```

**Real-World Examples:**
```
Instagram Examples:
- GET /api/posts → 200 OK (show your feed)
- POST /api/posts → 201 Created (new photo posted)
- DELETE /api/posts/123 → 204 No Content (photo deleted)
- GET /api/posts/999999 → 404 Not Found (post doesn't exist)
```

### **JSON - The Data Language**

JSON (JavaScript Object Notation) is how modern applications exchange data. It's lightweight, readable, and universal.

**JSON Structure Rules:**
```
✅ Strings in double quotes: "name": "John"
✅ Numbers without quotes: "age": 25
✅ Booleans: true or false (lowercase)
✅ Arrays: ["item1", "item2", "item3"]
✅ Objects: {"key": "value"}
✅ Null values: "middleName": null

❌ Single quotes: 'name': 'John'
❌ Trailing commas: {"a": 1, "b": 2,}
❌ Comments: // This is not allowed in JSON
❌ Functions: {"getName": function() {}}
```

**Job Portal JSON Examples:**

**Single Job Object:**
```json
{
  "id": 1,
  "title": "Full Stack Developer",
  "company": "TechCorp Solutions",
  "location": "Hyderabad",
  "salary": 800000,
  "currency": "INR",
  "skills": ["Java", "Spring Boot", "Angular", "MySQL"],
  "experience": {
    "minimum": 2,
    "maximum": 5,
    "unit": "years"
  },
  "isActive": true,
  "isRemote": false,
  "postedDate": "2025-12-18T10:30:00Z",
  "applicationDeadline": "2025-01-15T23:59:59Z",
  "description": "We are looking for passionate developers to join our innovative team."
}
```

**Job Application Object:**
```json
{
  "applicationId": 101,
  "jobId": 1,
  "candidate": {
    "name": "Priya Sharma",
    "email": "priya.sharma@email.com",
    "phone": "+91-9876543210",
    "experience": 3
  },
  "documents": {
    "resume": {
      "fileName": "priya_resume.pdf",
      "uploadedAt": "2025-12-18T11:00:00Z",
      "fileSize": 2048576
    }
  },
  "status": "UNDER_REVIEW",
  "appliedAt": "2025-12-18T11:00:00Z",
  "coverLetter": "I am excited to apply for this position..."
}
```

**API Response with Multiple Jobs:**
```json
{
  "success": true,
  "message": "Jobs retrieved successfully",
  "data": {
    "jobs": [
      {
        "id": 1,
        "title": "Full Stack Developer",
        "company": "TechCorp",
        "location": "Hyderabad",
        "salary": 800000
      },
      {
        "id": 2,
        "title": "Backend Developer", 
        "company": "StartupHub",
        "location": "Bangalore",
        "salary": 1200000
      }
    ],
    "pagination": {
      "currentPage": 1,
      "totalPages": 3,
      "totalJobs": 15,
      "jobsPerPage": 5
    }
  },
  "timestamp": "2025-12-18T11:15:00Z"
}
```

**Error Response Example:**
```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Job title is required",
    "details": [
      {
        "field": "title",
        "issue": "Title cannot be empty"
      },
      {
        "field": "salary",
        "issue": "Salary must be greater than 0"
      }
    ]
  },
  "timestamp": "2025-12-18T11:20:00Z"
}
```

---

## 💻 **Practice: Java 21 Coding Exercises**

### **Exercise 1: Create Records for Job Portal**

Create these Records and test them in your IDE:

```java
// 1. Job Record
public record Job(
    String title,
    String company, 
    String location,
    double salary,
    List<String> skills,
    boolean isRemote
) {
    // Custom method to format salary
    public String getFormattedSalary() {
        return String.format("₹%.2f LPA", salary / 100000.0);
    }
    
    // Method to check if job matches skill
    public boolean requiresSkill(String skill) {
        return skills.contains(skill);
    }
}

// 2. Candidate Record
public record Candidate(
    String name,
    String email,
    String phone,
    int experience,
    List<String> skills
) {
    // Method to calculate skill match percentage
    public double calculateSkillMatch(Job job) {
        long matchingSkills = skills.stream()
            .filter(skill -> job.skills().contains(skill))
            .count();
        return (double) matchingSkills / job.skills().size() * 100;
    }
}

// 3. Application Record
public record Application(
    int applicationId,
    Job job,
    Candidate candidate,
    LocalDateTime appliedAt,
    String status
) {
    // Method to get application summary
    public String getSummary() {
        return \"\"\"
               Application Summary:
               Candidate: %s
               Position: %s at %s
               Applied: %s
               Status: %s
               Skill Match: %.1f%%
               \"\"\".formatted(
                   candidate.name(),
                   job.title(),
                   job.company(),
                   appliedAt.format(DateTimeFormatter.ofPattern("dd-MM-yyyy HH:mm")),
                   status,
                   candidate.calculateSkillMatch(job)
               );
    }
}
```

**Test Your Records:**
```java
import java.time.LocalDateTime;
import java.util.List;

public class JobPortalTest {
    public static void main(String[] args) {
        // Create sample data
        Job job = new Job(
            "Full Stack Developer",
            "TechCorp",
            "Hyderabad", 
            800000,
            List.of("Java", "Spring Boot", "Angular", "MySQL"),
            false
        );
        
        Candidate candidate = new Candidate(
            "Rahul Kumar",
            "rahul.kumar@email.com",
            "+91-9876543210",
            3,
            List.of("Java", "Spring Boot", "React", "PostgreSQL")
        );
        
        Application application = new Application(
            1001,
            job,
            candidate,
            LocalDateTime.now(),
            "UNDER_REVIEW"
        );
        
        // Test methods
        System.out.println("Job: " + job);
        System.out.println("Formatted Salary: " + job.getFormattedSalary());
        System.out.println("Requires Java: " + job.requiresSkill("Java"));
        System.out.println("Skill Match: " + candidate.calculateSkillMatch(job) + "%");
        System.out.println("\n" + application.getSummary());
    }
}
```

### **Exercise 2: Pattern Matching Practice**

```java
public class JobApplicationProcessor {
    
    public static void categorizeApplication(Object data) {
        String category = switch (data) {
            case Application app when app.candidate().experience() > 5 ->
                "🌟 Senior Level Application";
                
            case Application app when app.candidate().experience() > 2 ->
                "👨‍💻 Mid-Level Application";
                
            case Application app ->
                "🎓 Entry Level Application";
                
            case Job job when job.salary() > 1000000 ->
                "💰 High-Paying Position";
                
            case Job job ->
                "📝 Standard Position";
                
            case Candidate candidate when candidate.skills().size() > 5 ->
                "🚀 Versatile Candidate";
                
            case String str ->
                "📄 Text Data: " + str;
                
            case null ->
                "❌ No Data Provided";
                
            default ->
                "🤔 Unknown Data Type";
        };
        
        System.out.println(category);
    }
    
    public static void main(String[] args) {
        // Test with different data types
        Job seniorJob = new Job("Senior Architect", "BigCorp", "Mumbai", 1500000, 
                               List.of("Java", "Microservices"), false);
        
        Candidate skillfulCandidate = new Candidate("Expert Dev", "expert@email.com", 
                                     "+91-1234567890", 8, 
                                     List.of("Java", "Python", "AWS", "Docker", "Kubernetes", "React"));
        
        categorizeApplication(seniorJob);           // High-Paying Position
        categorizeApplication(skillfulCandidate);   // Versatile Candidate
        categorizeApplication("Resume content");     // Text Data: Resume content
        categorizeApplication(null);                // No Data Provided
    }
}
```

### **Exercise 3: Text Blocks for Templates**

```java
public class JobPortalTemplates {
    
    public static String generateJobPostingHtml(Job job) {
        return \"\"\"
               <!DOCTYPE html>
               <html>
               <head>
                   <title>%s - %s</title>
                   <style>
                       .job-card { 
                           border: 1px solid #ddd; 
                           padding: 20px; 
                           margin: 10px; 
                           border-radius: 8px; 
                       }
                       .salary { color: #28a745; font-weight: bold; }
                       .skills { color: #007bff; }
                   </style>
               </head>
               <body>
                   <div class="job-card">
                       <h1>%s</h1>
                       <h2>%s</h2>
                       <p><strong>Location:</strong> %s</p>
                       <p class="salary">Salary: %s</p>
                       <p class="skills">Skills: %s</p>
                       <p><strong>Remote Work:</strong> %s</p>
                   </div>
               </body>
               </html>
               \"\"\".formatted(
                   job.title(), job.company(),
                   job.title(), job.company(),
                   job.location(),
                   job.getFormattedSalary(),
                   String.join(", ", job.skills()),
                   job.isRemote() ? "Available" : "Not Available"
               );
    }
    
    public static String generateWelcomeEmail(String candidateName, String jobTitle) {
        return \"\"\"
               Subject: Application Received - %s
               
               Dear %s,
               
               Thank you for applying to the position of %s at our company.
               
               Your application has been received and is currently under review.
               Our hiring team will carefully evaluate your qualifications and
               get back to you within 5-7 business days.
               
               Application Details:
               - Position: %s
               - Application Date: %s
               - Application ID: APP-%d
               
               If you have any questions, please don't hesitate to contact us.
               
               Best regards,
               JobConnect Team
               \"\"\".formatted(
                   jobTitle,
                   candidateName, 
                   jobTitle,
                   jobTitle,
                   LocalDateTime.now().format(DateTimeFormatter.ofPattern("dd-MM-yyyy")),
                   (int)(Math.random() * 10000)
               );
    }
}
```

---

## 🔧 **Practice: HTTP & API Testing**

### **Using Postman - Step by Step**

**Step 1: Download and Install Postman**
1. Go to: https://www.postman.com/downloads/
2. Download for your operating system
3. Install and create free account
4. Open Postman application

**Step 2: Your First GET Request**
1. Click "New" → "HTTP Request"
2. Set method to **GET**
3. Enter URL: `https://jsonplaceholder.typicode.com/posts`
4. Click "Send"
5. Observe the response:
   - Status: `200 OK`
   - Response time
   - JSON array with posts

**Step 3: Test Different Endpoints**

**Get Single Post:**
```
Method: GET
URL: https://jsonplaceholder.typicode.com/posts/1
```

**Get User Information:**
```
Method: GET  
URL: https://jsonplaceholder.typicode.com/users/1
```

**Get Comments for a Post:**
```
Method: GET
URL: https://jsonplaceholder.typicode.com/posts/1/comments
```

**Search Posts:**
```
Method: GET
URL: https://jsonplaceholder.typicode.com/posts?userId=1
```

**Step 4: Create New Data (POST Request)**

1. Set method to **POST**
2. URL: `https://jsonplaceholder.typicode.com/posts`
3. Go to **Headers** tab, add:
   - Key: `Content-Type`
   - Value: `application/json`
4. Go to **Body** tab, select **raw**, then **JSON**
5. Enter this JSON:

```json
{
  "title": "My First Job Posting",
  "body": "Looking for a talented Full Stack Developer to join our team. Must have experience with Java and Angular.",
  "userId": 1
}
```

6. Click "Send"
7. Check response:
   - Status: `201 Created`
   - Response includes your data with generated ID

**Step 5: Update Data (PUT Request)**

1. Method: **PUT**
2. URL: `https://jsonplaceholder.typicode.com/posts/1`
3. Headers: `Content-Type: application/json`
4. Body (JSON):

```json
{
  "id": 1,
  "title": "Updated Job Title - Senior Developer",
  "body": "Updated job description with new requirements",
  "userId": 1
}
```

**Step 6: Delete Data (DELETE Request)**

1. Method: **DELETE**
2. URL: `https://jsonplaceholder.typicode.com/posts/1`
3. No headers or body needed
4. Click "Send"
5. Check response: `200 OK` with empty object `{}`

### **API Testing Exercises**

**Exercise 1: Job Portal API Design**

Design REST endpoints for a job portal. What URLs would you use?

**Your Task:** Complete this API specification:

```
Job Management:
GET    /api/jobs                     // List all jobs
POST   /api/jobs                     // Create new job  
GET    /api/jobs/{id}                // Get specific job
PUT    /api/jobs/{id}                // Update job
DELETE /api/jobs/{id}                // Delete job

Search & Filter:
GET    /api/jobs/search?title=Java&location=Hyderabad

Application Management:
GET    /api/jobs/{jobId}/applications // List applications for job
POST   /api/jobs/{jobId}/apply        // Apply to job
GET    /api/applications/{id}         // Get specific application

Company Management:
[YOUR TURN - Design these endpoints]
```

**Exercise 2: Test Real APIs**

Test these APIs and note the responses:

1. **GitHub API:**
   - GET: `https://api.github.com/users/octocat`
   - What information does it return?

2. **HTTP Testing Service:**
   - GET: `https://httpbin.org/get`
   - POST: `https://httpbin.org/post` (with any JSON body)

3. **Random User API:**
   - GET: `https://randomuser.me/api/`
   - Generate random user data

**Exercise 3: JSON Practice**

Fix these broken JSON examples:

```json
// Broken JSON 1:
{
  'name': 'John Doe',
  'age': 25,
  'skills': ['Java', 'Spring Boot',]
}

// Broken JSON 2:
{
  "company": "TechCorp",
  "jobs": [
    {
      "title": "Developer",
      "salary": 50000,
    }
  ]
}
```

**Corrected JSON:**
```json
// Fixed JSON 1:
{
  "name": "John Doe",
  "age": 25,
  "skills": ["Java", "Spring Boot"]
}

// Fixed JSON 2:
{
  "company": "TechCorp", 
  "jobs": [
    {
      "title": "Developer",
      "salary": 500000
    }
  ]
}
```

---

## ❓ **Common Questions & Troubleshooting**

### **Java 21 Questions**

**Q: Why use Records instead of regular classes?**
**A:** Records reduce boilerplate code by 80%, are automatically immutable (safer), generate equals/hashCode correctly, and are the modern way to create data classes in Java.

**Q: Can I add custom methods to Records?**
**A:** Yes! You can add custom methods, just like in the examples above. Records can have custom methods, static methods, and even implement interfaces.

**Q: When should I use Text Blocks?**
**A:** Use Text Blocks for multi-line strings like SQL queries, HTML templates, JSON templates, or any string that spans multiple lines.

### **HTTP/API Questions**

**Q: When do I use GET vs POST?**
**A:** 
- **GET**: Retrieving data (viewing jobs, user profiles, search results)
- **POST**: Creating new data (new job posting, user registration, job application)

**Q: What's the difference between PUT and PATCH?**
**A:** 
- **PUT**: Replace entire resource (send complete object)
- **PATCH**: Partial update (send only changed fields)

**Q: Why do APIs return status codes?**
**A:** Status codes tell you what happened without reading the response body. 200 means success, 404 means not found, etc.

### **JSON Questions**

**Q: Can I use single quotes in JSON?**
**A:** No! JSON requires double quotes for strings. Single quotes will cause parsing errors.

**Q: Can I add comments to JSON?**
**A:** No, JSON doesn't support comments. Some tools accept them, but standard JSON doesn't.

**Q: What's the difference between null and undefined in JSON?**
**A:** JSON has `null` but no `undefined`. Use `null` for empty values.

### **Postman Troubleshooting**

**Problem: "Connection refused"**
```
Solutions:
1. Check your internet connection
2. Verify the URL is correct (https:// vs http://)
3. Try the URL in your browser first
4. Check if your network/company blocks API requests
```

**Problem: "Invalid JSON"**
```
Solutions:
1. Use double quotes for strings: "name": "John"
2. Remove trailing commas: {"a": 1, "b": 2}  ✓
3. Validate JSON using online JSON validator
4. Ensure Content-Type header is set to application/json
```

**Problem: "401 Unauthorized"**
```
This is normal for APIs requiring authentication.
For learning, use public APIs that don't require login.
```

---

## 📚 **Additional Learning Resources**

### **Java 21 Deep Dive**
- **Oracle Java 21 Documentation**: https://docs.oracle.com/en/java/javase/21/
- **Java 21 New Features Guide**: https://www.baeldung.com/java-21-new-features
- **Modern Java Tutorials**: https://www.oracle.com/java/technologies/javase/21-relnote-issues.html

### **HTTP and REST APIs**
- **MDN HTTP Guide**: https://developer.mozilla.org/en-US/docs/Web/HTTP
- **REST API Best Practices**: https://restfulapi.net/
- **HTTP Status Code Reference**: https://httpstatuses.com/

### **JSON Learning**
- **JSON.org Official**: https://www.json.org/
- **MDN JSON Guide**: https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON

### **Practice Platforms**
- **HTTP Testing**: httpbin.org
- **Mock APIs**: jsonplaceholder.typicode.com
- **JSON Validation**: jsonlint.com
- **Java Practice**: HackerRank Java Domain

---

## 🎯 **Assignment for Tonight**

### **Assignment 1: Java 21 Programming (30 minutes)**

Create a complete Job Portal data model using Records:

```java
// Create these Records and test them:

public record Company(String name, String industry, String location, int size) {}

public record Job(
    int id,
    String title, 
    Company company,
    double salary,
    List<String> requirements,
    boolean isRemote,
    LocalDate postedDate
) {
    // Add custom methods for:
    // 1. getFormattedSalary() - return "₹X.XX LPA"
    // 2. isRecentPosting() - return true if posted within 7 days
    // 3. matchesSkill(String skill) - check if skill is in requirements
}

public record Candidate(
    String name,
    String email, 
    List<String> skills,
    int experienceYears
) {
    // Add method: calculateMatchScore(Job job) - return percentage match
}

// Create test data and demonstrate all methods work
```

### **Assignment 2: API Testing (20 minutes)**

Using Postman, test these endpoints and document responses:

1. **GET** `https://jsonplaceholder.typicode.com/users`
2. **POST** `https://jsonplaceholder.typicode.com/users` with:
```json
{
  "name": "Your Name",
  "username": "yourUsername", 
  "email": "your.email@example.com"
}
```
3. **GET** `https://httpbin.org/status/404` - What status code do you get?
4. **POST** `https://httpbin.org/post` with job posting JSON

### **Assignment 3: JSON Design (15 minutes)**

Design JSON structures for:

1. **Job Search Response** (list of 5 jobs with pagination info)
2. **Job Application Request** (candidate applying to job)
3. **Error Response** (when job not found)

Use proper JSON syntax and include realistic data.

---

## 🏆 **Self-Assessment Checklist**

**Java 21 Skills:**
- [ ] Can create Records with custom methods
- [ ] Understand when to use Text Blocks
- [ ] Can use Pattern Matching in switch statements
- [ ] Completed all Java coding exercises

**HTTP/REST Skills:**
- [ ] Know the difference between GET, POST, PUT, DELETE
- [ ] Understand common HTTP status codes
- [ ] Can identify valid vs invalid JSON
- [ ] Successfully tested APIs in Postman

**Tomorrow's Readiness:**
- [ ] Excited to build first Spring Boot API
- [ ] Understand how frontend will call backend APIs
- [ ] Ready to see HTTP requests in action with own code

**Success Indicator:** You should feel confident creating Java Records and testing APIs with Postman. Tomorrow, we'll build APIs that respond to your Postman requests!

---

**Great job completing Day 2! Tomorrow we build your first Spring Boot API! 🚀**