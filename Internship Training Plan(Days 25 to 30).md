# 30-Day Internship Plan – Full-Stack Apps with Java, Spring Boot, Angular

## Overview

In this 30-day internship, you will **build two real full-stack applications**:

1. **JobConnect** – a mini Job Portal  
2. **TaskTrack** – a Personal Task Manager  

You will work with **Java, Spring Boot, REST APIs, Angular, and GitHub**. By the end, you will be able to **demo your own apps**, understand how real full-stack projects work, and be ready for the advanced Full-Stack Developer Training Program.

- **Duration:** 30 Days  
- **Daily Time:** ~2 hours (1 hr Theory + 1 hr Practice)  
- **Style:** Learn a small concept → Immediately build something with it  
- **Outcome:** 2 working apps + GitHub portfolio + presentation skills

---

## Phase 1: Setup & Fundamentals (Days 1–4)

### Day 1 – Environment Setup & Introduction

**Theory (1 hr)**
- What is full-stack development? Frontend, backend, database, API.
- Overview of Java, Spring Boot, Angular, REST, JSON.
- Tools overview: JDK, IntelliJ/Eclipse, Maven/Gradle, Node.js, Angular CLI, Git & GitHub, Postman.

**Practice (1 hr)**
- Install JDK + IDE, Node.js + Angular CLI.
- Create a GitHub account and a blank repo `internship-projects`.
- Run `ng new hello-internship` and verify `mvn -v`, `ng version`.

---

### Day 2 – Java & HTTP Basics

**Theory (1 hr)**
- Core Java refresher: classes, methods, packages.
- What is HTTP? Methods (GET/POST/PUT/DELETE), status codes, JSON format.
- How frontend and backend talk to each other (REST API concept).

**Practice (1 hr)**
- Create a simple Java console program (e.g., greet user, simple calculator).
- Install Postman or VS Code REST client.
- Hit a public sample API (e.g., https://jsonplaceholder.typicode.com/posts) and inspect JSON response.

---

### Day 3 – Spring Boot: First REST API

**Theory (1 hr)**
- What is Spring Boot? Why it simplifies Java backend development.
- Creating a project using Spring Initializr.
- Basics of `@RestController`, `@GetMapping`, dependency injection.

**Practice (1 hr)**
- Create a Spring Boot project `jobconnect-backend`.
- Implement `/api/hello` endpoint returning a simple JSON message.
- Test the endpoint in browser/Postman.

---

### Day 4 – Angular: First HTTP Call

**Theory (1 hr)**
- Angular basics: project structure, components, templates, services.
- Using HttpClient to call REST APIs from frontend.

**Practice (1 hr)**
- Create Angular project `jobconnect-frontend`.
- Create a `HelloComponent` that calls `/api/hello` from Spring Boot and displays the response.
- Verify end-to-end: Angular → Spring Boot → response on the page.

---

## Phase 2: JobConnect – Job Portal (Days 5–18)

### Day 5 – Job Entity & Basic CRUD (Backend)

**Theory (1 hr)**
- Entity concept, fields, primary key.
- Intro to Spring Data JPA and H2/MySQL database.
- Annotations: `@Entity`, `@Id`, `@GeneratedValue`, `@Column`.

**Practice (1 hr)**
- Configure H2 or MySQL in `jobconnect-backend`.
- Create `Job` entity with fields: `id`, `title`, `company`, `location`, `salaryRange`, `skills`, `description`, `createdAt`.
- Run the app and verify schema creation in database.

---

### Day 6 – Repository & Service (Backend)

**Theory (1 hr)**
- Repository pattern and `JpaRepository` interface.
- Service layer and clean architecture: Controller → Service → Repository.
- Separation of concerns and maintainability.

**Practice (1 hr)**
- Create `JobRepository extends JpaRepository<Job, Long>`.
- Create `JobService` class with methods: `createJob()`, `getAllJobs()`, `getJobById()`.
- Test service methods by calling them from a simple endpoint.

---

### Day 7 – Job REST Controller

**Theory (1 hr)**
- REST endpoint design for CRUD operations.
- HTTP methods: GET (retrieve), POST (create), PUT (update), DELETE (remove).
- `@RequestBody`, `@PathVariable`, `@RestController` annotations.

**Practice (1 hr)**
- Create `JobController` with endpoints:
  - `GET /api/jobs` → retrieve all jobs
  - `GET /api/jobs/{id}` → get single job
  - `POST /api/jobs` → create new job
- Test all endpoints with Postman and verify JSON responses.

---

### Day 8 – Update & Delete Endpoints

**Theory (1 hr)**
- PUT vs PATCH semantics (PUT for full update, PATCH for partial).
- DELETE semantics and safe removal.
- HTTP status codes: 200 (OK), 201 (Created), 204 (No Content), 404 (Not Found).

**Practice (1 hr)**
- Implement `PUT /api/jobs/{id}` for updating a job.
- Implement `DELETE /api/jobs/{id}` for removing a job.
- Return proper HTTP status codes and handle "job not found" cases gracefully.

---

### Day 9 – Angular Job List Page

**Theory (1 hr)**
- Angular routing basics: `RouterModule`, `Routes`.
- Creating components and templates.
- Using services to fetch data via HttpClient.

**Practice (1 hr)**
- In `jobconnect-frontend`, create:
  - `JobListComponent` (template, component class)
  - `JobService` (calls `/api/jobs` endpoint)
- Display jobs in a table or card layout.
- Add debug logging to understand data flow.

---

### Day 10 – Job Details Page

**Theory (1 hr)**
- Route parameters and `ActivatedRoute`.
- Passing data between routes and components.
- Lifecycle hooks: `OnInit`.

**Practice (1 hr)**
- Add route `/jobs/:id` to your routing config.
- Create `JobDetailsComponent` that:
  - Reads job `id` from route parameter
  - Calls service to fetch job by id
  - Displays full job details
- Add a link from job list → details page on job card/row click.

---

### Day 11 – Create Job (Frontend Form)

**Theory (1 hr)**
- Angular forms: Reactive Forms approach (FormBuilder, FormControl).
- Form validation: required, minLength, pattern validators.
- Displaying validation errors to user.

**Practice (1 hr)**
- Create `JobFormComponent` with form fields matching Job entity.
- Use ReactiveFormsModule for form management.
- Implement `createJob()` method that calls `POST /api/jobs`.
- Add validation messages for required fields and proper error display.

---

### Day 12 – Edit & Delete Job (Frontend)

**Theory (1 hr)**
- Reusing forms for both create and edit workflows.
- Pre-filling form with existing data.
- Confirmation dialogs for destructive actions (delete).

**Practice (1 hr)**
- Modify JobFormComponent to support both "Add New" and "Edit Existing" modes.
- Add "Edit" button in list/details → navigate to form with pre-filled data.
- Implement `updateJob()` calling `PUT /api/jobs/{id}`.
- Add "Delete" button with confirmation → calls `DELETE /api/jobs/{id}` and refreshes list.

---

### Day 13 – Search & Filter Jobs

**Theory (1 hr)**
- Query parameters in REST APIs.
- Filtering strategies: backend filtering vs frontend filtering.
- When to filter backend (large datasets) vs frontend (small datasets).

**Practice (1 hr)**
- Enhance backend endpoint: `GET /api/jobs?title=Java&location=Hyderabad`.
- Add search bar in Angular component (title, location search).
- Implement search method that calls filtered API endpoint.
- Display filtered results dynamically as user types.

---

### Day 14 – Apply to Job (Backend)

**Theory (1 hr)**
- Entity relationships: One-to-Many (Job has many Applications).
- Foreign keys and relational database concepts.
- Data Transfer Objects (DTOs) for request/response payloads.

**Practice (1 hr)**
- Create `Application` entity: `id`, `candidateName`, `email`, `resumeUrl`, `appliedAt`, `jobId`.
- Create `ApplicationRepository`, `ApplicationService`.
- Create `ApplicationController` with:
  - `POST /api/jobs/{jobId}/apply` endpoint
- Test with Postman, verify application is saved in database.

---

### Day 15 – Apply to Job (Frontend)

**Theory (1 hr)**
- Navigation to child routes or modal dialogs for forms.
- Passing context data between components.
- Success/error message handling.

**Practice (1 hr)**
- Add "Apply Now" button on Job Details page.
- Create `ApplyJobComponent` with form: candidateName, email, resumeUrl.
- Implement form submission calling `POST /api/jobs/{jobId}/apply`.
- Show success message on successful application.
- Redirect or close form after successful apply.

---

### Day 16 – UI/UX Improvements for JobConnect

**Theory (1 hr)**
- Basic UI/UX principles: consistency, clarity, feedback.
- Bootstrap or Angular Material for styling.
- Navbar, footer, responsive layout basics.

**Practice (1 hr)**
- Add navigation bar (Home, Browse Jobs, About).
- Apply Bootstrap styling or Angular Material components.
- Improve form appearance and add visual feedback.
- Add loading indicators while fetching jobs.
- Display error messages gracefully to users.

---

### Day 17 – Code Cleanup & README

**Theory (1 hr)**
- Project structure best practices: organize by feature/domain.
- Naming conventions for packages, components, services.
- Writing clear README documentation.

**Practice (1 hr)**
- Refactor package structure:
  - Backend: `controller`, `service`, `repository`, `model`, `dto`
  - Frontend: `components`, `services`, `models`
- Create comprehensive `README.md` for JobConnect:
  - Project overview
  - Technology stack
  - Setup instructions (how to run backend & frontend)
  - API endpoints documentation
  - Screenshots
- Push code to GitHub with proper commit messages.

---

### Day 18 – JobConnect Demo Day

**Theory (1 hr)**
- Presenting a project effectively: problem statement, solution, features, technology.
- Common technical interview questions about your project.
- Answering "Why did you choose this technology?" and "What was the hardest part?"

**Practice (1 hr)**
- Rehearse a 5-minute demo of JobConnect showing:
  - Job list and search functionality
  - Job details page
  - Create/edit/delete a job
  - Apply to a job
  - Code structure overview
- Record yourself or practice with peers.
- Note any bugs or improvements needed.

---

## Phase 3: TaskTrack – Task Manager (Days 19–24)

### Day 19 – TaskTrack Backend Setup

**Theory (1 hr)**
- Recap: creating a new Spring Boot project from scratch.
- Design decisions: what fields does a task need?
- Task lifecycle and statuses.

**Practice (1 hr)**
- Create new Spring Boot project `tasktrack-backend` (or new module).
- Create `Task` entity with fields: `id`, `title`, `description`, `status` (enum: TODO/IN_PROGRESS/DONE), `dueDate`, `createdAt`, `updatedAt`.
- Configure H2 or MySQL database connection.
- Run application and verify table creation.

---

### Day 20 – Task REST APIs

**Theory (1 hr)**
- Reusing patterns from JobConnect: service, repository, controller structure.
- Enum types for task status.
- Status-based filtering and queries.

**Practice (1 hr)**
- Create `TaskRepository extends JpaRepository<Task, Long>`.
- Create `TaskService` with CRUD methods.
- Create `TaskController` with endpoints:
  - `GET /api/tasks`
  - `GET /api/tasks/{id}`
  - `POST /api/tasks`
  - `PUT /api/tasks/{id}`
  - `DELETE /api/tasks/{id}`
  - Optional: `GET /api/tasks?status=TODO`
- Test all endpoints with Postman.

---

### Day 21 – TaskTrack Angular App Setup

**Theory (1 hr)**
- Project organization: separate Angular app vs module within same workspace.
- Module structure and component hierarchy.
- Reusing learnings from JobConnect.

**Practice (1 hr)**
- Create `tasktrack-frontend` Angular app or add new module.
- Setup routing module with basic routes.
- Create layout components: navbar, sidebar (optional).
- Connect Angular app to TaskTrack backend.

---

### Day 22 – Task List & Filters (Frontend)

**Theory (1 hr)**
- Displaying task lists with status indicators.
- Angular pipes for formatting and filtering.
- Reactive filtering: using RxJS to update list dynamically.

**Practice (1 hr)**
- Create `TaskListComponent` and `TaskService`.
- Fetch tasks from `/api/tasks`.
- Display tasks in a table with columns: title, status, due date, actions.
- Add buttons/dropdown to filter tasks by status (TODO, IN_PROGRESS, DONE).
- Show status-based visual indicators (badges or colors).

---

### Day 23 – Task Form & Status Update

**Theory (1 hr)**
- Reusing reactive forms from JobConnect.
- UX patterns: quick actions (toggle status) vs full edit form.
- Date picker for due date selection.

**Practice (1 hr)**
- Create `TaskFormComponent` for adding new tasks and editing existing tasks.
- Implement validation: required title, valid due date.
- Add quick "Mark as Done" action (checkbox or button) to update task status immediately.
- Implement full task update via edit form.
- Add delete functionality with confirmation.

---

### Day 24 – Polish TaskTrack & Add README

**Theory (1 hr)**
- Comparison: JobConnect vs TaskTrack – different domains, same patterns.
- Importance of having multiple projects for resume/portfolio.
- Consistent coding style and documentation.

**Practice (1 hr)**
- Improve TaskTrack UI: clean, simple, professional appearance.
- Add color-coded status indicators (Todo: yellow, In Progress: blue, Done: green).
- Add due date warning (tasks due soon highlighted in orange).
- Create comprehensive `README.md` for TaskTrack.
- Push code to GitHub.
- Verify both JobConnect and TaskTrack repos are clean and well-documented.

---

## Phase 4: Practice, Wrap-Up & Next Steps (Days 25–30)

### Day 25 – Code Review, Refactoring & Bug Fixes

**Theory (1 hr)**
- Debugging techniques: logs, browser dev tools, Postman testing.
- Code quality principles: DRY (Don't Repeat Yourself), SOLID basics.
- Common mistakes and how to avoid them.

**Practice (1 hr)**
- Code review: review both JobConnect and TaskTrack for consistency.
- Fix any known bugs in either application.
- Remove console logs and unused imports.
- Improve error handling: proper error messages, fallback UI.
- Validate all form inputs thoroughly.
- Ensure consistent naming and code style across both projects.

---

## Days 26–30: Practice, Doubt Resolution & Portfolio Building

### Days 26–27 – Intensive Practice & Problem Solving

**Self-Study & Practice**
- Work on any pending features or enhancements:
  - Add pagination to job/task lists
  - Improve sorting options
  - Add date-based filtering
  - Enhance UI/UX further
- Debug and test edge cases (empty lists, validation, network errors).
- Experiment with new features not covered in the training.
- Pair with peers and review each other's code.

**Doubt Resolution**
- Clarify any concepts from Days 1–25 that need deeper understanding.
- Ask questions about Spring Boot, Angular, REST API design.
- Get feedback on your code structure and architecture.

---

### Days 28–30 – Portfolio Building & Preparation for Advanced Training

**Portfolio Preparation**
- Finalize both applications: JobConnect and TaskTrack.
- Create polished README files with:
  - Project overview and motivation
  - Tech stack justification
  - Architecture diagrams (simple sketches)
  - How to run the applications
  - Key features and future enhancements
  - Screenshots or demo links
- Update your GitHub profile with links to both projects.
- Create a portfolio page or LinkedIn summary highlighting these projects.

**Understanding Your Journey So Far**
You have successfully:
- Built a REST API with Spring Boot
- Created an Angular frontend consuming APIs
- Worked with databases (JPA/Hibernate)
- Implemented CRUD operations end-to-end
- Deployed applications on GitHub
- Created professional README documentation

**What Awaits in the 45–60 Day Full-Stack Developer Training Program**

The advanced training program will significantly deepen your skills:

**Advanced Backend (Spring Boot & Java)**
- **Spring Security & JWT Authentication:** Secure your APIs with login/logout, role-based access control, JWT tokens.
- **Advanced Spring Data JPA:** Complex queries, relationships optimization, pagination, sorting, custom SQL.
- **Exception Handling & Validation:** Global exception handlers, custom validators, proper error responses.
- **Business Logic & Transactions:** Transactional methods, rollback strategies, business workflow implementation.
- **File Upload & Processing:** Handle file uploads, image processing, document handling.
- **Caching Strategies:** Redis caching for performance optimization.
- **Testing (Unit & Integration):** JUnit, Mockito, test-driven development (TDD).
- **Microservices Architecture:** Breaking monolith into services, service-to-service communication.
- **Message Queues:** Kafka/RabbitMQ for asynchronous processing.

**Advanced Frontend (Angular)**
- **Advanced Routing:** Lazy loading, route guards, nested routes, URL parameters.
- **State Management:** NgRx/RxJS for complex state handling across components.
- **HTTP Interceptors:** Global request/response handling, JWT token attachment, error interception.
- **Custom Directives & Pipes:** Create reusable UI utilities.
- **Performance Optimization:** Change detection strategies, OnPush strategy, tree-shaking.
- **Advanced Forms:** Dynamic form generation, conditional validation, multi-step forms.
- **Angular Material:** Professional UI component library.
- **Testing (Unit & E2E):** Jasmine, Karma, Cypress for frontend testing.
- **Reactive Programming:** Deep dive into RxJS Observables, operators, streams.

**DevOps & Deployment**
- **Docker:** Containerizing Java and Angular applications.
- **Docker Compose:** Multi-container application setup.
- **CI/CD Pipelines:** GitHub Actions, Jenkins for automated testing and deployment.
- **Cloud Deployment:** AWS, Azure, or GCP (free tier options).
- **Environment Management:** Development, staging, production configurations.

**Database & Performance**
- **SQL Optimization:** Indexes, query optimization, explain plans.
- **Database Design:** Normalization, denormalization, schema design patterns.
- **Transaction Management:** ACID properties, isolation levels, locking.

**Real-World Development Skills**
- **Code Review Practices:** How to give and receive feedback.
- **Version Control Best Practices:** Branching strategies (Git Flow, Trunk-Based), merge conflicts.
- **Documentation:** API documentation (Swagger/OpenAPI), code comments, design docs.
- **Soft Skills:** Communication, teamwork, problem-solving in team settings.

**Capstone Projects**
- Build an **E-Commerce Platform** (products, orders, payments, reviews)
- Build a **Social Media Application** (users, posts, likes, comments, notifications)
- Build an **Learning Management System** (courses, lessons, quizzes, progress tracking)

**Why This Training Takes 45–60 Days**
- Days 1–25 (this internship) cover the **fundamentals and basic full-stack flow**.
- Days 26–60 will cover **advanced features, security, testing, deployment, and real-world best practices** that enterprise applications require.
- The extended program ensures you're ready for **Senior Developer and Architect roles**, not just junior positions.

**Your Next Steps**
1. **Complete this 30-day internship** with excellence.
2. **Deploy your applications** somewhere (Heroku free tier, AWS free tier, or simple hosting).
3. **Create a compelling narrative** about what you learned and built.
4. **Identify your weaker areas** (frontend vs backend, design vs logic) for focused learning.
5. **Enroll in the 45–60 day Full-Stack Developer Training Program** to become a job-ready senior developer.

**Job Market Reality**
- Most **mid-level and senior developer roles** require the skills covered in the 45–60 day program.
- Companies look for candidates who understand **security, performance, testing, deployment, and architectural decisions**.
- Your 30-day internship apps + 45–60 day training will position you to **confidently interview for roles** targeting 5–10+ years of experience.

---

## Final Remarks

**Your 30-day internship is not an endpoint; it's a launch pad.** You've proven you can build real applications. The advanced training will show you how to build them at scale, securely, and reliably.

**Best of luck!** 🚀

---

## Appendix: Useful Resources

**Spring Boot & Java**
- Spring Boot Official Documentation: https://spring.io/projects/spring-boot
- Baeldung Spring Boot Tutorials: https://www.baeldung.com/
- Oracle Java Tutorials: https://docs.oracle.com/javase/tutorial/

**Angular**
- Angular Official Documentation: https://angular.io/docs
- Angular Learning Materials: https://angular.io/guide/learning-angular
- RxJS Documentation: https://rxjs.dev/

**REST API Design**
- RESTful API Best Practices: https://restfulapi.net/
- HTTP Status Codes: https://httpwg.org/specs/rfc7231.html#status.codes

**Tools & Platforms**
- Postman API Testing: https://www.postman.com/
- GitHub: https://github.com/
- Spring Initializr: https://start.spring.io/

**Version Control**
- Git Documentation: https://git-scm.com/doc
- GitHub Guides: https://guides.github.com/

**Deployment**
- Docker Documentation: https://docs.docker.com/
- AWS Free Tier: https://aws.amazon.com/free/

---

**Document Version:** 1.0  
**Last Updated:** December 2025  
**Created For:** Internship Program Participants
