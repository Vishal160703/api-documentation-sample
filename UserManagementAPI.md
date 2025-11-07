User Management API Documentation
📚 Table of Contents

1. Overview

2. Authentication

3. Endpoints

GET /api/users

POST /api/users

PUT /apiusersid

DELETE /apiusersid

4. Error Handling

5. Notes

1. Overview

The User Management API allows clients to perform CRUD operations — Create, Read, Update, and Delete — on user data.
It’s designed for applications that manage user profiles, such as HR systems, CRMs, or customer management tools.

Base URL:

https://reqres.in

2. Authentication

This is a public API and does not require authentication for testing.
However, in real-world scenarios, most APIs use authentication to protect data.

Example (if authentication were required):

Authorization: Bearer <your_api_token>


Header Format:

Key	Value
Content-Type	application/json
Authorization	Bearer <token>
3. Endpoints
🟢 GET /api/users

Description:
Retrieve a list of users.

Request Example:

GET https://reqres.in/api/users?page=1


Query Parameters:

Name	Type	Required	Description
page	integer	No	Specifies which page of users to fetch

Response Example:

{
  "page": 1,
  "per_page": 6,
  "total": 12,
  "data": [
    {
      "id": 1,
      "email": "george.bluth@reqres.in",
      "first_name": "George",
      "last_name": "Bluth",
      "avatar": "https://reqres.in/img/faces/1-image.jpg"
    }
  ]
}


Response Codes:

Code	Meaning
200	OK – Request successful
404	Not Found – Invalid page number
500	Server Error – Internal failure
🟡 POST /api/users

Description:
Create a new user in the system.

Request Example:

POST https://reqres.in/api/users


Request Body:

{
  "name": "Vishal",
  "job": "Technical Writer"
}


Response Example:

{
  "name": "Vishal",
  "job": "Technical Writer",
  "id": "102",
  "createdAt": "2025-11-06T10:00:00.000Z"
}


Response Codes:

Code	Meaning
201	Created successfully
400	Bad Request – Missing fields
500	Server Error – Internal issue
🔵 PUT /api/users/{id}

Description:
Update existing user information by ID.

Request Example:

PUT https://reqres.in/api/users/2


Request Body:

{
  "name": "Vishal",
  "job": "Senior Technical Writer"
}


Response Example:

{
  "name": "Vishal",
  "job": "Senior Technical Writer",
  "updatedAt": "2025-11-06T10:05:00.000Z"
}


Response Codes:

Code	Meaning
200	OK – User updated
404	Not Found – Invalid user ID
500	Server Error
🔴 DELETE /api/users/{id}

Description:
Delete a user by ID.

Request Example:

DELETE https://reqres.in/api/users/2


Response Example:
No content returned

Status Code:

204 No Content


Response Codes:

Code	Meaning
204	Success – User deleted
404	Not Found – Invalid ID
500	Server Error
4. Error Handling
Code	Meaning	Possible Cause
400	Bad Request	Invalid input or missing parameter
401	Unauthorized	Missing or invalid token
404	Not Found	Resource or user not found
500	Internal Server Error	Unexpected server-side issue
5. Notes

All data is returned in JSON format.

Pagination is supported in the GET /api/users endpoint.

Data created or updated using ReqRes is mock data (temporary).

Each endpoint is designed for testing and learning API documentation.

✅ End of Documentation