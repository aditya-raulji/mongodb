# Task 1: Create a "CodingGita Students" database

## **Assignment: Building the "CodingGita Students" Database**

#### In this article, we will walk through a practical assignment that helps you solidify the concepts you've learned so far. You will be creating a "CodingGita Students" database with two collections: students and courses. You will also perform basic CRUD operations (Create, Read, Update, Delete) to manage the data. By the end of this task, you will have hands-on experience with inserting, querying, and modifying data in MongoDB.

## First task in 9 assigbment that sir geevel withe their example

### 1. Create the Database and Collections

- First, let’s create a new database called CodingGita. Inside this database, we will create two collections: students and courses.

#### Step 1: Create the database

````jsx 
use codinggita  // Switch to the CodingGita database. If it doesn't exist, MongoDB will create it automatically.
````

#### Step 2: Create the students collection

```jsx
 db.createCollection("students"); 
 ```

#### Step 3: Create the courses collection
```jsx
 db.createCollection("courses"); 
 ```

- At this point, you have created an empty database with two collections. Next, let’s move on to adding sample data into these collections.

### 2. Insert Sample Data
- Now, let's insert some sample data into both the students and courses collections.

#### #Step 1: Insert sample data into the students collection

  ````jsx 
  db.students.insertMany([
  { 
    "name": "Aditya",
    "rollNumber": 100,
    "department": "Computer Science",
    "year": 1,
    "coursesEnrolled": ["CS101", "CS102"]
  },
  { 
    "name": "Ridhm",
    "rollNumber": 101,
    "department": "Computer Science",
    "year": 1,
    "coursesEnrolled": ["CS101", "CS103"]
  },
  { 
    "name": "Rijans",
    "rollNumber": 102,
    "department": "Electrical Engineering",
    "year": 2,
    "coursesEnrolled": ["EE101", "EE102"]
  }
]); 
````
#### Step 2: Insert sample data into the courses collection


````jsx
db.courses.insertMany([
  { 
    "courseCode": "CS101", 
    "courseName": "Introduction to Programming", 
    "credits": 3, 
    "instructor": "Prof. Rs" 
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
    "instructor": "Prof. Khan" 
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
````

- At this point, you have successfully inserted data into the students and courses collections.



# Task 2: Perform CRUD operations

 - Add a few more students and courses to the database.

 ```jsx
db.students.insertMany([
  {
    "name": "Sanjana",
    "rollNumber": 103,
    "department": "Mechanical Engineering",
    "year": 2,
    "coursesEnrolled": ["ME101", "ME102"]
  },
  {
    "name": "Aarav",
    "rollNumber": 104,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS104"]
  }
]);
```

###  Add More Courses:

```jsx

db.courses.insertMany([
  {
    "courseCode": "CS104",
    "courseName": "Operating Systems",
    "credits": 3,
    "instructor": "Prof. Sharma"
  },
  {
    "courseCode": "ME101",
    "courseName": "Thermodynamics",
    "credits": 4,
    "instructor": "Prof. Nair"
  },
  {
    "courseCode": "ME102",
    "courseName": "Fluid Mechanics",
    "credits": 4,
    "instructor": "Prof. Patel"
  }
]);
```


## 3. Querying Data

- Now, let's perform some queries to fetch data based on different conditions.

- Step 1: Query students based on department If we want to find all students in the Computer Science department, we can use the find method with a query filter.

```jsx
 db.students.find({ "department": "Computer Science" }); 
 ```

- This query will return all students who belong to the Computer Science department.


#### Step 2: Query students based on year If we want to find students who are in year 2, we can query the students collection like this:

````jsx 
db.students.find({ "year": 2 }); 
````

-  This will return all students who are in the second year.

##### Step 3: Query students by course enrollment Let’s say you want to find all students who are enrolled in CS101. You can perform the following query:

```jsx
db.students.find({ "coursesEnrolled": "CS101" });
```

- This query will return all students who are enrolled in the CS101 course.

#### 4. Updating Data

- Updating data in MongoDB is easy with the updateOne and updateMany methods. Let’s go through some examples of how to update data.

- Step 1: Update a student’s courses Let’s say Arjun wants to update his courses and add the CS102 course to his list of enrolled courses.

```jsx
db.students.updateOne(
  { "name": "104" },
  { $push: { "coursesEnrolled": "CS103" } }
);
```

- This command will update Arjun’s document by pushing CS102 into his coursesEnrolled array.

- Step 2: Update a course instructor If Prof. Gupta is no longer teaching Data Structures (CS102), we can update the instructor for that course.

```jsx
db.courses.updateOne(
  { "courseCode": "CS104" },
  { $set: { "instructor": "Prof. Sharma" } }
);

```

- This query updates the instructor field for the course CS102 to Prof. Mehta.

### 5. Deleting Data
- Deleting data in MongoDB is straightforward. You can use the deleteOne or deleteMany methods to remove documents.

- Step 1: Delete a student record If we want to delete Arjun’s student record from the database, we can do so with the following command:

```jsx 
db.students.deleteOne({rollNumber: 102  });
```

- This will delete the document where the name field is Arjun.

- Step 2: Delete all students from a specific department Let’s say we want to remove all students from the Electrical Engineering department:

```jsx
db.students.deleteMany({ courseCode: "ME101" });
```

- This will delete all students in the Electrical Engineering department.

