
# Table Banking System

## Overview
The Table Banking System is a financial management platform designed to enable users to make regular contributions, accumulate interest on their savings, and access loans once they meet specific eligibility criteria

## Features

### Functional Features
- **User Registration:** Users can register and create an account to interact with the system.
- **Monthly Contributions:** Users are required to contribute every month. Skipping a month will make them ineligible for a loan.
- **Loan Application:** After making consecutive monthly contributions, users become eligible to apply for loans. Loans can be issued with either compound or simple interest, depending on the loan type and terms
- **Earn Interest::** Contributions accumulate interest, either simple or compound, based on the user's preferences and the system's rules. This helps users grow their savings effortlessly.
- **Loan Eligibility:** The system automatically determines the eligibility for a loan based on the user's monthly contributions and other criteria.
- **Loan Repayment:** Loans come with a repayment schedule, and users can repay them in installments, with interest starting immediately upon loan issuance.

### Technical Features
- **Spring Boot 3.x** for building the backend of the application.
- **Java 17+** for modern and efficient development.
- **Spring Data JPA** integrated with **PostgreSQL** for data persistence and query operations.
- **Lombok** used to reduce boilerplate code (such as getters, setters, constructors).
- **Spring Boot DevTools** to enable auto-restart during development, improving development speed.
- **Spring Boot Testing** using **JUnit** and **Mockito** for unit and integration testing.
- **Postman** for API testing to ensure all endpoints work as expected.

## System Requirements
- **Java 17+** (Ensure Java 17 or higher is installed)
- **PostgreSQL** (Make sure a PostgreSQL instance is running and accessible)
- **Maven**  (for building and managing dependencies)

## Setup Instructions

### 1. Clone the repository
Clone this repository to your local machine:

```bash
git clone https://github.com/malise5/table_Banking.git
```

### 2. Configure the Database
- Install and configure PostgreSQL on your local machine or use a remote database.
- Update `application.properties` or `application.yml` with your PostgreSQL database connection details:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/loan_system
spring.datasource.username=your-db-username
spring.datasource.password=your-db-password
```

### 3. Build the Project
To build the project, use the following Maven command:

```bash
mvn clean install
```

### 4. Run the Application
Run the Spring Boot application using:

```bash
mvn spring-boot:run
```

Alternatively, you can run the project directly from your IDE (e.g., IntelliJ IDEA, Eclipse).

### 5. Test the APIs
Use **Postman** to test the exposed APIs. Import the provided Postman collection or create your own tests for the following:

- **User Registration:** POST `/api/users/register`
- **Monthly Contribution:** POST `/api/contributions`
- **Loan Application:** POST `/api/loans/apply`
- **Loan Eligibility Check:** GET `/api/loans/eligibility`

## API Endpoints

### 1. **POST /api/users/register**
- Registers a new user in the system.
- **Request Body:**
  ```json
  {
    "username": "john_doe",
    "email": "john.doe@example.com",
    "password": "securepassword123",
    "full_name": "John Doe",
    "phone_number": "+1234567890",
    "address": "123 Main Street, Hometown, ABC 12345",
    "date_of_birth": "1990-05-15"
  }
  ```
- **Response:**
  - `200 OK` if successful.
  - `400 Bad Request` for invalid input.

### 2. **POST /api/contributions**
- Allows a user to make a monthly contribution.
- **Request Body:**
  ```json
  {
    "userId": 1,
    "amount": 100
  }
  ```
- **Response:**
  - `200 OK` if successful.
  - `400 Bad Request` for invalid contribution.

### 3. **POST /api/loans/apply**
- User can apply for a loan based on their contributions.
- **Request Body:**
  ```json
  {
    "userId": 1,
    "loanAmount": 5000,
    "interestType": "compound"
  }
  ```
- **Response:**
  - `200 OK` if successful.
  - `400 Bad Request` if the user is ineligible.

### 4. **GET /api/loans/eligibility**
- Checks if the user is eligible for a loan.
- **Request Params:**
  - `userId`: User's ID.
- **Response:**
  - `200 OK` with eligibility status.
  - `400 Bad Request` for invalid user ID.

## Development

### Local Development Setup
Ensure you have the following tools installed:
- **Java 17+**
- **PostgreSQL**
- **Maven** or **Gradle**
- **IDE (Optional)**: IntelliJ IDEA, Eclipse, or VSCode

### Running Tests
To run unit tests, use the following Maven command:

```bash
mvn test
```

### Testing APIs
Use **Postman** to send requests to the endpoints described above.

## Technologies Used
- **Spring Boot 3.x**
- **Java 17+**
- **Spring Data JPA**
- **PostgreSQL**
- **Lombok**
- **JUnit & Mockito** (for testing)
- **Postman** (for API testing)

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
