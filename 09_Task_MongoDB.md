## **Assignment: Building the "CodingGita Students" Database**


## **6. Practice Assignments**

### **Task 1: Create a "CodingGita Students" database**

Create a new MongoDB database called `CodingGita`. Add two collections:
- `students`: Name, roll number, department, year, courses enrolled.
- `courses`: Course code, name, credits, instructor.

### **Ans:-**  
**step-1 : create a new database**  
    `use CodingGita`

**step-2 : Add two collections**  
  ```js 
  db.createCollection("students")
  ```
  ```js 
  db.createCollection("corses")
  ```

**step-3 : Add sample data in both**  
 ```js
 // students collection
db.students.insertMany([
  { 
    "name": "Jenil",
    "rollNumber": 101,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS102"]
  },
  { 
    "name": "Mahir",
    "rollNumber": 102,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS103"]
  },
  { 
    "name": "Arjun",
    "rollNumber": 103,
    "department": "Electrical Engineering",
    "year": 3,
    "coursesEnrolled": ["EE101", "EE102"]
  }
])

// courses collection
db.courses.insertMany([
  { 
    "courseCode": "CS101", 
    "courseName": "Introduction to Programming", 
    "credits": 3, 
    "instructor": "Prof. Sharma" 
  },
  { 
    "courseCode": "CS102", 
    "courseName": "Data Structures", 
    "credits": 3, 
    "instructor": "Prof. Gupta" 
  },
  { 
    "courseCode": "CS103", 
    "courseName": "Algorithms", 
    "credits": 3, 
    "instructor": "Prof. Kapoor" 
  },
  { 
    "courseCode": "EE101", 
    "courseName": "Basic Electrical Engineering", 
    "credits": 4, 
    "instructor": "Prof. Verma" 
  },
  { 
    "courseCode": "EE102", 
    "courseName": "Circuit Theory", 
    "credits": 4, 
    "instructor": "Prof. Yadav" 
  }
]);
 ```


### **Task 2: Perform CRUD operations**
- Add a few more students and courses to the database.
- Query data based on:
  - Department (e.g., "Computer Science").
  ```js
  db.students.find({"department":"Computer Science"})

  // Output:
  {
  _id: ObjectId('677bd1e0e2d99e18dfecccfb'),
  name: 'Jenil',
  rollNumber: 101,
  department: 'Computer Science',
  year: 2,
  coursesEnrolled: [
    'CS101',
    'CS102'
    ]
  }

  {
  _id: ObjectId('677bd1e0e2d99e18dfecccfc'),
  name: 'Mahir',
  rollNumber: 102,
  department: 'Computer Science',
  year: 2,
  coursesEnrolled: [
    'CS101',
    'CS103'
    ]
  }

  ```
  - Year (e.g., "2").
  ```js
  db.students.find({"year":2})

  // Output:

  {
  _id: ObjectId('677bd1e0e2d99e18dfecccfb'),
  name: 'Jenil',
  rollNumber: 101,
  department: 'Computer Science',
  year: 2,
  coursesEnrolled: [
    'CS101',
    'CS102'
    ]
  }

  {
  _id: ObjectId('677bd1e0e2d99e18dfecccfc'),
  name: 'Mahir',
  rollNumber: 102,
  department: 'Computer Science',
  year: 2,
  coursesEnrolled: [
    'CS101',
    'CS103'
    ]
  }

  ```


  - Courses enrolled (e.g., "CS101").
  ```js
  db.students.find({"coursesEnrolled":"CS102"})
  // Output:

  {
  _id: ObjectId('677bd1e0e2d99e18dfecccfb'),
  name: 'Jenil',
  rollNumber: 101,
  department: 'Computer Science',
  year: 2,
  coursesEnrolled: [
    'CS101',
    'CS102'
    ]
  }
  ```

- Update the courses for a specific student (e.g., adding a new course).

```js
// Update the courses for a specific student
db.students.updateOne({"name":"Mahir"},{$set:{coursesEnrolled : ['CS101', 'CS103', 'CS105']}})


// Output:
db.students.find({"coursesEnrolled":"CS105"})

{
  _id: ObjectId('677bd1e0e2d99e18dfecccfc'),
  name: 'Mahir',
  rollNumber: 102,
  department: 'Computer Science',
  year: 2,
  coursesEnrolled: [
    'CS101',
    'CS103',
    'CS105'
  ]
} 

```
- Delete a student or course from the database.
```js
// Delete a student
db.students.deleteOne({"name":"Mahir"})


// Delete a course
db.coueses.deleteOne({"courseCode":'CS101'})
```

---

#### **7. Resources for Further Learning**
  
- **MongoDB Official Documentation**: Explore MongoDB’s official documentation to understand syntax, advanced features, and best practices. [MongoDB Docs](https://docs.mongodb.com/)

- **MongoDB University**: Access free courses for structured learning and certification. MongoDB University offers comprehensive, beginner-friendly tutorials. [MongoDB University](https://university.mongodb.com/)

---