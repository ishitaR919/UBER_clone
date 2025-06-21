# /users/register Endpoint

## Description

This endpoint registers a new user. It validates the input data and creates a new user in the system.

## HTTP Method & URL

POST /users/register


## Required Request Data

- fullname:
  - firstname: string (required, minimum 3 characters)
  - lastname: string (required, minimum 3 characters)
- email: string (required, valid email format, minimum 5 characters)
- password: string (required, minimum 6 characters)

## Successful Response

- Status Code: 200 (or 201)
- Description: User successfully registered.


## Error Responses

- 400 Bad Request: Input validation failed (e.g., invalid email, insufficient character length, or missing fields).
- 500 Internal Server Error: An unexpected error occurred on the server.



## Example Responses

- user (object):
  - fullname (object):
    - firstname (String): string (required, minimum 3 characters).
    - lastname (String): string (required, minimum 3 characters).
  - email (String): string (required, valid email format, minimum 5 characters).
  - password (String): string (required, minimum 6 characters).
- token (String): JWT Token

# /users/login Endpoint

## Description

This endpoint authenticates an existing user. It validates the input data, checks the credentials, and returns a JWT token if authentication is successful.

## HTTP Method & URL

POST /users/login

## Required Request Data

- email: string (required, valid email format, minimum 5 characters)
- password: string (required, minimum 6 characters)

## Successful Response

- Status Code: 200
- Description: User successfully authenticated.

### Example Response

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "_id": "609e1257f28b3c0015d3e8c2",
    "fullname": {
      "firstname": "Jane",
      "lastname": "Doe"
    },
    "email": "jane.doe@example.com"
  }
}
```




