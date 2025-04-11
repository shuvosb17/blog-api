# Blog API

A simple but powerful Blog API built with Go, featuring CRUD operations and modern Go practices including concurrency patterns.

## Features

- CRUD operations for blog posts
- Concurrent request handling
- Middleware for logging and request timing
- RESTful API design
- Graceful shutdown
- In-memory storage with thread-safe operations

## API Endpoints

- `POST /api/v1/posts` - Create a new blog post
- `GET /api/v1/posts` - Get all blog posts
- `GET /api/v1/posts/:id` - Get a specific blog post
- `PUT /api/v1/posts/:id` - Update a blog post
- `DELETE /api/v1/posts/:id` - Delete a blog post

## Getting Started

### Prerequisites

- Go 1.16 or higher

### Installation

1. Clone the repository
2. Install dependencies:
   ```bash
   go mod tidy
   ```

### Running the Server

```bash
go run cmd/server/main.go
```

The server will start on `http://localhost:3000`

## API Usage Examples

### Create a Post
```bash
curl -X POST http://localhost:3000/api/v1/posts \
  -H "Content-Type: application/json" \
  -d '{"title":"My First Post","content":"Hello, World!","author":"John Doe"}'
```

### Get All Posts
```bash
curl http://localhost:3000/api/v1/posts
```

### Get a Specific Post
```bash
curl http://localhost:3000/api/v1/posts/{post-id}
```

### Update a Post
```bash
curl -X PUT http://localhost:3000/api/v1/posts/{post-id} \
  -H "Content-Type: application/json" \
  -d '{"title":"Updated Title","content":"Updated content"}'
```

### Delete a Post
```bash
curl -X DELETE http://localhost:3000/api/v1/posts/{post-id}
```

## Project Structure

```
blog-api/
├── cmd/
│   └── server/
│       └── main.go
├── internal/
│   ├── handlers/
│   │   └── post.go
│   ├── middleware/
│   │   └── logger.go
│   └── models/
│       └── post.go
├── go.mod
└── README.md
```

## Implementation Details

- Uses Fiber framework for HTTP routing
- Implements concurrent request handling using goroutines and channels
- Thread-safe operations using mutex for data access
- Structured logging middleware with request timing
- Graceful shutdown handling 
