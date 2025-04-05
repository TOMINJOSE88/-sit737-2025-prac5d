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

docker-compose up --build


##Deploying to Google Cloud
Push the image to Google Cloud Artifact Registry:

If you've made any changes locally, follow these steps to push the image to the cloud:

docker build -t calculator-web .
docker tag calculator-web australia-southeast2-docker.pkg.dev/sit737-25t1-jose-e4e07b7/calculator/calculator-microservice:v2
docker push australia-southeast2-docker.pkg.dev/sit737-25t1-jose-e4e07b7/calculator/calculator-microservice:v2
Deploy the image to Google Cloud Run:

##To deploy the updated image to Google Cloud Run:

gcloud run deploy calculator-service --image=australia-southeast2-docker.pkg.dev/sit737-25t1-jose-e4e07b7/calculator/calculator-microservice:v2 --platform=managed --region=australia-southeast2 --allow-unauthenticated
This will make your service available in the cloud.

Testing the Service
Once the container is running, you can test the API endpoints using:

Addition: /add?num1=10&num2=5

Subtraction: /subtract?num1=10&num2=4

Multiplication: /multiply?num1=6&num2=7

Division: /divide?num1=20&num2=5

Exponentiation: /power?num1=2&num2=4

Square Root: /sqrt?num1=16

Modulo: /modulo?num1=10&num2=3


##Pull and Run the Docker Image from the Cloud
Pull the Docker image from Google Cloud Artifact Registry:

Pull the image that was previously pushed to Google Cloud Artifact Registry:

docker pull australia-southeast2-docker.pkg.dev/sit737-25t1-jose-e4e07b7/calculator/calculator-microservice:v2
This will download the image with the latest changes from the cloud to your local machine.

Run the container:

After pulling the image, run it locally with Docker, mapping port 8082 on your local machine to port 8080 inside the container:

docker run -p 8082:8080 australia-southeast2-docker.pkg.dev/sit737-25t1-jose-e4e07b7/calculator/calculator-microservice:v2
This will make the microservice available at http://localhost:8082.