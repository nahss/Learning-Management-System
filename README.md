# Learning Management System (LMS) Module

The Learning Management System (LMS) module facilitates decentralized management of educational institutes, courses, student enrollments, and grant approvals within a blockchain ecosystem. It provides functionalities for creating and managing institutes, adding courses, enrolling students, handling grant requests, managing balances, and ensuring secure transactions between stakeholders.

## Struct Definitions

### Institute
- **id**: Unique identifier for each institute.
- **name**: Name of the institute.
- **email**: Email address of the institute.
- **phone**: Contact phone number of the institute.
- **fees**: Fees associated with courses offered by the institute.
- **balance**: Balance of SUI tokens held by the institute.
- **courses**: Table storing courses offered by the institute.
- **enrollments**: Table storing student enrollments in courses.
- **requests**: Table storing enrollment requests from students.
- **institute**: Address of the institute.

### Course
- **id**: Unique identifier for each course.
- **title**: Title or name of the course.
- **instructor**: Name of the instructor teaching the course.
- **capacity**: Maximum number of students that can enroll in the course.
- **enrolledStudents**: Vector storing addresses of students enrolled in the course.

### Student
- **id**: Unique identifier for each student.
- **name**: Name of the student.
- **email**: Email address of the student.
- **homeAddress**: Home address of the student.
- **balance**: Balance of SUI tokens held by the student.
- **student**: Address of the student.

### Enrollment
- **id**: Unique identifier for each enrollment record.
- **student**: Address of the enrolled student.
- **studentName**: Name of the enrolled student.
- **courseId**: ID of the course in which the student is enrolled.
- **date**: Date of enrollment.
- **time**: Timestamp of enrollment.

### EnrollmentRequest
- **id**: Unique identifier for each enrollment request.
- **student**: Address of the student requesting enrollment.
- **homeAddress**: Home address of the student.
- **created_at**: Timestamp of when the enrollment request was created.

### GrantRequest
- **id**: Unique identifier for each grant request.
- **student**: Address of the student requesting the grant.
- **amount_requested**: Amount of funds requested by the student.
- **reason**: Reason provided by the student for requesting the grant.
- **approved**: Boolean indicating if the grant request has been approved.

### GrantApproval
- **id**: Unique identifier for each grant approval.
- **grant_request_id**: ID of the grant request that is approved.
- **approved_by**: Address of the institute approving the grant request.
- **amount_approved**: Amount of funds approved.
- **reason**: Reason provided by the institute for approving the grant.

## Accessors

### student_check_balance
Returns the balance of SUI tokens held by a student.

### institute_check_balance
Returns the balance of SUI tokens held by an institute.

## Public - Entry Functions

### create_institute
Creates a new institute with specified details such as name, email, phone, and initial fees. Initializes tables for courses, enrollments, and enrollment requests associated with the institute.

### create_student
Creates a new student with specified details such as name, email, and home address. Initializes the student's balance and assigns the student's address.

### add_course
Adds a new course with specified details such as title, instructor, and capacity. Initializes an empty list of enrolled students for the course.

### new_enrollment_request
Initiates a new enrollment request from a student for a course, capturing details such as the student's address, home address, and timestamp.

### add_enrollment
Enrolls a student in a course offered by an institute. Deducts course fees from the student's balance, enrolls the student in the course, and records the enrollment details.

### fund_student_account
Adds funds to a student's balance. Only accessible by the student identified by the transaction context.

### withdraw_institute_balance
Allows an institute to withdraw funds from its balance. Ensures that the withdrawal amount does not exceed the institute's current balance.

### create_grant_request
Initiates a grant request from a student, specifying the amount requested and the reason for the request.

### approve_grant_request
Approves a grant request submitted by a student. Records the approval details including the approving institute, approved amount, and reason for approval.

### update_course
Updates details of a course such as title, instructor, and capacity. Only accessible by authorized personnel from the institute.

### update_student
Updates details of a student such as name, email, and home address. Only accessible by the student identified by the transaction context.

## Setup

### Prerequisites

1. **Rust and Cargo**: Install Rust and Cargo on your development machine by following the official Rust installation instructions.

2. **SUI Blockchain**: Set up a local instance of the SUI blockchain for development and testing purposes. Refer to the SUI documentation for installation instructions.

### Build and Deploy

1. Clone the LMS module repository and navigate to the project directory on your local machine.

2. Compile the smart contract code using the following command:

   ```bash
   sui move build
   ```

3. Deploy the compiled smart contract to your local SUI blockchain node using the SUI CLI or other deployment tools.

4. Note the contract address and other relevant identifiers for interacting with the deployed contract.

## Usage

### Managing Institutes and Courses

Create new institutes, add courses, update course details, manage enrollments, and handle enrollment requests using the provided functions.

### Student Management

Create new students, update student details, check student balances, and fund student accounts securely using blockchain transactions.

### Grant Management

Initiate grant requests, approve grant requests, and manage grant approvals transparently using blockchain-powered functionalities.

### Financial Transactions

Withdraw funds from institute balances, add funds to student balances, and ensure secure financial transactions between stakeholders.

## Interacting with the Smart Contract

### Using the SUI CLI

1. Utilize the SUI CLI to interact with the deployed smart contract, providing function arguments and transaction contexts as required.

2. Monitor transaction outputs and blockchain events to track institute operations, student enrollments, grant approvals, and financial transactions within the decentralized learning management system.

## Conclusion

The Learning Management System (LMS) module provides a decentralized platform for managing educational institutes, courses, student enrollments, and grant approvals. By leveraging blockchain technology, this module ensures transparency, security, and efficiency in the management of educational transactions, fostering a conducive environment for institutes, students, and educational stakeholders.