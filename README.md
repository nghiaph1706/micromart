
# MICROMART Project

MICROMART is a multi-service e-commerce platform designed to handle authentication, user management, product catalog, orders, payments, and notifications. Each service operates independently, utilizing different databases to ensure scalability and maintainability.

## Docker Compose Configuration

The following services are defined in the Docker Compose configuration:

### 1. Authentication Service
- **Auth Database (PostgreSQL)**
  - Database: `auth_db`
  - User: `auth_admin`
  - Password: `auth_pass123`
  - Port: `5432`

- **Auth Service (Node.js)**
  - Runs on port `3000`
  - Connects to the `auth-db` for authentication and user-related tasks.
  - Uses JWT and middleware for secure API endpoints.

### 2. User Service
- **User Database (MySQL)**
  - Database: `user_db`
  - User: `user_admin`
  - Password: `user_pass123`
  - Port: `3306`

- **User Service (Laravel)**
  - Runs on port `9000`
  - Connects to the `user-db` for managing user profiles, authentication, and CRUD operations.

### 3. Product Service
- **Product Database (PostgreSQL)**
  - Database: `product_db`
  - User: `product_admin`
  - Password: `product_pass123`
  - Port: `5433`

- **Product Service (Java - Spring Boot)**
  - Runs on port `8080`
  - Connects to the `product-db` for managing product catalogs, stock, and product-related tasks.

### 4. Order Service
- **Order Database (MySQL)**
  - Database: `order_db`
  - User: `order_admin`
  - Password: `order_pass123`
  - Port: `3307`

- **Order Service (Python - FastAPI/Flask)**
  - Runs on port `8000`
  - Connects to the `order-db` for managing orders, statuses, and processing order-related information.

### 5. Payment Service
- **Payment Database (PostgreSQL)**
  - Database: `payment_db`
  - User: `payment_admin`
  - Password: `payment_pass123`
  - Port: `5434`

- **Payment Service (Go)**
  - Runs on port `8081`
  - Connects to the `payment-db` for managing payment transactions, processing payments, and handling third-party integrations.

### 6. Notification Service
- **Redis for caching & message brokering**
  - Runs on port `6379`
  
- **MongoDB for storing notification data**
  - Database: `mongo`
  - User: `mongo_admin`
  - Password: `mongo_pass123`
  - Port: `27017`

- **Notification Service (C# .NET Core)**
  - Runs on port `5000`
  - Uses Redis and MongoDB to handle background jobs and push notifications.

### 7. RabbitMQ Service
- **RabbitMQ (Message Broker)**
  - Runs on port `5672` for message communication between services.
  - Management Console available on port `15672` for managing queues and exchanges.
  - Provides asynchronous messaging and decoupling between services.

  - **RabbitMQ Configuration:**
    - Default user: `guest`
    - Default password: `guest`

## Setup and Installation

### Prerequisites
- Docker and Docker Compose installed.

### Steps to Start the Project Locally
1. Clone the repository.
2. Navigate to the project directory.
3. Run the following command to start the services:

   ```bash
   docker-compose up --build
   ```

4. The services will be available at the following ports:
   - Auth Service: `http://localhost:3000`
   - User Service: `http://localhost:9000`
   - Product Service: `http://localhost:8080`
   - Order Service: `http://localhost:8000`
   - Payment Service: `http://localhost:8081`
   - Notification Service: `http://localhost:5000`
   - RabbitMQ Management Console: `http://localhost:15672`

### Running in Production Environment
For a production environment, we use a separate configuration file: `docker-compose.prod.yml`. This configuration is optimized for production, ensuring that sensitive data is properly configured and that the services are run with the correct settings for scalability and performance.

#### Steps to Start the Project in Production
1. Clone the repository.
2. Navigate to the project directory.
3. Run the following command to start the services in the production environment:

   ```bash
   docker-compose -f docker-compose.yml -f docker-compose.prod.yml up --build
   ```

This will load both the default `docker-compose.yml` and the production-specific `docker-compose.prod.yml` configuration files, setting the correct environment variables and optimizing services for production.

The services will be available at the same ports as mentioned above, but the environment will be configured for production use, with any necessary optimizations for security, performance, and scalability.

## Communication Between Services
- The services communicate asynchronously using **RabbitMQ** for message brokering. Each service can send messages to RabbitMQ queues and listen for messages to update or perform actions.
- RabbitMQ is configured to run on port `5672` (for message queues) and can be monitored via the RabbitMQ management console running on port `15672`.

## Database Configuration
Each service has its own dedicated database:
- PostgreSQL for **Auth**, **Product**, and **Payment** services.
- MySQL for **User** and **Order** services.
- Redis and MongoDB are used by the **Notification** service.

## Conclusion
MICROMART provides a robust, modular, and scalable e-commerce platform using a microservices architecture. By leveraging Docker, Docker Compose, and RabbitMQ, the system ensures efficient communication and management of different services and databases.

## Contact
Please feel free to contact me if you need any further information.
- Name: Phạm Lễ Nghĩa
- Email: [your-email@example.com](mailto:your-email@example.com)
- LinkedIn: [your-linkedin-profile](https://www.linkedin.com/in/your-profile/)