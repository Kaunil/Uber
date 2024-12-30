# User Registration Endpoint

## Endpoint
`POST /users/register`

## Description
This endpoint is used to register a new user. It requires the user's first name, last name, email, and password.

## Request Body
The request body should be a JSON object with the following structure:
```json
{
  "fullName": {
    "firstName": "string",
    "lastName": "string"
  },
  "email": "string",
  "password": "string"
}
```

### Example
```json
{
  "fullName": {
    "firstName": "John",
    "lastName": "Doe"
  },
  "email": "john.doe@example.com",
  "password": "password123"
}
```

## Response

### Success
- **Status Code:** `201 Created`
- **Body:**
  ```json
  {
    "token": "string",
    "user": {
      "_id": "string",
      "fullName": {
        "firstName": "string",
        "lastName": "string"
      },
      "email": "string",
      "socketId": "string"
    }
  }
  ```

### Error
- **Status Code:** `400 Bad Request`
- **Body:**
  ```json
  {
    "errors": [
      {
        "msg": "string",
        "param": "string",
        "location": "string"
      }
    ]
  }
  ```

## Validation
- `email` must be a valid email address.
- `fullName.firstName` must be at least 3 characters long.
- `password` must be at least 6 characters long.

# User Login Endpoint

## Endpoint
`POST /users/login`

## Description
This endpoint is used to log in an existing user. It requires the user's email and password.

## Request Body
The request body should be a JSON object with the following structure:
```json
{
  "email": "string",
  "password": "string"
}
```

### Example
```json
{
  "email": "john.doe@example.com",
  "password": "password123"
}
```

## Response

### Success
- **Status Code:** `200 OK`
- **Body:**
  ```json
  {
    "token": "string",
    "user": {
      "_id": "string",
      "fullName": {
        "firstName": "string",
        "lastName": "string"
      },
      "email": "string",
      "socketId": "string"
    }
  }
  ```

### Example
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "_id": "60d0fe4f5311236168a109ca",
    "fullName": {
      "firstName": "John",
      "lastName": "Doe"
    },
    "email": "john.doe@example.com",
    "socketId": "12345"
  }
}
```

### Error
- **Status Code:** `400 Bad Request`
- **Body:**
  ```json
  {
    "errors": [
      {
        "msg": "string",
        "param": "string",
        "location": "string"
      }
    ]
  }
  ```

- **Status Code:** `401 Unauthorized`
- **Body:**
  ```json
  {
    "message": "Invalid email or password"
  }
  ```

## Validation
- `email` must be a valid email address.
- `password` must be at least 6 characters long.
