# User Management API

## Setup

1. Clone the repository.
2. Run `npm install`.
3. Start the server: `node index.js`.
4. API will be available at `http://localhost:3000`.

## API Endpoints

### Get All Users
- **URL**: `/api/users`
- **Method**: `GET`
- **Success Response**:
  - Code: 200
  - Content: `[ { id: 1, name: "John", email: "john@example.com" }, ... ]`

### Get User by ID
- **URL**: `/api/users/:id`
- **Method**: `GET`
- **URL Params**: `id=[integer]`
- **Success Response**:
  - Code: 200
  - Content: `{ id: 1, name: "John", email: "john@example.com" }`
- **Error Response**:
  - Code: 404
  - Content: `{ message: "User not found" }`

### Create a New User
- **URL**: `/api/users`
- **Method**: `POST`
- **Body**: `{ "name": "Alice", "email": "alice@example.com" }`
- **Success Response**:
  - Code: 201
  - Content: `{ id: 3, name: "Alice", email: "alice@example.com" }`
- **Error Response**:
  - Code: 400
  - Content: `{ message: "Name and email are required" }`

### Update a User
- **URL**: `/api/users/:id`
- **Method**: `PUT`
- **URL Params**: `id=[integer]`
- **Body**: `{ "name": "Updated Name" }`
- **Success Response**:
  - Code: 200
  - Content: `{ id: 1, name: "Updated Name", email: "john@example.com" }`
- **Error Response**:
  - Code: 404
  - Content: `{ message: "User not found" }`
  - Code: 400
  - Content: `{ message: "At least one field (name or email) must be provided" }`

### Delete a User
- **URL**: `/api/users/:id`
- **Method**: `DELETE`
- **URL Params**: `id=[integer]`
- **Success Response**:
  - Code: 204
- **Error Response**:
  - Code: 404
  - Content: `{ message: "User not found" }`

## Error Handling

- **Validation errors** return `400 Bad Request` with a descriptive message.
- **Resource not found** errors return `404 Not Found` with a descriptive message.
