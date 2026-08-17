# REST API Documentation

## Base URL

https://student-task-backend-wmkv.onrender.com

## 1. Create Task

**Method:** `POST`  
**Endpoint:** `/api/tasks`  
**Purpose:** Creates a new task in the database.

### Request Body:

```json
{
  "title": "Testing API",
  "course": "BACSE344",
  "dueDate": "2026-08-18",
  "priority": "High"
}
```

### Successful Response: **201 Created**

```json
{
    "title": "Testing API",
    "course": "BACSE344",
    "dueDate": "2026-08-18T00:00:00.000Z",
    "priority": "High",
    "status": "Pending",
    "_id": "6a8337e1eab68a2463f269d9",
    "createdAt": "2026-08-17T16:33:37.816Z",
    "updatedAt": "2026-08-17T16:33:37.816Z",
    "__v": 0
}
```

**Note:** The response contains the newly created task, including the automatically generated: _id, Status: Pending, createdAt, updatedAt

## 2. Read Task

**Method:** `GET`  
**Endpoint:** `/api/tasks`  
**Purpose:** Retrieves all tasks stored in the MongoDB Atlas tasks collection

### Successful Response: **200 OK**

```json
[
    {
        "_id": "6a8337e1eab68a2463f269d9",
        "title": "Testing API",
        "course": "BACSE344",
        "dueDate": "2026-08-18T00:00:00.000Z",
        "priority": "High",
        "status": "Pending",
        "createdAt": "2026-08-17T16:33:37.816Z",
        "updatedAt": "2026-08-17T16:33:37.816Z",
        "__v": 0
    },
    {
        "_id": "6a80baaf766f604ecfe595c1",
        "title": "Complete Cloud Assignment",
        "course": "CS101",
        "dueDate": "2026-08-19T00:00:00.000Z",
        "priority": "High",
        "status": "Pending",
        "createdAt": "2026-08-15T19:14:55.983Z",
        "updatedAt": "2026-08-17T16:32:07.221Z",
        "__v": 0
    }
]
```

**Note:** Tasks are retrieved and sorted by due date in ascending order to help students view upcoming deadlines first.

## 3. Update Task

**Method:** `PUT`  
**Endpoint:** `/api/tasks/:id`  
**Purpose:** Updates an existing task using its unique _id

### Request Body:

```json
{
  "status": "In Progress"
}
```

### Successful Response: **200 OK**

```json
{
    "_id": "6a8337e1eab68a2463f269d9",
    "title": "Testing API",
    "course": "BACSE344",
    "dueDate": "2026-08-18T00:00:00.000Z",
    "priority": "High",
    "status": "In Progress",
    "createdAt": "2026-08-17T16:33:37.816Z",
    "updatedAt": "2026-08-17T16:46:56.076Z",
    "__v": 0
}
```

## 4. Delete Task

**Method:** `DELETE`  
**Endpoint:** `/api/tasks/:id`  
**Purpose:** Deletes a specific task from the database using its unique _id

### Successful Response: **200 OK**

```json
{
  "message": "Task deleted successfully"
}
```