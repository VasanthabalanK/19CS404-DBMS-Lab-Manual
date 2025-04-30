# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---



### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---



---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - Student Name
Vasanthabalan K

## Scenario Chosen:
University

## ER Diagram:
![Screenshot 2025-04-30 202032](https://github.com/user-attachments/assets/1bca0c53-c744-4359-b232-2387573ad1f9)


## Entities and Attributes:
Student

Attributes: StudentID (Primary Key), FullName, DateOfBirth

Department

Attributes: DepartmentID (Primary Key), Name, CourseName (Note: CourseName seems misplaced here — likely a separate entity is needed for Course)

Program

Attributes: ProgramID (Primary Key), Program Name, DepartmentID (Foreign Key)

Teaches (Modeled as an entity but may be better as a relationship)

Attributes: InstructorID, CourseID, staff number
...

## Relationships and Constraints:
University

Entities involved: Student, Department, Program

Cardinality:

A Student belongs to one Department

A Program is part of one Department

A Department can have many Students and Programs

Participation:

Total for Students (every student must be in a department)

Partial for Departments (not every department needs students/programs, possibly)

Teaches

Entities involved: Possibly Instructor, Course

Cardinality: Many-to-Many (an Instructor can teach many courses, and a course can be taught by many instructors)

Participation: Partial for both

Note: The diagram lacks clear entities for Instructor and Course — could be modeled explicitly
...

## Extension (Prerequisite / Billing):
Prerequisite:

Could be modeled as a recursive relationship on the Course entity (e.g., Course A requires Course B)

Attributes: CourseID, PrerequisiteCourseID

Billing:

Not modeled in this ER diagram

Could be introduced with a new Billing entity connected to Student

Attributes: BillID, StudentID, Amount, DueDate

## Design Choices:
Entity Identification: Focused on key academic entities: Student, Department, Program. These are commonly needed in a university database.

Attributes: Captured essential properties only (like ID, name, etc.), assuming additional attributes could be added as needed.

Teaches: Although modeled as an entity, it could be better modeled as a relationship between Instructor and Course.

Simplification Assumptions:

No separate Instructor or Course entity was modeled despite relevant attributes (likely for simplicity)

The University relationship groups multiple entities, which might be more useful broken into simpler, binary relationships for clarity.

## RESULT
Thus, the Entity-Relationship (ER) Diagram have been created successfully.
