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
