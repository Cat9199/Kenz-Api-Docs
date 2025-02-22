# Auth API Documentation

## 1. Register
### Endpoint
```
POST /api/register
```
### Description
Creates a new user account.

### Request Parameters
| Parameter     | Type   | Required | Description |
|--------------|--------|----------|-------------|
| username     | string | Yes      | Unique username |
| name         | string | Yes      | Full name of the user |
| country_code | string | Yes      | Country code of the user |
| email        | string | Yes      | Unique email address |
| password     | string | Yes      | Password with a minimum length of 8 characters |
| phone_number | string | No       | User's phone number |
| fcm_token    | string | No       | Firebase Cloud Messaging token |

### Response
- **201 Created**: User successfully registered.
- **422 Unprocessable Entity**: Validation errors with failure messages.

---

## 2. Login
### Endpoint
```
POST /api/login
```
### Description
Authenticates a user and returns an access token.

### Request Parameters
| Parameter  | Type   | Required | Description |
|-----------|--------|----------|-------------|
| login     | string | Yes      | Email or username of the user |
| password  | string | Yes      | User's password |
| fcm_token | string | No       | Firebase Cloud Messaging token |

### Response
- **200 OK**: Successful authentication with user details and token.
- **422 Unprocessable Entity**: User not found.
- **401 Unauthorized**: Incorrect password.

---

## 3. Update FCM Token
### Endpoint
```
POST /api/update-fcm-token
```
### Description
Updates the FCM (Firebase Cloud Messaging) token for push notifications.

### Request Parameters
| Parameter  | Type   | Required | Description |
|-----------|--------|----------|-------------|
| fcm_token | string | Yes      | New FCM token to be updated |

### Response
- **200 OK**: Token successfully updated.
- **422 Unprocessable Entity**: Validation error with failure messages.

