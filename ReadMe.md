
## Board - Server part of the web application for registering tasks for company departments.

This repository contains the server component of the Board. It is a Spring Boot application that serves JSON data to power the frontend website and API.

## Requirements

For building and running the application you need:

- [JDK 1.8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
- [Maven 3](https://maven.apache.org)
- [MySQL](https://dev.mysql.com/downloads/mysql/)

## Running the application locally

There are several ways to run a Spring Boot application on your local machine. One way is to execute the `main` method in the `ru.lok.board.boardApplication` class from your IDE.

Alternatively you can use the [Spring Boot Maven plugin](https://docs.spring.io/spring-boot/docs/current/reference/html/build-tool-plugins-maven-plugin.html) like so:

```shell
mvn spring-boot:run
```

## API

There are four main entities in the system that a user may interact with: User, Task, Comment, and Department. 
These entities form a hierarchy that is reflected in the API endpoints.
A Department has one or more Task, each of which may have one or more Comments. User has one or more Task.

## Task

For most users, the primary entry point for the CIViC API will be the Task endpoint.
This endpoint allows a user to retrieve information about what Task are in Board.

### Gets a list of task

This endpoint returns a listing of Task in Board.
You can use the {page} and {pageSize} parameters to iterate through all the variants.

HTTP Request

```shell
GET http://localhost:8080/task/{page}/{pageSize}
```

### Add a Task

This endpoint adds a task to the Board.

HTTP Request

```shell
POST http://localhost:8080/task
```

RequestBody: {"userId":" ", "departmentId":"", "title": "", "message":""}

### Task update

This endpoint renews a task to the Board.

HTTP Request

```shell
PUT http://localhost:8080/task
```
RequestBody: {"id":"", "userId":"", "departmentId":"", "title":"", "message":""}

### Complited task.

This endpoint sets the completion flag for the task with the {id}.

HTTP Request

```shell
GET http://localhost:8080/task/{id}/setcomplit
```

## Department

### Add a Department

This endpoint adds a department to the Board.

HTTP Request

```shell
POST http://localhost:8080/department
```
RequestBody: {"id":"", "nameDepartment":"", "title":""}

### Department tasks.

Returns a list of department tasks. IdDepatment - {idDep}.

HTTP Request

```shell
GET http://localhost:8080/department/{idDep}/task/{page}/{pageSize}
```

### Deleting a department

This endpoint delete a department on the Board. IdDepatment - {idDep}.


HTTP Request

```shell
DELETE http://localhost:8080/department/delete/{idDep}
```

##User

### Gets a list of user

This endpoint returns a listing of User in Board.
You can use the {page} and {pageSize} parameters to iterate through all the variants.

HTTP Request

```shell
GET http://localhost:8080/user/{page}/{pageSize}
```

### Adding a user 

This endpoint adds a user.

HTTP Request

```shell
POST http://localhost:8080/user
```

RequestBody: {"username":"", "password":""}

### Updating a user

This endpoint udates a user.

HTTP Request

```shell
PUT http://localhost:8080/user
```
RequestBody: {"id":"", "username":"", "password":""}

### User search

This endpoint searches for a user by username.

HTTP Request

```shell
GET http://localhost:8080/user/serch/{username}
```

##Comment

### Find comment by id


This endpoint searches for a comment by id.

HTTP Request

```shell
GET http://localhost:8080/comment/{{id}}
```

### Add a comment

This endpoint adds a comment.

HTTP Request

```shell
POST http://localhost:8080/comment
```
RequestBody: {"taskId":"", "username":"", "message":""}

### Delet a coment

This endpoint deletes a comment.

HTTP Request

```shell
DELETE http://localhost:8080/comment/{id}
```

### Get a list of comments for the task

This endpoint gives a list of comments for a task.
HTTP Request

```shell
GET http://localhost:8080/comment/task/{taskId}/{page}/{pageSize}
```



## Copyright

Released under the MIT License

Copyright 2021 Barannikov Mikhail

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

