# Build your own API

In this assignment you will be tasked to build your own server that will serve as an API. You will be building a fully functional server that could, if deployed to the cloud, serve real live internet traffic and be integrated as a part of a web application.

------------

# Summary
You will be building a server that can keep track of tasks. Your server must be able to do the following:

- Use mongodb as a database
- Create a new task with a title property and a boolean determining whether the task has been completed. A new unique id would be created for each new task
- List all tasks created
- Get a specific task
- Delete a specified task
- Edit the title or completion of a specific task
- (Extra Credit) Bulk add multiple tasks in one request
- (Extra Credit) Bulk delete multiple tasks in one request

Your application will accept JSON and/or URL parameters and will return JSON data. Your server would be ready to be automatically integrated in a web system.

## List of endpoints to be created

Here is a specific list of endpoints that you will be required to create, along with the method and the inputs/outputs:

-------

### Create a new Task
```
POST /v1/tasks
```
#### Input
```
{title: "Test Task 2"}
```
#### Output
```
{id: "507f191e810c19729de860ea"} (return a 201 code)
```
The id returned is a object id for the todo that was just created

-------

### List all tasks created
```
GET /v1/tasks
```
#### Input
```
None
```
#### Output
```
(return a 200 code)
{
   tasks: [
     {id: 1, title: "Test Task 1", is_completed: true},
     {id: 2, title: "Test Task 2", is_completed: false}
   ]
}
```
-------

### Get a specific task
```
GET /v1/tasks/{id}
```
#### Input
```
id (passed through the URL)
```
#### Output
```
(return a 200 code)
{id: 3, title: "Test Task 2", is_completed: false}
```
#### On Error
```
if id not found:
(return a 404 code)

{ 
    error: "There is no task at that id"
}
```

-------

### Delete a specific task
```
DELETE /v1/tasks/{id}
```
#### Input
```
id (passed through the URL)
```
#### Output
```
None (return a 204 code)
```

-------

###Edit the title or completion of a specific task
```
PUT /v1/tasks/{id}
```
#### Input
```
{title: "Test Task 2", is_completed: false}
```
#### Output
```
None (return a 204 code)
```
#### On Error
```
if id not found:
(return a 404 code)

{ 
    error: "There is no task at that id"
}
```

-------

### (Extra Credit) Bulk add tasks
```
POST /v1/tasks
```
#### Input
```
{
   tasks: [
      {title: "Test Task 1", is_completed: true},
      {title: "Test Task 2", is_completed: false},
      {title: "Test Task 3", is_completed: true}
   ]
}
```
#### Output
```
(return a 201 code)
{
   tasks: [
      {id: 507f191e810c19729de860ea},
      {id: 507f191e810c19729de860eb},
      {id: 507f191e810c19729de860ec}
   ]
}
```
Notes: This endpoint bulk adds more than one task. Note that this feature uses the same endpoint as the single task creation endpoint

-------
### (Extra Credit) Bulk delete tasks
```
DELETE /v1/tasks
```
#### Input
```
{
   tasks: [
     {id: 507f191e810c19729de860ea},
     {id: 507f191e810c19729de860eb},
     {id: 507f191e810c19729de860ec}
  ]
}
```
#### Output
```
None (return a 204 code)
```
