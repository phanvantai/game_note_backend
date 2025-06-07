# Game Note Backend

A Go REST API backend for the Game Note Flutter application.

## Quick Start

### Prerequisites

- Go 1.19 or higher
- Git

### Installation

    1. Clone and navigate to the backend directory:

    ```bash
    cd game_note_backend
    ```

    2. Install dependencies:

    ```bash
    go mod tidy
    ```

    3. Run the server:

    ```bash
    go run main.go
    ```

    The server will start on port 8080 by default.

### API Endpoints

- `GET /health` - Health check endpoint
- `GET /hello` - Test endpoint returning a hello message

### Environment Variables

- `PORT` - Server port (default: 8080)

### Testing

Test the endpoints:

    ```bash
    # Health check
    curl http://localhost:8080/health

    # Hello endpoint
    curl http://localhost:8080/hello
    ```

## Development

### Project Structure

    ```bash
    game_note_backend/
    ├── main.go          # Main server file
    ├── go.mod           # Go module file
    ├── go.sum           # Go dependencies checksum
    └── README.md        # This file
    ```

### Next Steps

- [ ] Add PostgreSQL database connection
- [ ] Implement Firebase Auth validation
- [ ] Add user management endpoints
- [ ] Add tournament management endpoints
- [ ] Add real-time features with WebSockets
