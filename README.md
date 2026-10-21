# Real-Time Chat Application

A real-time chat application built using **Java, Spring Boot, WebSocket, STOMP, SockJS, and Bootstrap**. Users can enter their name and exchange messages instantly through a shared chat room.

## Features

- Real-time messaging between connected users
- WebSocket communication using STOMP and SockJS
- Shared chat room for multiple users
- Dynamic message rendering without refreshing the page
- Automatic scrolling to the latest message
- Responsive user interface using Bootstrap 5
- Spring Boot backend with message broker configuration

## Tech Stack

| Technology | Purpose |
|---|---|
| Java | Backend programming |
| Spring Boot | Backend application |
| Spring WebSocket | Real-time communication |
| STOMP | Messaging protocol |
| SockJS | WebSocket fallback support |
| HTML5 | Application structure |
| CSS / Bootstrap 5 | User interface |
| JavaScript | Client-side messaging |
| Maven | Dependency management and build |

## Project Architecture

The application uses a client-server architecture.

1. The browser establishes a connection to the `/chat` endpoint.
2. The client subscribes to `/topic/messages`.
3. A user sends a message to `/app/sendMessage`.
4. Spring Boot processes the message through a STOMP message handler.
5. The backend broadcasts the message to `/topic/messages`.
6. All subscribed clients receive and display the message.

## Prerequisites

Make sure you have installed:

- Java 21 or the Java version configured in your project
- Maven, or the Maven Wrapper included with the project
- Git
- A web browser

## Getting Started

### 1. Clone the repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

Replace `YOUR_GITHUB_REPOSITORY_URL` with your actual repository URL.

### 2. Navigate to the project directory

```bash
cd your-project-folder
```

### 3. Run the application

Using Maven:

```bash
mvn spring-boot:run
```

Alternatively, if your project includes the Maven Wrapper:

**Windows**

```bash
mvnw.cmd spring-boot:run
```

**Linux / macOS**

```bash
./mvnw spring-boot:run
```

### 4. Open the application

Visit:

```text
http://localhost:8080
```

If your application uses a different port, open the corresponding local URL.

## WebSocket Configuration

The application uses the following STOMP destinations:

| Destination | Purpose |
|---|---|
| `/chat` | SockJS connection endpoint |
| `/app` | Prefix for application-bound messages |
| `/topic/messages` | Destination for broadcasting chat messages |

Example client-side message:

```javascript
stompClient.send(
    "/app/sendMessage",
    {},
    JSON.stringify({
        sender: "Deepak",
        content: "Hello everyone!"
    })
);
```

The backend must provide a matching message handler and broadcast the processed message to `/topic/messages`.

## Current Limitations

- Messages are not persisted in a database in the current in-memory broker setup.
- Messages sent before a user connects are not automatically available to that user.
- Authentication and authorization are not implemented in the current basic version.
- The simple message broker is intended for basic applications and learning; larger deployments may require a dedicated message broker.

## Future Improvements

- User authentication and authorization
- Private messaging between users
- Chat room creation and management
- Message history using PostgreSQL
- Online user indicators
- Message timestamps
- Docker-based deployment
- Production deployment with HTTPS and secure WebSocket communication

## Learning Outcomes

This project demonstrates practical experience with:

- Building a Java backend using Spring Boot
- Configuring WebSocket endpoints
- Understanding STOMP messaging and message brokers
- Connecting a JavaScript frontend to a backend
- Handling real-time events
- Using Git and GitHub for version control

## Author

**Deepak Bisht**


---

*This project was built as a hands-on learning project to understand real-time communication and backend development using Java and Spring Boot.*
