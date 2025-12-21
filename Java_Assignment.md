
## 📝 **Comprehensive Practice Questions**

### **Java 8 Features - Coding Questions (5 Questions)**

#### **Question 1: Lambda Expressions & Functional Interfaces**
```java
/**
 * Create a lambda expression to filter a list of integers and return only even numbers.
 * Use Predicate functional interface.
 */
import java.util.*;
import java.util.function.Predicate;
import java.util.stream.Collectors;

public class LambdaExercise1 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
        
        // TODO: Create a Predicate lambda to check if number is even
        Predicate<Integer> isEven = /* Your code here */;
        
        // TODO: Filter the list using the predicate and collect results
        List<Integer> evenNumbers = /* Your code here */;
        
        System.out.println("Even numbers: " + evenNumbers);
        // Expected output: [2, 4, 6, 8, 10]
    }
}

```

#### **Question 2: Stream API with Method References**
```java
/**
 * Given a list of employee names, convert all names to uppercase 
 * and sort them alphabetically using Stream API and method references.
 */
import java.util.*;
import java.util.stream.Collectors;

public class StreamExercise2 {
    public static void main(String[] args) {
        List<String> employees = Arrays.asList("john", "alice", "bob", "charlie", "diana");
        
        // TODO: Convert to uppercase, sort, and collect using method references
        List<String> result = employees.stream()
            .map(/* Method reference here */)
            .sorted(/* Method reference here */)
            .collect(Collectors.toList());
            
        System.out.println("Sorted uppercase names: " + result);
        // Expected: [ALICE, BOB, CHARLIE, DIANA, JOHN]
    }
}

```

#### **Question 3: Optional Class Usage**
```java
/**
 * Create a method that safely finds an employee by ID using Optional.
 * Handle cases where employee might not exist.
 */
import java.util.*;

class Employee {
    private int id;
    private String name;
    private String department;
    
    public Employee(int id, String name, String department) {
        this.id = id;
        this.name = name;
        this.department = department;
    }
    
    // Getters
    public int getId() { return id; }
    public String getName() { return name; }
    public String getDepartment() { return department; }
    
    @Override
    public String toString() {
        return String.format("Employee{id=%d, name='%s', department='%s'}", id, name, department);
    }
}

public class OptionalExercise3 {
    private static List<Employee> employees = Arrays.asList(
        new Employee(1, "John Doe", "IT"),
        new Employee(2, "Jane Smith", "HR"),
        new Employee(3, "Bob Johnson", "Finance")
    );
    
    // TODO: Implement this method using Optional
    public static Optional<Employee> findEmployeeById(int id) {
        // Your code here - use Optional.ofNullable() or stream().findFirst()
    }
    
    public static void main(String[] args) {
        // Test existing employee
        Optional<Employee> emp1 = findEmployeeById(2);
        emp1.ifPresentOrElse(
            System.out::println,
            () -> System.out.println("Employee not found")
        );
        
        // Test non-existing employee
        Optional<Employee> emp2 = findEmployeeById(999);
        String result = emp2.map(Employee::getName).orElse("Unknown Employee");
        System.out.println("Employee name: " + result);
    }
}

```

#### **Question 4: Collectors and Grouping**
```java
/**
 * Group employees by department and count employees in each department
 * using Stream API and Collectors.
 */
import java.util.*;
import java.util.stream.Collectors;

public class CollectorsExercise4 {
    public static void main(String[] args) {
        List<Employee> employees = Arrays.asList(
            new Employee(1, "John", "IT"),
            new Employee(2, "Jane", "HR"),
            new Employee(3, "Bob", "IT"),
            new Employee(4, "Alice", "Finance"),
            new Employee(5, "Charlie", "IT"),
            new Employee(6, "Diana", "HR")
        );
        
        // TODO: Group by department
        Map<String, List<Employee>> byDepartment = employees.stream()
            .collect(/* Your grouping collector here */);
        
        // TODO: Count by department  
        Map<String, Long> countByDepartment = employees.stream()
            .collect(/* Your counting collector here */);
        
        System.out.println("Grouped by department:");
        byDepartment.forEach((dept, empList) -> 
            System.out.println(dept + ": " + empList.size() + " employees"));
            
        System.out.println("\nCount by department:");
        countByDepartment.forEach((dept, count) -> 
            System.out.println(dept + ": " + count));
    }
}

```

#### **Question 5: Date and Time API (Java 8)**
```java
/**
 * Create a method that calculates age from birthdate and finds all employees
 * who are above a certain age using LocalDate and Period.
 */
import java.time.*;
import java.time.format.DateTimeFormatter;
import java.util.*;
import java.util.stream.Collectors;

class EmployeeWithAge {
    private String name;
    private LocalDate birthDate;
    
    public EmployeeWithAge(String name, String birthDate) {
        this.name = name;
        this.birthDate = LocalDate.parse(birthDate);
    }
    
    public String getName() { return name; }
    public LocalDate getBirthDate() { return birthDate; }
    
    // TODO: Implement this method
    public int getAge() {
        // Calculate age using Period.between()
    }
    
    @Override
    public String toString() {
        return String.format("%s (Age: %d)", name, getAge());
    }
}

public class DateTimeExercise5 {
    public static void main(String[] args) {
        List<EmployeeWithAge> employees = Arrays.asList(
            new EmployeeWithAge("John", "1990-05-15"),
            new EmployeeWithAge("Jane", "1985-12-20"),
            new EmployeeWithAge("Bob", "1992-03-10"),
            new EmployeeWithAge("Alice", "1988-08-25")
        );
        
        // TODO: Find employees above age 30
        List<EmployeeWithAge> above30 = employees.stream()
            .filter(/* Your age filter here */)
            .collect(Collectors.toList());
            
        System.out.println("Employees above 30:");
        above30.forEach(System.out::println);
        
        // TODO: Find average age
        double averageAge = employees.stream()
            .mapToInt(/* Method reference to getAge */)
            .average()
            .orElse(0.0);
            
        System.out.println("Average age: " + averageAge);
    }
}

```

---

### **Records Practice Questions**

#### **Question 6: Basic Record Creation**
```java
/**
 * Create a Record for a Book with title, author, price, and ISBN.
 * Add a custom method to determine if it's expensive (price > 500).
 */
public record Book(/* Define fields here */) {
    
    // TODO: Add validation in compact constructor
    public Book {
        // Validate that price is positive and title is not empty
    }
    
    // TODO: Add custom method
    public boolean isExpensive() {
        // Return true if price > 500
    }
    
    // TODO: Add formatted display method
    public String getDisplayInfo() {
        // Return formatted string: "Title: Java Guide by John Doe - ₹599.00"
    }
}

class RecordTest {
    public static void main(String[] args) {
        Book book1 = new Book("Java Complete Guide", "Herbert Schildt", 750.00, "978-0123456789");
        Book book2 = new Book("JavaScript Basics", "John Doe", 350.00, "978-9876543210");
        
        System.out.println(book1.getDisplayInfo());
        System.out.println("Is expensive: " + book1.isExpensive());
    }
}

```

#### **Question 7: Record with Collections**
```java
/**
 * Create a Record for a Student with subjects as a List.
 * Implement methods to calculate average marks and find highest scoring subject.
 */
import java.util.*;

public record Subject(String name, int marks) {}

public record Student(String name, int rollNumber, List<Subject> subjects) {
    
    // TODO: Defensive copying in constructor
    public Student {
        // Create immutable copy of subjects list
        subjects = /* Your code here */;
    }
    
    // TODO: Calculate average marks
    public double getAverageMarks() {
        // Calculate and return average of all subject marks
    }
    
    // TODO: Find highest scoring subject
    public Optional<Subject> getHighestScoringSubject() {
        // Return subject with maximum marks using stream
    }
    
    // TODO: Check if student passed (average >= 40)
    public boolean hasPassed() {
        // Return true if average marks >= 40
    }
}

class StudentTest {
    public static void main(String[] args) {
        List<Subject> subjects = Arrays.asList(
            new Subject("Math", 85),
            new Subject("Physics", 78),
            new Subject("Chemistry", 92),
            new Subject("English", 75)
        );
        
        Student student = new Student("Alice Johnson", 101, subjects);
        
        System.out.println("Student: " + student.name());
        System.out.println("Average: " + student.getAverageMarks());
        System.out.println("Highest: " + student.getHighestScoringSubject().orElse(null));
        System.out.println("Passed: " + student.hasPassed());
    }
}

```

---

### **Text Blocks Practice Questions**

#### **Question 8: HTML Template with Text Blocks**
```java
/**
 * Create HTML templates using Text Blocks for a job posting website.
 */
public class HTMLTemplateExercise {
    
    // TODO: Create a method that returns HTML for job card using text blocks
    public static String createJobCard(String title, String company, String location, String salary) {
        return """
                <!-- Your HTML template here using text blocks -->
                <!-- Include title, company, location, salary parameters -->
                """;
    }
    
    // TODO: Create email template using text blocks
    public static String createApplicationEmail(String candidateName, String jobTitle, String companyName) {
        return """
                <!-- Your email template here -->
                <!-- Include professional email format with parameters -->
                """;
    }
    
    public static void main(String[] args) {
        String jobCard = createJobCard(
            "Full Stack Developer", 
            "TechCorp Solutions", 
            "Hyderabad", 
            "₹8-12 LPA"
        );
        
        String email = createApplicationEmail(
            "John Doe", 
            "Java Developer", 
            "Innovation Labs"
        );
        
        System.out.println("Job Card HTML:");
        System.out.println(jobCard);
        
        System.out.println("\nApplication Email:");
        System.out.println(email);
    }
}

```

#### **Question 9: SQL Queries with Text Blocks**
```java
/**
 * Create complex SQL queries using Text Blocks for job portal database operations.
 */
public class SQLQueryExercise {
    
    // TODO: Create a complex SELECT query using text blocks
    public static String getJobSearchQuery() {
        return """
                -- Your SQL query here for job search
                -- Include JOINs, WHERE conditions, ORDER BY
                """;
    }
    
    // TODO: Create INSERT query for new job posting
    public static String getInsertJobQuery() {
        return """
                -- Your INSERT query here
                -- Include all necessary job fields
                """;
    }
    
    // TODO: Create analytical query for job statistics  
    public static String getJobStatsQuery() {
        return """
                -- Your analytical query here
                -- Include GROUP BY, HAVING, aggregations
                """;
    }
    
    public static void main(String[] args) {
        System.out.println("Job Search Query:");
        System.out.println(getJobSearchQuery());
        
        System.out.println("\nInsert Job Query:");
        System.out.println(getInsertJobQuery());
        
        System.out.println("\nJob Statistics Query:");
        System.out.println(getJobStatsQuery());
    }
}

```

---

### **Pattern Matching with instanceof Practice Questions**

#### **Question 10: Shape Area Calculator**
```java
/**
 * Use pattern matching with instanceof to calculate areas of different shapes.
 */
abstract class Shape {
    abstract String getType();
}

class Circle extends Shape {
    private final double radius;
    
    public Circle(double radius) { this.radius = radius; }
    public double getRadius() { return radius; }
    
    @Override
    String getType() { return "Circle"; }
}

class Rectangle extends Shape {
    private final double length, width;
    
    public Rectangle(double length, double width) {
        this.length = length;
        this.width = width;
    }
    
    public double getLength() { return length; }
    public double getWidth() { return width; }
    
    @Override
    String getType() { return "Rectangle"; }
}

class Triangle extends Shape {
    private final double base, height;
    
    public Triangle(double base, double height) {
        this.base = base;
        this.height = height;
    }
    
    public double getBase() { return base; }
    public double getHeight() { return height; }
    
    @Override
    String getType() { return "Triangle"; }
}

public class PatternMatchingShapes {
    
    // TODO: Implement using pattern matching with instanceof
    public static double calculateArea(Shape shape) {
        // Use instanceof with pattern variables
        // Calculate area based on shape type
        return 0.0; // Replace with your implementation
    }
    
    // TODO: Implement shape description using pattern matching
    public static String getShapeDescription(Shape shape) {
        // Use pattern matching to create descriptive strings
        return ""; // Replace with your implementation
    }
    
    public static void main(String[] args) {
        Shape[] shapes = {
            new Circle(5.0),
            new Rectangle(4.0, 6.0),
            new Triangle(8.0, 3.0)
        };
        
        for (Shape shape : shapes) {
            System.out.println(getShapeDescription(shape));
            System.out.println("Area: " + calculateArea(shape));
            System.out.println();
        }
    }
}

```

#### **Question 11: Data Processing with Pattern Matching**
```java
/**
 * Process different types of user data using pattern matching.
 */
public class DataProcessingExercise {
    
    // TODO: Implement data processing using pattern matching
    public static String processUserInput(Object input) {
        // Handle String, Integer, Double, Boolean, and List types
        // Use pattern matching with instanceof
        // Return appropriate formatted messages
        
        return ""; // Replace with your implementation
    }
    
    // TODO: Implement validation using pattern matching
    public static boolean validateInput(Object input) {
        // Validate based on type:
        // String: not null and not empty
        // Integer: positive number
        // Double: positive and finite
        // Boolean: always valid
        // List: not null and not empty
        
        return false; // Replace with your implementation
    }
    
    public static void main(String[] args) {
        Object[] inputs = {
            "Hello World",
            42,
            3.14159,
            true,
            Arrays.asList("Java", "Spring", "Angular"),
            null,
            "",
            -5,
            Double.POSITIVE_INFINITY
        };
        
        for (Object input : inputs) {
            System.out.println("Input: " + input);
            System.out.println("Valid: " + validateInput(input));
            System.out.println("Processed: " + processUserInput(input));
            System.out.println("---");
        }
    }
}

```

---

### **🏗️ Comprehensive Project: Mini Job Posting System with Java 21 Features**

#### **Question 12: Complete Job Portal Implementation**
```java
/**
 * Build a comprehensive Mini Job Posting System using all Java 21 features:
 * - Records for data modeling
 * - Text Blocks for templates
 * - Pattern Matching for processing
 * - Modern Java 8+ features (Streams, Optional, etc.)
 */

import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;
import java.util.*;
import java.util.stream.Collectors;

// TODO: Define these Records with proper validation
public record Company(/* Define company fields */) {
    // Add validation and custom methods
}

public record Job(/* Define job fields */) {
    // Add validation, custom methods, and business logic
}

public record Application(/* Define application fields */) {
    // Add validation and status management
}

public record Candidate(/* Define candidate fields */) {
    // Add validation and profile methods
}

// Enums for type safety
enum JobType { FULL_TIME, PART_TIME, CONTRACT, INTERNSHIP }
enum ExperienceLevel { ENTRY, JUNIOR, MID, SENIOR, LEAD }
enum ApplicationStatus { APPLIED, UNDER_REVIEW, INTERVIEW_SCHEDULED, REJECTED, OFFERED }

class JobPortalSystem {
    private final List<Company> companies = new ArrayList<>();
    private final List<Job> jobs = new ArrayList<>();
    private final List<Application> applications = new ArrayList<>();
    private final List<Candidate> candidates = new ArrayList<>();
    
    // TODO: Implement these methods
    
    // Company Management
    public Company addCompany(/* parameters */) {
        // Validate and add company
    }
    
    public List<Company> getAllCompanies() {
        return List.copyOf(companies);
    }
    
    // Job Management  
    public Job postJob(/* parameters */) {
        // Validate and post new job
    }
    
    public List<Job> getActiveJobs() {
        // Return only active jobs, sorted by post date
    }
    
    public List<Job> searchJobs(String keyword, String location, JobType jobType, ExperienceLevel experience) {
        // Implement comprehensive search using streams
    }
    
    public Optional<Job> getJobById(String jobId) {
        // Find job by ID using streams
    }
    
    // Application Management
    public Application submitApplication(/* parameters */) {
        // Validate and submit application
    }
    
    public List<Application> getApplicationsForJob(String jobId) {
        // Get all applications for specific job
    }
    
    public List<Application> getApplicationsByCandidate(String candidateId) {
        // Get all applications by specific candidate
    }
    
    public Application updateApplicationStatus(String applicationId, ApplicationStatus newStatus) {
        // Update application status with validation
    }
    
    // Analytics and Reporting
    public Map<String, Long> getJobStatsByCompany() {
        // Count jobs grouped by company using collectors
    }
    
    public Map<JobType, Long> getJobStatsByType() {
        // Count jobs by type
    }
    
    public double getAverageApplicationsPerJob() {
        // Calculate average applications per job
    }
    
    public List<Job> getTopJobsByApplications(int limit) {
        // Get jobs with most applications
    }
    
    // Template Generation using Text Blocks
    public String generateJobPostingHTML(Job job) {
        // Create HTML template using text blocks
        return """
                <!-- Your comprehensive HTML template here -->
                """;
    }
    
    public String generateApplicationEmailTemplate(Application application, Job job, Company company) {
        // Create email template using text blocks
        return """
                <!-- Your email template here -->
                """;
    }
    
    public String generateJobReportJSON(String companyId) {
        // Generate JSON report using text blocks
        return """
                {
                  "reportType": "jobSummary",
                  "generatedDate": "%s",
                  "company": {
                    // Your JSON structure here
                  }
                }
                """.formatted(LocalDateTime.now().toString());
    }
    
    // Data Processing with Pattern Matching
    public String processJobData(Object data) {
        // Use pattern matching to process different data types
        // Handle Job, Company, Application, String, Number, etc.
        
        return switch (data) {
            // Your pattern matching implementation here
            case null -> "No data provided";
            default -> "Unknown data type";
        };
    }
    
    public boolean validateJobData(Object data) {
        // Validate data using pattern matching
        // Return true if valid, false otherwise
        
        return switch (data) {
            // Your validation logic here
            case null -> false;
            default -> false;
        };
    }
}

// Main class for testing
public class JobPortalApplication {
    public static void main(String[] args) {
        JobPortalSystem portal = new JobPortalSystem();
        
        // TODO: Create test data and demonstrate all functionality
        
        // 1. Add companies
        Company techCorp = portal.addCompany(/* parameters */);
        Company startupHub = portal.addCompany(/* parameters */);
        
        // 2. Post jobs
        Job job1 = portal.postJob(/* parameters */);
        Job job2 = portal.postJob(/* parameters */);
        
        // 3. Register candidates
        // 4. Submit applications  
        // 5. Search and filter jobs
        // 6. Generate reports
        // 7. Test pattern matching
        // 8. Display templates
        
        System.out.println("🎉 Job Portal System Demo Complete!");
    }
}

/**
 * IMPLEMENTATION REQUIREMENTS:
 * 
 * 1. Records must include:
 *    - Proper field definitions
 *    - Validation in compact constructors
 *    - Custom business methods
 *    - Formatted display methods
 * 
 * 2. Text Blocks must be used for:
 *    - HTML templates (job cards, application forms)
 *    - Email templates (application confirmations)
 *    - JSON response templates
 *    - SQL query templates (bonus)
 * 
 * 3. Pattern Matching must handle:
 *    - Different object types (Job, Company, Application)
 *    - Data validation scenarios
 *    - Type-specific processing logic
 * 
 * 4. Java 8+ Features must include:
 *    - Stream API for filtering and processing
 *    - Optional for safe null handling
 *    - Collectors for grouping and counting
 *    - Method references where appropriate
 *    - Lambda expressions for functional operations
 * 
 * 5. Bonus Features:
 *    - Add logging using text blocks
 *    - Implement caching for search results
 *    - Add configuration using records
 *    - Create builder patterns for complex objects
 * 
 * EVALUATION CRITERIA:
 * - Correct usage of Java 21 features (40%)
 * - Code quality and organization (30%)
 * - Business logic implementation (20%)
 * - Error handling and validation (10%)
 */
```