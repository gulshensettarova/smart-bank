# 💳 Mini Bank System — Spring Boot Version

## 📌 Project Overview
The goal of this project is to build a console- or REST-based *Mini Bank System* that simulates basic banking operations. The system will support both *user* and *admin* roles and be implemented using *Spring Boot*, following clean code principles and OOP best practices.

---

## 🧑‍💼 Functional Requirements

### 👤 User Operations
- *Register* — Create a new user account
- *Login* — Authenticate using email and password
- *Change Password* — Update password using the old one
- *Create Account* — Create multiple accounts (SAVINGS/CHECKING)
- *Deposit* — Add funds to a selected account
- *Withdraw* — Withdraw funds (balance must be sufficient)
- *Transfer* — Transfer money to another account
- *View Transaction History* — List operations for a specific account
- *Logout* — Sign out of the system

### 🛠️ Admin Operations
- *View All Users* — List all users and their status
- *Activate/Deactivate User* — Toggle user status between ACTIVE and INACTIVE
- *View User Accounts* — View all accounts for a selected user
- *View System Statistics* — 
  - Total number of users
  - Number of active users
  - Total account balances
  - Total number of operations (grouped by type)

---

## ⚙️ Technical Requirements

### 🏗️ Architecture
- *Spring Boot*
- Layered architecture: Controller → Service → Repository → Entity
- RESTful API endpoints
- DTOs for request and response handling
- Input validation using javax.validation
- Exception handling using @ControllerAdvice

### 🧱 Entities
- User: contains personal info, status, and linked accounts
- Account: contains balance, account type, linked to a user
- Operation: records transaction details linked to an account

### 🔐 Enums
- AccountType: SAVINGS, CHECKING
- OperationType: DEPOSIT, WITHDRAWAL, TRANSFER
- UserStatus: ACTIVE, INACTIVE

### ❗ Custom Exceptions
- UserAlreadyExistsException
- InvalidCredentialsException
- UserBlockedException
- UserNotFoundException
- InsufficientBalanceException


## 🔐 Security

The application should implement basic security features using *Spring Security*. Users and Admins must have separate access levels.

### Authentication & Authorization
- Use *JWT-based authentication* (preferred) or *Session-based login*
- Protect endpoints using role-based access control:
  - ROLE_USER for regular users
  - ROLE_ADMIN for administrative access

## 🧪 Testing

Testing is a critical part of the Mini Bank System. It ensures code quality, catches regressions, and helps maintain reliability during feature extensions.

### 🧰 Tools & Frameworks

| Tool         | Purpose                       |
|--------------|-------------------------------|
| JUnit 5      | Unit & integration testing     |
| Mockito      | Mocking dependencies           |
| Spring Boot Test | Context loading & web-layer testing |
| Testcontainers (optional) | Running tests with real DB containers (e.g., PostgreSQL) |

---

### 🧪 Test Types

#### ✅ Unit Tests
- Focus on testing *individual methods and classes* (especially service layer)
- Use *Mockito* to mock dependencies (e.g., repositories)
- Fast and isolated from the full Spring context


#### ✅ Controller (Web) Tests
- Use @WebMvcTest to test controller layer only
- Mock services and validate HTTP request/response behavior

#### ✅ Validation Tests
- Ensure that DTO constraints (@NotBlank, @Email, etc.) trigger expected errors
- Write tests for failed validation scenarios

---

### 📊 Coverage Goals

| Layer         | Minimum Coverage |
|---------------|------------------|
| Service Layer | 90%              |
| Controller    | 80%              |
| Repository    | Optional         |
| Overall       | *≥ 80%*        |

Use tools like *JaCoCo* or *IntelliJ Coverage* to measure test coverage.
