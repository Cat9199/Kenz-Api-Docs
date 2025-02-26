# Chat-Kenz WebSocket API Documentation

## Overview
Chat-Kenz provides a **WebSocket API** for real-time chat functionality. This document guides mobile developers on how to connect, authenticate, send, and receive messages via WebSockets.

## WebSocket Server
- **URL:** `wss://chat-kenz.rascoda.com`
- **Protocol:** WebSocket
- **Authentication:** JWT Token in `auth` payload

## Connecting to WebSocket
To connect, use the WebSocket client in your mobile application.

### **Example (JavaScript - React Native)**
```javascript
import io from 'socket.io-client';

const socket = io('wss://chat-kenz.rascoda.com', {
  auth: {
    token: 'YOUR_JWT_TOKEN'
  }
});

socket.on('connect', () => {
  console.log('Connected to Chat-Kenz WebSocket');
});

socket.on('connect_error', (err) => {
  console.error('Connection Error:', err.message);
});
```

## Authentication
- The WebSocket requires a **JWT token** for authentication.
- The token must be passed in the `auth` object when initializing the connection.
- If authentication fails, the connection will be rejected.

## Sending Messages
To send a message, emit a `send_message` event with the following data:

### **Payload Structure**
```json
{
  "chatId": 123,
  "message": "Hello, how are you?",
  "type": "text",
  "file_url": null
}
```

### **Example (JavaScript - React Native)**
```javascript
socket.emit('send_message', {
  chatId: 123,
  message: 'Hello, how are you?',
  type: 'text',
  file_url: null
});
```

## Receiving Messages
Listen for the `receive_message` event to get new messages in real time.

### **Example**
```javascript
socket.on('receive_message', (data) => {
  console.log('New message received:', data);
});
```

### **Response Format**
```json
{
  "id": 456,
  "chat_id": 123,
  "sender_id": 1,
  "message": "Hello, how are you?",
  "type": "text",
  "file_url": null,
  "created_at": "2025-02-26T10:00:00Z"
}
```

## Handling Disconnection
Handle unexpected disconnections and attempt to reconnect.
```javascript
socket.on('disconnect', () => {
  console.log('Disconnected from server');
});
```

## Error Handling
Listen for errors from the server.
```javascript
socket.on('error', (errorMessage) => {
  console.error('Server Error:', errorMessage);
});
```

## Notes
- Always ensure a valid JWT token is provided.
- Reconnect on disconnections to maintain a smooth chat experience.
- Use proper error handling for a seamless user experience.

## Contact
For any issues, contact the backend team at `support@rascoda.com`.

---
This documentation helps mobile developers integrate Chat-Kenz WebSocket efficiently.

