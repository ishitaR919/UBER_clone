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

# /users/profile Endpoint

## Description

This endpoint returns the profile information of the authenticated user. The user must be logged in and provide a valid JWT token (usually via cookies or Authorization header).

## HTTP Method & URL

GET /users/profile

## Authentication

- Required: Yes (JWT token via cookie or Authorization header)

## Successful Response

- Status Code: 200
- Description: Returns the user's profile information.

### Example Response

```json
{
  "_id": "609e1257f28b3c0015d3e8c2",
  "fullname": {
    "firstname": "Jane",
    "lastname": "Doe"
  },
  "email": "jane.doe@example.com",
 
}
```

## Error Responses

- 401 Unauthorized: Missing or invalid authentication token.
- 500 Internal Server Error: An unexpected error occurred on the server.

---

# /users/logout Endpoint

## Description

This endpoint logs out the authenticated user by clearing the authentication token and blacklisting it to prevent further use.

## HTTP Method & URL

GET /users/logout

## Authentication

- Required: Yes (JWT token via cookie or Authorization header)

## Successful Response

- Status Code: 200
- Description: User successfully logged out.

### Example Response

```json
{
  "message": "Logged out"
}
```

## Error Responses

- 401 Unauthorized: Missing or invalid authentication token.
- 500 Internal Server Error: An unexpected error occurred on the server.

---

# Captain Routes Documentation

## /captains/register Endpoint

### Description

This endpoint registers a new captain (driver) along with their vehicle details. It validates the input data and creates a new captain in the system.

### HTTP Method & URL

POST /captains/register

### Required Request Data

- **fullname**:
  - **firstname**: string (required, minimum 3 characters)
  - **lastname**: string (required, minimum 3 characters)
- **email**: string (required, valid email format)
- **password**: string (required, minimum 6 characters)
- **vehicle**:
  - **color**: string (required, minimum 3 characters)
  - **plate**: string (required, minimum 3 characters)
  - **capacity**: integer (required, minimum 1)
  - **vehicleType**: string (required, one of: `"car"`, `"motorcycle"`, `"auto"`)

### Example Request Body

```json
{
  "fullname": {
    "firstname": "Alex",
    "lastname": "Smith"
  },
  "email": "alex.smith@example.com",
  "password": "securePassword123",
  "vehicle": {
    "color": "Red",
    "plate": "XYZ1234",
    "capacity": 4,
    "vehicleType": "car"
  }
}
```

### Successful Response

- **Status Code:** 201
- **Description:** Captain successfully registered.

### Example Response

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "captain": {
    "_id": "60a1b2c3d4e5f6a7b8c9d0e1",
    "fullname": {
      "firstname": "Alex",
      "lastname": "Smith"
    },
    "email": "alex.smith@example.com",
    "vehicle": {
      "color": "Red",
      "plate": "XYZ1234",
      "capacity": 4,
      "vehicleType": "car"
    }
  }
}
```

### Error Responses

- **400 Bad Request:** Input validation failed (e.g., missing or invalid fields).
- **500 Internal Server Error:** An unexpected error occurred on the server.

---

> **Note:**  
> Login, profile, and logout endpoints for captains are currently commented out and not available.




