# Chat API Documentation

## 1. Delete Chat
### Endpoint
```
DELETE /api/chat/{id}
```
### Description
Deletes a chat if the authenticated user is a participant in it.

### Request Parameters
| Parameter | Type   | Required | Description |
|-----------|--------|----------|-------------|
| id        | int    | Yes      | The ID of the chat to be deleted |

### Response
- **200 OK**: Chat successfully deleted.
- **403 Forbidden**: User is not authorized to delete this chat.
- **404 Not Found**: Chat does not exist.

---

## 2. Report Chat
### Endpoint
```
POST /api/chat/{id}/report
```
### Description
Allows a user to report a chat for inappropriate behavior or other reasons.

### Request Parameters
| Parameter | Type   | Required | Description |
|-----------|--------|----------|-------------|
| id        | int    | Yes      | The ID of the chat being reported |
| reason    | string | Yes      | The reason for reporting the chat |

### Response
- **200 OK**: Chat successfully reported.
- **403 Forbidden**: User is not authorized to report this chat.
- **404 Not Found**: Chat does not exist.
- **422 Unprocessable Entity**: Validation error with failure messages.

