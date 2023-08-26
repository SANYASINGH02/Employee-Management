# Employee-Management
This application is used to manage employees database.

Steps to run the project - 
>> Download and Install Java version 17.0.6  ( https://www.oracle.com/java/technologies/downloads/#jdk17-windows)

>> Download and Install MongoDB ( https://fastdl.mongodb.org/windows/mongodb-windows-x86_64-6.0.8-signed.msi ) , reference video for installation step - https://www.youtube.com/watch?v=8zQknJFjjrk 

>> Download codes and open it in intelliJ( or any IDE ) .
>> Download POSTMAN ( https://www.postman.com/downloads/ ). Click on 'New Request' and enter base url after running the MongodbemployeeApplication file from IntelliJ ( or any IDE )


>> For database , I am guiding you by running APIs because as written in assignment doc that we have to generate employee id by code and reportsTo parameter also take employee id so we can't assign it randomly .


The Employee Management API allows you to manage employees in a MongoDB database with pagination and sorting options.
I have implemented 2 levels Entry and Intermediate .



   API DOCUMENTATION ----


BASE URL -   http://localhost:8080
API Endpoints --

1 >>  Add Employee

Endpoint: /employees/add
Method: POST
Request Body:  give employee details in json format like example-
{
    "employeeName": "Sanya Singh",
    "phoneNumber": "2228222233",
    "email": "sanya.singh@example.com",
    "reportsTo": -1,
    "profileImage": "https://example.com/myimage1.jpg"
}
Response Body: generated employee-id
Description: Adds an employee to the database with the provided employee data. Generates a unique UUID as the employee ID.

suppose this endpoint generates employee id = 255
so insert next employee details and set reportsTo = 255
example-  
   {
        "employeeName": "Saurabh",
        "phoneNumber": "555555",
        "email": "saurabh2@example.com",
        "reportsTo": 255,
        "profileImage": "https://example.com/myimage2.jpg"
    }



2 >> Get All Employees

Endpoint: /employees/getAll
Method: GET
Parameters:
page (optional): Specifies the page number (default is 0).
size (optional): Specifies the page size (default is 3).
sort (optional): Specifies the sorting criteria, such as sort=employeeName,asc for ascending order by employee name. Multiple sort parameters can be provided, separated by commas.
Response:
HTTP Status Code: 200 (OK)
Response Body:contains all employees details
Description: Retrieves employees from the database with pagination and sorting options. Supports optional query parameters for pagination (page and size) and sorting (sort).



3>> Get Employee by ID 

Endpoint: /employees/get/{id}
Method: GET
Path Parameter:
id: The ID of the employee.
Description: Retrieves an employee details from the database based on their ID



4 >>  Delete Employee by ID

Endpoint: /employees/delete/{id}
Method: DELETE
Path Parameter:
id: The ID of the employee to be deleted.
Description: Deletes an employee from the database based on their ID



5 >>  Update Employee Details

Endpoint: /employees/update/{id}
Method: PUT
Path Parameter:
id: The ID of the employee whose details needs to be modified.
Request Body : enter the new details of this employee in json format as given in 1st API .
Description: Updates an employee based on their ID



6 >>  Get nth level Manager based on employee ID

Endpoint: /employees/get/{id}/manager/{level}
Method : GET
Path Parameter:
id: The ID of the employee .
level: level of the manager of employee .
Description: Takes an employee ID and a level (n) as input and returns the nth level manager of that employee.


