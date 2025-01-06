

## **6. More Practice Tasks**

### **Task 1: Add multiple students**
Insert at least **5 students** into the `students` collection with unique roll numbers, names, departments, years, and subjects enrolled.
#### **ANS**
```js
db.students.insertMany([
  { 
    "name": "Jenil",
    "rollNumber": 101,
    "department": "Computer Science",
    "year": 2,
    "subjectsEnrolled": ["React", "NodeJS", "MongoDB"]
  },
  { 
    "name": "Mahir",
    "rollNumber": 102,
    "department": "Computer Science",
    "year": 2,
    "subjectsEnrolled": ["React", "NodeJS"]
  },
  { 
    "name": "Jatan",
    "rollNumber": 103,
    "department": "EC Engineering",
    "year": 2,
    "subjectsEnrolled": ["EC Theory", "Electrical Machines"]
  },
  { 
    "name": "Arjun",
    "rollNumber": 104,
    "department": "Electrical Engineering",
    "year": 3,
    "subjectsEnrolled": ["Circuit Theory", "Electrical Machines"]
  },
  { 
    "name": "Jagjeet",
    "rollNumber": 105,
    "department": "AI and ML Engineering",
    "year": 3,
    "subjectsEnrolled": ["AI Theory", "ML Machines"]
  }
]);
```

## **Task 2: Add multiple subjects**
Insert **4 subjects** into the `subjects` collection, each with 3 to 5 topics.
#### **ANS :**
```js
db.subjects.insertMany([
  { 
    "subjectName": "React",
    "topics": [
      "JSX", 
      "Components", 
      "State", 
      "Props", 
      "Hooks"
    ]
  },
  { 
    "subjectName": "NodeJS", 
    "topics": [
      "Modules", 
      "Express", 
      "File System", 
      "Asynchronous Programming"
    ]
  },
  { 
    "subjectName": "MongoDB", 
    "topics": [
      "Database Design", 
      "CRUD Operations", 
      "Aggregation", 
      "Indexes"
    ]
  },
  { 
    "subjectName": "HTML & CSS", 
    "topics": [
      "HTML tags", 
      "CSS selectors", 
      "CSS Styling", 
      "Indexes"
    ]
  }
]);
```

## **Task 3: Query students based on subject enrollment**
Query the `students` collection to find all students who are enrolled in **NodeJS**.
#### **ANS**
```js
db.students.find({"subjectsEnrolled":"NodeJS"})

//Output:
{
  _id: ObjectId('677bdb54e2d99e18dfeccd03'),
  name: 'Jenil',
  rollNumber: 101,
  department: 'Computer Science',
  year: 2,
  subjectsEnrolled: [
    'React',
    'NodeJS',
    'MongoDB'
  ]
}
{
  _id: ObjectId('677bdb54e2d99e18dfeccd04'),
  name: 'Mahir',
  rollNumber: 102,
  department: 'Computer Science',
  year: 2,
  subjectsEnrolled: [
    'React',
    'NodeJS'
  ]
}
```

## **Task 4: Add a new topic to a subject**
Add a new topic to the **NodeJS** subject.
#### **ANS**
```js
db.subjects.updateOne({"subjectName":"NodeJS"}, {$push:{"topics":"CRUD API"}})

// Output:
{
  _id: ObjectId('677bdb68e2d99e18dfeccd09'),
  subjectName: 'NodeJS',
  topics: [
    'Modules',
    'Express',
    'File System',
    'Asynchronous Programming',
    'CRUD API'
  ]
}
```

## **Task 5: Query subjects with multiple topics**
Query the `subjects` collection to find subjects that contain **at least 5 topics**.
#### **ANS**
```js
db.subjects.find({$where: "this.topics.length >= 5"}).pretty()

// Output:
{
  _id: ObjectId('677bdb68e2d99e18dfeccd08'),
  subjectName: 'React',
  topics: [
    'JSX',
    'Components',
    'State',
    'Props',
    'Hooks'
  ]
}

{
  _id: ObjectId('677bdb68e2d99e18dfeccd09'),
  subjectName: 'NodeJS',
  topics: [
    'Modules',
    'Express',
    'File System',
    'Asynchronous Programming',
    'CRUD API'
  ]
}
```

## **Task 6: Update student enrollment**
Add the subject **"React Native"** to **Jenil's** subjects.
#### **ANS**
```js
db.students.updateOne({"name":"Jenil"},{$push : {"subjectsEnrolled":"React Native"}})

// Output:
{
  _id: ObjectId('677bdb54e2d99e18dfeccd03'),
  name: 'Jenil',
  rollNumber: 101,
  department: 'Computer Science',
  year: 2,
  subjectsEnrolled: [
    'React',
    'NodeJS',
    'MongoDB',
    'React Native'
  ]
}
```

## **Task 7: Query all students**
Query all students in the database and print out their names and enrolled subjects.
#### **ANS**
```js
db.students.find({},{name:1, subjectsEnrolled:1, _id:0}).pretty()

// Output:
{
  name: 'Jenil',
  subjectsEnrolled: [
    'React',
    'NodeJS',
    'MongoDB',
    'React Native'
  ]
}

{
  name: 'Mahir',
  subjectsEnrolled: [
    'React',
    'NodeJS'
  ]
}

{
  name: 'Jatan',
  subjectsEnrolled: [
    'EC Theory',
    'Electrical Machines'
  ]
}
```

## **Task 8: Update multiple students' year**
Update the year for all students in the **Computer Science** department to year 3.
#### **ANS**
```js
db.students.updateMany({"department":"Computer Science"},{$set:{"year":3}})

// Output:
{
  _id: ObjectId('677bdb54e2d99e18dfeccd03'),
  name: 'Jenil',
  rollNumber: 101,
  department: 'Computer Science',
  year: 3,
  subjectsEnrolled: [
    'React',
    'NodeJS',
    'MongoDB',
    'React Native'
  ]
}

{
  _id: ObjectId('677bdb54e2d99e18dfeccd04'),
  name: 'Mahir',
  rollNumber: 102,
  department: 'Computer Science',
  year: 3,
  subjectsEnrolled: [
    'React',
    'NodeJS'
  ]
}

{
  _id: ObjectId('677bdb54e2d99e18dfeccd06'),
  name: 'Arjun',
  rollNumber: 104,
  department: 'Electrical Engineering',
  year: 3,
  subjectsEnrolled: [
    'Circuit Theory',
    'Electrical Machines'
  ]
}
```

## **Task 9: Add new topics to multiple subjects**
Add new topics to **React**, **NodeJS**, and **MongoDB** subjects. Ensure each subject gets at least **one** new topic.
#### **ANS**
```js
// Update in React
db.subjects.updateOne({"subjectName":"React"}, {$push:{"topics":"DOM"}})

// Update in NodeJS
db.subjects.updateOne({"subjectName":"NodeJS"}, {$push:{"topics":"Authentication"}})

// Update in MongooDB
db.subjects.updateOne({"subjectName":"MongoDB"}, {$push:{"topics":"MongoShell"}})

```


## **Task 10: Remove a topic from a subject**
Remove the topic **"Express"** from the **NodeJS** subject.
#### **ANS**
```js
db.subjects.updateOne({"subjectName":"NodeJS"},{$pull:{"topics":"Express"}})
```

## **Task 11: Query all students in a specific year**
Query and return all students in **year 2** or **year 3**.
#### **ANS**
```js
db.students.find({$or:[{"year":2}, {"year":3}]})
```

## **Task 12: Delete a student by roll number**
Delete a student from the database using their **roll number**.
#### **ANS**
```js 
db.students.deleteOne({"rollNumber":104})
```

## **Task 13: Delete all students from a department**
Delete all students who belong to the **Electrical Engineering** department.
#### **ANS**
```js
db.students.deleteMany({"department":"Electrical Engineering"})
```

## **Task 14: Retrieve all topics for a subject**
Query the **MongoDB** subject and retrieve all topics listed for it.
#### **ANS**
```js
db.subjects.find({"name":"MongoDB"},{topics:1, _id:0})
```

## **Task 15: Count the number of subjects in which a student is enrolled**
Write a query that returns the number of subjects each student is enrolled in.
#### **ANS**
```js

```

---

