#Calculator Microservice

A simple Node.js and Express-based calculator microservice supporting basic arithmetic operations, with robust logging using Winston and containerization via Docker and Docker Compose.

---

##Features

- Addition, Subtraction, Multiplication, Division
- Exponentiation (Power)
- Square Root
- Modulo Operation
- Error handling with HTTP status codes
- Winston logging (Console & File-based logs)
- Dockerized & Docker Compose-ready
- Health check endpoint for container stability

---

## API Endpoints

All operations accept query parameters (`num1` and `num2`) via HTTP GET requests:

| Endpoint      | Description                         | Example                                 |
|---------------|-------------------------------------|-----------------------------------------|
| `/add`        | Add two numbers                     | `/add?num1=5&num2=3`                     |
| `/subtract`   | Subtract second number from first   | `/subtract?num1=10&num2=4`              |
| `/multiply`   | Multiply two numbers                | `/multiply?num1=6&num2=7`               |
| `/divide`     | Divide first number by second       | `/divide?num1=20&num2=5`                |
| `/power`      | Exponentiation (num1 ^ num2)        | `/power?num1=2&num2=4`                  |
| `/sqrt`       | Square root of a number             | `/sqrt?num1=16`                         |
| `/modulo`     | Modulo (num1 % num2)                | `/modulo?num1=10&num2=3`                |

---

## Error Handling

- Returns `400 Bad Request` for invalid or missing parameters.
- Division by zero and square root of negative numbers are handled gracefully.

---

##Logging

Logs are handled by **Winston** and stored in the `logs/` directory:

- `error.log`: Logs errors
- `combined.log`: Logs all activity
- Console logging with simplified format

---

## Docker Usage

### Prerequisites

- Docker
- Docker Compose

### Build and Run with Docker Compose

```bash
docker-compose up --build
