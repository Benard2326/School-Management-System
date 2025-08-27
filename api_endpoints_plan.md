# Comprehensive API Endpoints Plan

## 1. Overview

This document outlines all the API endpoints required for the school management system, organized by feature domain. Each endpoint includes HTTP method, path, request/response specifications, and implementation notes.

## 2. API Structure

### 2.1 Base URL
```
http://localhost:5000/api
```

### 2.2 API Versioning
```
http://localhost:5000/api/v1
```

### 2.3 Authentication
All protected endpoints require a JWT token in the Authorization header:
```
Authorization: Bearer <token>
```

## 3. Authentication Endpoints

### 3.1 User Registration
```
POST /auth/register
```

**Request Body:**
```json
{
  "username": "string",
  "email": "string",
  "password": "string",
  "role": "admin|teacher|student|guardian",
  "firstName": "string",
  "lastName": "string",
  "dateOfBirth": "date",
  "gender": "male|female|other",
  "address": "string",
  "contactNumber": "string"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "user": {
      "id": "string",
      "username": "string",
      "email": "string",
      "role": "string",
      "firstName": "string",
      "lastName": "string",
      "dateOfBirth": "date",
      "gender": "string",
      "address": "string",
      "contactNumber": "string",
      "isActive": true,
      "createdAt": "date"
    },
    "token": "string"
  }
}
```

### 3.2 User Login
```
POST /auth/login
```

**Request Body:**
```json
{
  "email": "string",
  "password": "string"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "user": {
      "id": "string",
      "username": "string",
      "email": "string",
      "role": "string",
      "firstName": "string",
      "lastName": "string",
      "isActive": true,
      "lastLogin": "date"
    },
    "token": "string"
  }
}
```

### 3.3 User Logout
```
POST /auth/logout
```

**Response:**
```json
{
  "success": true,
  "message": "Logged out successfully"
}
```

### 3.4 Get User Profile
```
GET /auth/profile
```

**Response:**
```json
{
  "success": true,
  "data": {
    "user": {
      "id": "string",
      "username": "string",
      "email": "string",
      "role": "string",
      "firstName": "string",
      "lastName": "string",
      "dateOfBirth": "date",
      "gender": "string",
      "address": "string",
      "contactNumber": "string",
      "profilePicture": "string",
      "isActive": true,
      "createdAt": "date",
      "updatedAt": "date"
    }
  }
}
```

### 3.5 Update User Profile
```
PUT /auth/profile
```

**Request Body:**
```json
{
  "firstName": "string",
  "lastName": "string",
  "dateOfBirth": "date",
  "gender": "string",
  "address": "string",
  "contactNumber": "string",
  "profilePicture": "string"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "user": {
      "id": "string",
      "username": "string",
      "email": "string",
      "role": "string",
      "firstName": "string",
      "lastName": "string",
      "dateOfBirth": "date",
      "gender": "string",
      "address": "string",
      "contactNumber": "string",
      "profilePicture": "string",
      "isActive": true,
      "createdAt": "date",
      "updatedAt": "date"
    }
  }
}
```

### 3.6 Change Password
```
PUT /auth/password
```

**Request Body:**
```json
{
  "currentPassword": "string",
  "newPassword": "string"
}
```

**Response:**
```json
{
  "success": true,
  "message": "Password changed successfully"
}
```

### 3.7 Forgot Password
```
POST /auth/forgot-password
```

**Request Body:**
```json
{
  "email": "string"
}
```

**Response:**
```json
{
  "success": true,
  "message": "Password reset instructions sent to your email"
}
```

### 3.8 Reset Password
```
POST /auth/reset-password
```

**Request Body:**
```json
{
  "token": "string",
  "newPassword": "string"
}
```

**Response:**
```json
{
  "success": true,
  "message": "Password reset successfully"
}
```

## 4. Student Management Endpoints

### 4.1 Get All Students
```
GET /students
```

**Query Parameters:**
- `classId` (string): Filter by class
- `status` (string): Filter by status (active, inactive, graduated)
- `page` (number): Page number (default: 1)
- `limit` (number): Number of items per page (default: 10)

**Response:**
```json
{
  "success": true,
  "data": [
    {
      "id": "string",
      "firstName": "string",
      "lastName": "string",
      "dateOfBirth": "date",
      "gender": "string",
      "address": "string",
      "contactNumber": "string",
      "guardianId": "string",
      "classId": "string",
      "enrollmentDate": "date",
      "status": "active|inactive|graduated",
      "createdAt": "date",
      "updatedAt": "date"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 10,
    "total": 100,
    "pages": 10
  }
}
```

### 4.2 Get Student by ID
```
GET /students/:id
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "firstName": "string",
    "lastName": "string",
    "dateOfBirth": "date",
    "gender": "string",
    "address": "string",
    "contactNumber": "string",
    "guardianId": "string",
    "classId": "string",
    "enrollmentDate": "date",
    "status": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 4.3 Create Student
```
POST /students
```

**Request Body:**
```json
{
  "firstName": "string",
  "lastName": "string",
  "dateOfBirth": "date",
  "gender": "string",
  "address": "string",
  "contactNumber": "string",
  "guardianId": "string",
  "classId": "string",
  "enrollmentDate": "date"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "firstName": "string",
    "lastName": "string",
    "dateOfBirth": "date",
    "gender": "string",
    "address": "string",
    "contactNumber": "string",
    "guardianId": "string",
    "classId": "string",
    "enrollmentDate": "date",
    "status": "active",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 4.4 Update Student
```
PUT /students/:id
```

**Request Body:**
```json
{
  "firstName": "string",
  "lastName": "string",
  "dateOfBirth": "date",
  "gender": "string",
  "address": "string",
  "contactNumber": "string",
  "guardianId": "string",
  "classId": "string",
  "status": "active|inactive|graduated"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "firstName": "string",
    "lastName": "string",
    "dateOfBirth": "date",
    "gender": "string",
    "address": "string",
    "contactNumber": "string",
    "guardianId": "string",
    "classId": "string",
    "enrollmentDate": "date",
    "status": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 4.5 Delete Student
```
DELETE /students/:id
```

**Response:**
```json
{
  "success": true,
  "message": "Student deleted successfully"
}
```

## 5. Teacher Management Endpoints

### 5.1 Get All Teachers
```
GET /teachers
```

**Query Parameters:**
- `subjectId` (string): Filter by subject
- `status` (string): Filter by status (active, inactive)
- `page` (number): Page number (default: 1)
- `limit` (number): Number of items per page (default: 10)

**Response:**
```json
{
  "success": true,
  "data": [
    {
      "id": "string",
      "firstName": "string",
      "lastName": "string",
      "dateOfBirth": "date",
      "gender": "string",
      "address": "string",
      "contactNumber": "string",
      "subjectId": "string",
      "hireDate": "date",
      "qualification": "string",
      "status": "active|inactive",
      "createdAt": "date",
      "updatedAt": "date"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 10,
    "total": 50,
    "pages": 5
  }
}
```

### 5.2 Get Teacher by ID
```
GET /teachers/:id
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "firstName": "string",
    "lastName": "string",
    "dateOfBirth": "date",
    "gender": "string",
    "address": "string",
    "contactNumber": "string",
    "subjectId": "string",
    "hireDate": "date",
    "qualification": "string",
    "status": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 5.3 Create Teacher
```
POST /teachers
```

**Request Body:**
```json
{
  "firstName": "string",
  "lastName": "string",
  "dateOfBirth": "date",
  "gender": "string",
  "address": "string",
  "contactNumber": "string",
  "subjectId": "string",
  "hireDate": "date",
  "qualification": "string"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "firstName": "string",
    "lastName": "string",
    "dateOfBirth": "date",
    "gender": "string",
    "address": "string",
    "contactNumber": "string",
    "subjectId": "string",
    "hireDate": "date",
    "qualification": "string",
    "status": "active",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 5.4 Update Teacher
```
PUT /teachers/:id
```

**Request Body:**
```json
{
  "firstName": "string",
  "lastName": "string",
  "dateOfBirth": "date",
  "gender": "string",
  "address": "string",
  "contactNumber": "string",
  "subjectId": "string",
  "qualification": "string",
  "status": "active|inactive"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "firstName": "string",
    "lastName": "string",
    "dateOfBirth": "date",
    "gender": "string",
    "address": "string",
    "contactNumber": "string",
    "subjectId": "string",
    "hireDate": "date",
    "qualification": "string",
    "status": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 5.5 Delete Teacher
```
DELETE /teachers/:id
```

**Response:**
```json
{
  "success": true,
  "message": "Teacher deleted successfully"
}
```

## 6. Class Management Endpoints

### 6.1 Get All Classes
```
GET /classes
```

**Query Parameters:**
- `teacherId` (string): Filter by teacher
- `subjectId` (string): Filter by subject
- `page` (number): Page number (default: 1)
- `limit` (number): Number of items per page (default: 10)

**Response:**
```json
{
  "success": true,
  "data": [
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "teacherId": "string",
      "subjectId": "string",
      "startDate": "date",
      "endDate": "date",
      "capacity": 30,
      "status": "active|inactive",
      "createdAt": "date",
      "updatedAt": "date"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 10,
    "total": 20,
    "pages": 2
  }
}
```

### 6.2 Get Class by ID
```
GET /classes/:id
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "name": "string",
    "description": "string",
    "teacherId": "string",
    "subjectId": "string",
    "startDate": "date",
    "endDate": "date",
    "capacity": 30,
    "status": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 6.3 Create Class
```
POST /classes
```

**Request Body:**
```json
{
  "name": "string",
  "description": "string",
  "teacherId": "string",
  "subjectId": "string",
  "startDate": "date",
  "endDate": "date",
  "capacity": 30
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "name": "string",
    "description": "string",
    "teacherId": "string",
    "subjectId": "string",
    "startDate": "date",
    "endDate": "date",
    "capacity": 30,
    "status": "active",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 6.4 Update Class
```
PUT /classes/:id
```

**Request Body:**
```json
{
  "name": "string",
  "description": "string",
  "teacherId": "string",
  "subjectId": "string",
  "startDate": "date",
  "endDate": "date",
  "capacity": 30,
  "status": "active|inactive"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "name": "string",
    "description": "string",
    "teacherId": "string",
    "subjectId": "string",
    "startDate": "date",
    "endDate": "date",
    "capacity": 30,
    "status": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 6.5 Delete Class
```
DELETE /classes/:id
```

**Response:**
```json
{
  "success": true,
  "message": "Class deleted successfully"
}
```

## 7. Subject Management Endpoints

### 7.1 Get All Subjects
```
GET /subjects
```

**Query Parameters:**
- `page` (number): Page number (default: 1)
- `limit` (number): Number of items per page (default: 10)

**Response:**
```json
{
  "success": true,
  "data": [
    {
      "id": "string",
      "name": "string",
      "code": "string",
      "description": "string",
      "credits": 3,
      "createdAt": "date",
      "updatedAt": "date"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 10,
    "total": 15,
    "pages": 2
  }
}
```

### 7.2 Get Subject by ID
```
GET /subjects/:id
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "name": "string",
    "code": "string",
    "description": "string",
    "credits": 3,
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 7.3 Create Subject
```
POST /subjects
```

**Request Body:**
```json
{
  "name": "string",
  "code": "string",
  "description": "string",
  "credits": 3
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "name": "string",
    "code": "string",
    "description": "string",
    "credits": 3,
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 7.4 Update Subject
```
PUT /subjects/:id
```

**Request Body:**
```json
{
  "name": "string",
  "code": "string",
  "description": "string",
  "credits": 3
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "name": "string",
    "code": "string",
    "description": "string",
    "credits": 3,
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 7.5 Delete Subject
```
DELETE /subjects/:id
```

**Response:**
```json
{
  "success": true,
  "message": "Subject deleted successfully"
}
```

## 8. Attendance Management Endpoints

### 8.1 Get All Attendance Records
```
GET /attendance
```

**Query Parameters:**
- `classId` (string): Filter by class
- `date` (string): Filter by date (YYYY-MM-DD)
- `studentId` (string): Filter by student
- `page` (number): Page number (default: 1)
- `limit` (number): Number of items per page (default: 10)

**Response:**
```json
{
  "success": true,
  "data": [
    {
      "id": "string",
      "studentId": "string",
      "classId": "string",
      "date": "date",
      "status": "present|absent|late",
      "remarks": "string",
      "recordedBy": "string",
      "createdAt": "date",
      "updatedAt": "date"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 10,
    "total": 100,
    "pages": 10
  }
}
```

### 8.2 Get Attendance Record by ID
```
GET /attendance/:id
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "studentId": "string",
    "classId": "string",
    "date": "date",
    "status": "string",
    "remarks": "string",
    "recordedBy": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 8.3 Record Attendance
```
POST /attendance
```

**Request Body:**
```json
{
  "studentId": "string",
  "classId": "string",
  "date": "date",
  "status": "present|absent|late",
  "remarks": "string"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "studentId": "string",
    "classId": "string",
    "date": "date",
    "status": "string",
    "remarks": "string",
    "recordedBy": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 8.4 Update Attendance Record
```
PUT /attendance/:id
```

**Request Body:**
```json
{
  "status": "present|absent|late",
  "remarks": "string"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "studentId": "string",
    "classId": "string",
    "date": "date",
    "status": "string",
    "remarks": "string",
    "recordedBy": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 8.5 Delete Attendance Record
```
DELETE /attendance/:id
```

**Response:**
```json
{
  "success": true,
  "message": "Attendance record deleted successfully"
}
```

### 8.6 Get Attendance Summary
```
GET /attendance/summary/:classId
```

**Query Parameters:**
- `startDate` (string): Start date (YYYY-MM-DD)
- `endDate` (string): End date (YYYY-MM-DD)

**Response:**
```json
{
  "success": true,
  "data": {
    "classId": "string",
    "className": "string",
    "startDate": "date",
    "endDate": "date",
    "totalDays": 20,
    "attendanceStats": {
      "present": 18,
      "absent": 1,
      "late": 1
    },
    "studentAttendance": [
      {
        "studentId": "string",
        "studentName": "string",
        "present": 18,
        "absent": 1,
        "late": 1,
        "percentage": 95
      }
    ]
  }
}
```

## 9. Grade Management Endpoints

### 9.1 Get All Grades
```
GET /grades
```

**Query Parameters:**
- `studentId` (string): Filter by student
- `assignmentId` (string): Filter by assignment
- `classId` (string): Filter by class
- `page` (number): Page number (default: 1)
- `limit` (number): Number of items per page (default: 10)

**Response:**
```json
{
  "success": true,
  "data": [
    {
      "id": "string",
      "studentId": "string",
      "assignmentId": "string",
      "points": 85,
      "letterGrade": "B",
      "comments": "string",
      "gradedBy": "string",
      "gradedDate": "date",
      "createdAt": "date",
      "updatedAt": "date"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 10,
    "total": 50,
    "pages": 5
  }
}
```

### 9.2 Get Grade by ID
```
GET /grades/:id
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "studentId": "string",
    "assignmentId": "string",
    "points": 85,
    "letterGrade": "B",
    "comments": "string",
    "gradedBy": "string",
    "gradedDate": "date",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 9.3 Record Grade
```
POST /grades
```

**Request Body:**
```json
{
  "studentId": "string",
  "assignmentId": "string",
  "points": 85,
  "comments": "string"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "studentId": "string",
    "assignmentId": "string",
    "points": 85,
    "letterGrade": "B",
    "comments": "string",
    "gradedBy": "string",
    "gradedDate": "date",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 9.4 Update Grade
```
PUT /grades/:id
```

**Request Body:**
```json
{
  "points": 90,
  "comments": "string"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "studentId": "string",
    "assignmentId": "string",
    "points": 90,
    "letterGrade": "A-",
    "comments": "string",
    "gradedBy": "string",
    "gradedDate": "date",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 9.5 Delete Grade
```
DELETE /grades/:id
```

**Response:**
```json
{
  "success": true,
  "message": "Grade deleted successfully"
}
```

### 9.6 Get Student Report
```
GET /grades/report/student/:studentId
```

**Query Parameters:**
- `classId` (string): Filter by class
- `startDate` (string): Start date (YYYY-MM-DD)
- `endDate` (string): End date (YYYY-MM-DD)

**Response:**
```json
{
  "success": true,
  "data": {
    "student": {
      "id": "string",
      "firstName": "string",
      "lastName": "string"
    },
    "class": {
      "id": "string",
      "name": "string"
    },
    "assignments": [
      {
        "id": "string",
        "title": "string",
        "dueDate": "date",
        "maxPoints": 100,
        "points": 85,
        "letterGrade": "B",
        "gradedDate": "date"
      }
    ],
    "average": 85,
    "letterGrade": "B"
  }
}
```

### 9.7 Get Class Report
```
GET /grades/report/class/:classId
```

**Query Parameters:**
- `startDate` (string): Start date (YYYY-MM-DD)
- `endDate` (string): End date (YYYY-MM-DD)

**Response:**
```json
{
  "success": true,
  "data": {
    "class": {
      "id": "string",
      "name": "string"
    },
    "assignments": [
      {
        "id": "string",
        "title": "string",
        "dueDate": "date",
        "maxPoints": 100
      }
    ],
    "students": [
      {
        "student": {
          "id": "string",
          "firstName": "string",
          "lastName": "string"
        },
        "average": 85,
        "letterGrade": "B"
      }
    ],
    "classAverage": 82.5
  }
}
```

## 10. Assignment Management Endpoints

### 10.1 Get All Assignments
```
GET /assignments
```

**Query Parameters:**
- `classId` (string): Filter by class
- `subjectId` (string): Filter by subject
- `page` (number): Page number (default: 1)
- `limit` (number): Number of items per page (default: 10)

**Response:**
```json
{
  "success": true,
  "data": [
    {
      "id": "string",
      "title": "string",
      "description": "string",
      "classId": "string",
      "subjectId": "string",
      "assignedDate": "date",
      "dueDate": "date",
      "maxPoints": 100,
      "assignmentType": "homework|quiz|test|project|exam",
      "createdBy": "string",
      "createdAt": "date",
      "updatedAt": "date"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 10,
    "total": 25,
    "pages": 3
  }
}
```

### 10.2 Get Assignment by ID
```
GET /assignments/:id
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "title": "string",
    "description": "string",
    "classId": "string",
    "subjectId": "string",
    "assignedDate": "date",
    "dueDate": "date",
    "maxPoints": 100,
    "assignmentType": "string",
    "createdBy": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 10.3 Create Assignment
```
POST /assignments
```

**Request Body:**
```json
{
  "title": "string",
  "description": "string",
  "classId": "string",
  "subjectId": "string",
  "dueDate": "date",
  "maxPoints": 100,
  "assignmentType": "homework|quiz|test|project|exam"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "title": "string",
    "description": "string",
    "classId": "string",
    "subjectId": "string",
    "assignedDate": "date",
    "dueDate": "date",
    "maxPoints": 100,
    "assignmentType": "string",
    "createdBy": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 10.4 Update Assignment
```
PUT /assignments/:id
```

**Request Body:**
```json
{
  "title": "string",
  "description": "string",
  "dueDate": "date",
  "maxPoints": 100
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "title": "string",
    "description": "string",
    "classId": "string",
    "subjectId": "string",
    "assignedDate": "date",
    "dueDate": "date",
    "maxPoints": 100,
    "assignmentType": "string",
    "createdBy": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 10.5 Delete Assignment
```
DELETE /assignments/:id
```

**Response:**
```json
{
  "success": true,
  "message": "Assignment deleted successfully"
}
```

## 11. Fee Management Endpoints

### 11.1 Get All Invoices
```
GET /invoices
```

**Query Parameters:**
- `studentId` (string): Filter by student
- `status` (string): Filter by status (paid, unpaid, overdue)
- `page` (number): Page number (default: 1)
- `limit` (number): Number of items per page (default: 10)

**Response:**
```json
{
  "success": true,
  "data": [
    {
      "id": "string",
      "studentId": "string",
      "amount": 500,
      "dueDate": "date",
      "status": "paid|unpaid|overdue",
      "description": "string",
      "createdAt": "date",
      "updatedAt": "date"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 10,
    "total": 30,
    "pages": 3
  }
}
```

### 11.2 Get Invoice by ID
```
GET /invoices/:id
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "studentId": "string",
    "amount": 500,
    "dueDate": "date",
    "status": "string",
    "description": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 11.3 Create Invoice
```
POST /invoices
```

**Request Body:**
```json
{
  "studentId": "string",
  "amount": 500,
  "dueDate": "date",
  "description": "string"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "studentId": "string",
    "amount": 500,
    "dueDate": "date",
    "status": "unpaid",
    "description": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 11.4 Update Invoice
```
PUT /invoices/:id
```

**Request Body:**
```json
{
  "amount": 550,
  "dueDate": "date",
  "description": "string",
  "status": "paid|unpaid|overdue"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "studentId": "string",
    "amount": 550,
    "dueDate": "date",
    "status": "string",
    "description": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 11.5 Delete Invoice
```
DELETE /invoices/:id
```

**Response:**
```json
{
  "success": true,
  "message": "Invoice deleted successfully"
}
```

### 11.6 Get All Payments
```
GET /payments
```

**Query Parameters:**
- `studentId` (string): Filter by student
- `invoiceId` (string): Filter by invoice
- `page` (number): Page number (default: 1)
- `limit` (number): Number of items per page (default: 10)

**Response:**
```json
{
  "success": true,
  "data": [
    {
      "id": "string",
      "invoiceId": "string",
      "amount": 500,
      "paymentDate": "date",
      "paymentMethod": "cash|bank_transfer|credit_card|paypal",
      "referenceNumber": "string",
      "createdAt": "date",
      "updatedAt": "date"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 10,
    "total": 25,
    "pages": 3
  }
}
```

### 11.7 Get Payment by ID
```
GET /payments/:id
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "invoiceId": "string",
    "amount": 500,
    "paymentDate": "date",
    "paymentMethod": "string",
    "referenceNumber": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 11.8 Record Payment
```
POST /payments
```

**Request Body:**
```json
{
  "invoiceId": "string",
  "amount": 500,
  "paymentDate": "date",
  "paymentMethod": "cash|bank_transfer|credit_card|paypal",
  "referenceNumber": "string"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "invoiceId": "string",
    "amount": 500,
    "paymentDate": "date",
    "paymentMethod": "string",
    "referenceNumber": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 11.9 Update Payment
```
PUT /payments/:id
```

**Request Body:**
```json
{
  "amount": 550,
  "paymentDate": "date",
  "paymentMethod": "string",
  "referenceNumber": "string"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "invoiceId": "string",
    "amount": 550,
    "paymentDate": "date",
    "paymentMethod": "string",
    "referenceNumber": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 11.10 Delete Payment
```
DELETE /payments/:id
```

**Response:**
```json
{
  "success": true,
  "message": "Payment deleted successfully"
}
```

## 12. Timetable Management Endpoints

### 12.1 Get All Timetable Entries
```
GET /timetable
```

**Query Parameters:**
- `classId` (string): Filter by class
- `teacherId` (string): Filter by teacher
- `day` (string): Filter by day (monday, tuesday, etc.)
- `page` (number): Page number (default: 1)
- `limit` (number): Number of items per page (default: 10)

**Response:**
```json
{
  "success": true,
  "data": [
    {
      "id": "string",
      "classId": "string",
      "subjectId": "string",
      "teacherId": "string",
      "day": "monday",
      "startTime": "09:00",
      "endTime": "10:00",
      "room": "string",
      "createdAt": "date",
      "updatedAt": "date"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 10,
    "total": 40,
    "pages": 4
  }
}
```

### 12.2 Get Timetable Entry by ID
```
GET /timetable/:id
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "classId": "string",
    "subjectId": "string",
    "teacherId": "string",
    "day": "string",
    "startTime": "string",
    "endTime": "string",
    "room": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 12.3 Create Timetable Entry
```
POST /timetable
```

**Request Body:**
```json
{
  "classId": "string",
  "subjectId": "string",
  "teacherId": "string",
  "day": "monday",
  "startTime": "09:00",
  "endTime": "10:00",
  "room": "string"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "classId": "string",
    "subjectId": "string",
    "teacherId": "string",
    "day": "string",
    "startTime": "string",
    "endTime": "string",
    "room": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 12.4 Update Timetable Entry
```
PUT /timetable/:id
```

**Request Body:**
```json
{
  "day": "tuesday",
  "startTime": "10:00",
  "endTime": "11:00",
  "room": "string"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "classId": "string",
    "subjectId": "string",
    "teacherId": "string",
    "day": "string",
    "startTime": "string",
    "endTime": "string",
    "room": "string",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 12.5 Delete Timetable Entry
```
DELETE /timetable/:id
```

**Response:**
```json
{
  "success": true,
  "message": "Timetable entry deleted successfully"
}
```

### 12.6 Get Class Timetable
```
GET /timetable/class/:classId
```

**Response:**
```json
{
  "success": true,
  "data": {
    "classId": "string",
    "className": "string",
    "schedule": {
      "monday": [
        {
          "id": "string",
          "subject": "string",
          "teacher": "string",
          "startTime": "09:00",
          "endTime": "10:00",
          "room": "string"
        }
      ],
      "tuesday": [
        // ... timetable entries
      ]
    }
  }
}
```

## 13. Announcement Management Endpoints

### 13.1 Get All Announcements
```
GET /announcements
```

**Query Parameters:**
- `authorId` (string): Filter by author
- `page` (number): Page number (default: 1)
- `limit` (number): Number of items per page (default: 10)

**Response:**
```json
{
  "success": true,
  "data": [
    {
      "id": "string",
      "title": "string",
      "content": "string",
      "authorId": "string",
      "targetAudience": "all|students|teachers|parents",
      "priority": "low|medium|high",
      "startDate": "date",
      "endDate": "date",
      "createdAt": "date",
      "updatedAt": "date"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 10,
    "total": 15,
    "pages": 2
  }
}
```

### 13.2 Get Announcement by ID
```
GET /announcements/:id
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "title": "string",
    "content": "string",
    "authorId": "string",
    "targetAudience": "string",
    "priority": "string",
    "startDate": "date",
    "endDate": "date",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 13.3 Create Announcement
```
POST /announcements
```

**Request Body:**
```json
{
  "title": "string",
  "content": "string",
  "targetAudience": "all|students|teachers|parents",
  "priority": "low|medium|high",
  "startDate": "date",
  "endDate": "date"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "title": "string",
    "content": "string",
    "authorId": "string",
    "targetAudience": "string",
    "priority": "string",
    "startDate": "date",
    "endDate": "date",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 13.4 Update Announcement
```
PUT /announcements/:id
```

**Request Body:**
```json
{
  "title": "string",
  "content": "string",
  "targetAudience": "all|students|teachers|parents",
  "priority": "low|medium|high",
  "startDate": "date",
  "endDate": "date"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "string",
    "title": "string",
    "content": "string",
    "authorId": "string",
    "targetAudience": "string",
    "priority": "string",
    "startDate": "date",
    "endDate": "date",
    "createdAt": "date",
    "updatedAt": "date"
  }
}
```

### 13.5 Delete Announcement
```
DELETE /announcements/:id
```

**Response:**
```json
{
  "success": true,
  "message": "Announcement deleted successfully"
}
```

## 14. Error Handling

### 14.1 Standard Error Response Format
```json
{
  "success": false,
  "message": "Error message",
  "error": {
    "code": "ERROR_CODE",
    "details": "Additional error details"
  }
}
```

### 14.2 Common Error Codes
- `VALIDATION_ERROR`: Request validation failed
- `AUTHENTICATION_ERROR`: User not authenticated
- `AUTHORIZATION_ERROR`: User not authorized
- `NOT_FOUND`: Resource not found
- `DUPLICATE_ENTRY`: Resource already exists
- `SERVER_ERROR`: Internal server error

## 15. Rate Limiting

### 15.1 Rate Limit Headers
All responses will include rate limit headers:
```
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 999
X-RateLimit-Reset: 1625099000
```

### 15.2 Rate Limits
- Auth endpoints: 10 requests/minute
- Read endpoints: 1000 requests/hour
- Write endpoints: 100 requests/hour

## 16. API Documentation

### 16.1 Swagger/OpenAPI Specification
The API will be documented using OpenAPI 3.0 specification with Swagger UI for interactive documentation.

### 16.2 Example Documentation Structure
```yaml
openapi: 3.0.0
info:
  title: School Management System API
  version: 1.0.0
  description: API for managing school operations
servers:
  - url: http://localhost:5000/api/v1
    description: Development server
paths:
  /auth/login:
    post:
      summary: User login
      description: Authenticate user and return JWT token
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                email:
                  type: string
                  format: email
                password:
                  type: string
                  minLength: 6
      responses:
        '200':
          description: Successful login
          content:
            application/json:
              schema:
                type: object
                properties:
                  success:
                    type: boolean
                  data:
                    type: object
                    properties:
                      user:
                        $ref: '#/components/schemas/User'
                      token:
                        type: string
        '401':
          description: Invalid credentials
```

## 17. Implementation Roadmap

### 17.1 Phase 1: Core Authentication (Week 1)
- Implement auth endpoints
- Set up JWT authentication
- Create user management endpoints

### 17.2 Phase 2: Entity Management (Week 2)
- Implement student, teacher, class, subject endpoints
- Set up database models
- Create CRUD operations

### 17.3 Phase 3: Attendance and Grades (Week 3)
- Implement attendance endpoints
- Create grade management endpoints
- Add reporting endpoints

### 17.4 Phase 4: Advanced Features (Week 4)
- Implement fee management endpoints
- Create timetable endpoints
- Add announcement endpoints

### 17.5 Phase 5: Testing and Documentation (Week 5)
- Write comprehensive tests
- Create API documentation
- Performance optimization

### 17.6 Phase 6: Security and Deployment (Week 6)
- Implement rate limiting
- Add security headers
- Deploy to production