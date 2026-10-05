# B) API Reference Entry

## Create a New Task

**Method:** `POST`

**Endpoint:**

```text
/api/v1/projects/{projectId}/tasks
```

### Description

This endpoint allows an authenticated user to create a new task inside a specific project.

The task must have a title, assignee, due date, and priority. The description is optional.

### Authentication

The endpoint requires a valid authentication token.

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```## Request Parameters

### Path Parameter

| Name | Data Type | Required | Description |
|---|---|---|---|
| `projectId` | String | Yes | The unique ID of the project where the new task will be created. |

### Request Body Parameters

| Name | Data Type | Required | Description |
|---|---|---|---|
| `title` | String | Yes | The name or title of the task. |
| `description` | String | No | A detailed explanation of the task. |
| `assigneeId` | String | Yes | The unique ID of the user assigned to the task. |
| `dueDate` | String (ISO 8601 date) | Yes | The date when the task is due. |
| `priority` | String | Yes | The priority of the task. Allowed values are `low`, `medium`, or `high`. |

### Required Request Headers

| Header | Required | Description |
|---|---|---|
| `Authorization` | Yes | Contains the user's Bearer authentication token. |
| `Content-Type` | Yes | Must be `application/json` because the request body is JSON. |## HTTP Response Codes

| HTTP Status Code | Meaning | When It Occurs |
|---|---|---|
| `201 Created` | Task created successfully. | The task was successfully created and saved in the project. |
| `400 Bad Request` | Invalid request. | One or more required fields are missing or contain invalid data. |
| `401 Unauthorized` | Authentication required or invalid. | The access token is missing, expired, or invalid. |
| `403 Forbidden` | Access denied. | The authenticated user does not have permission to create a task in the project. |
| `404 Not Found` | Project or user not found. | The specified project ID or assignee ID does not exist. |
| `409 Conflict` | Request conflicts with existing data. | The task cannot be created because it conflicts with the current project data. |
| `422 Unprocessable Entity` | Validation failed. | The request format is valid, but one or more values fail business validation. |
| `500 Internal Server Error` | Server error. | An unexpected error occurs on the server while processing the request. |## Example Request

### Request

```http
POST /api/v1/projects/proj_1001/tasks
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9
Content-Type: application/json
```

### Request Body

```json
{
  "title": "Complete project documentation",
  "description": "Write and review the technical documentation for the project.",
  "assigneeId": "user_205",
  "dueDate": "2026-10-15",
  "priority": "high"
}
```

In this example, the task is created in project `proj_1001` and assigned to user `user_205`.## Example Successful Response

### HTTP Response

```http
HTTP/1.1 201 Created
Content-Type: application/json
```

### Response Body

```json
{
  "success": true,
  "message": "Task created successfully",
  "data": {
    "id": "task_5001",
    "projectId": "proj_1001",
    "title": "Complete project documentation",
    "description": "Write and review the technical documentation for the project.",
    "assigneeId": "user_205",
    "dueDate": "2026-10-15",
    "priority": "high",
    "status": "pending",
    "createdAt": "2026-10-05T11:30:00Z"
  }
}
```

### Response Field Description

| Field | Data Type | Description |
|---|---|---|
| `success` | Boolean | Indicates whether the request was successful. |
| `message` | String | Provides a description of the result. |
| `id` | String | Unique ID of the newly created task. |
| `projectId` | String | ID of the project containing the task. |
| `title` | String | Title of the task. |
| `description` | String | Description of the task. |
| `assigneeId` | String | ID of the user assigned to the task. |
| `dueDate` | String | Date by which the task should be completed. |
| `priority` | String | Task priority: `low`, `medium`, or `high`. |
| `status` | String | Current task status. |
| `createdAt` | String | Date and time when the task was created. |