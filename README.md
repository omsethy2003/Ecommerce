
# Sb-ecom: E-commerce Backend Application 🛍️

## Table of Contents
- [About the Project](#about-the-project)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Error Handling](#error-handling)
- [Project Structure](#project-structure)
- [Initial Data Setup](#initial-data-setup)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## About the Project
Sb-ecom is a robust and scalable e-commerce backend application built with Spring Boot. It provides a comprehensive set of APIs to manage users, products, orders, categories, carts, and payments. Designed with a clean architecture, secure JWT-based authentication, and efficient data handling with MySQL.

## Features
- **User Management**: Registration, login, RBAC, and profile management.
- **Product Catalog**: CRUD for products and associations with categories.
- **Category Management**: Full CRUD support.
- **Shopping Cart**: Add, update, and remove items.
- **Order Management**: Place orders and view/manage statuses.
- **Payment Integration**: Stripe support for secure payments.
- **Address Management**: Multiple shipping addresses per user.
- **Error Handling**: Centralized with detailed messages.
- **Security**: JWT, BCrypt, role-based access, and CORS.
- **Data Mapping**: ModelMapper integration.
- **Initial Setup**: Auto-creates roles and default users with roles.

## Technologies Used
- **Backend**: Java 21, Spring Boot 3.5.0, Spring Web, Spring Security, Spring Data JPA, Lombok, ModelMapper, Jackson
- **Database**: MySQL, MySQL Connector/J
- **Security**: JWT (jjwt 0.12.6), Spring Security Test
- **Payment**: Stripe Java Library 29.0.0
- **Build Tool**: Maven

## Getting Started

### Prerequisites
- JDK 21+
- Maven 3.x+
- MySQL instance
- Stripe account

### Installation
```bash
git clone https://github.com/your-username/sb-ecom.git
cd sb-ecom
```

Update `src/main/resources/application.properties` with your local configuration:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce
spring.datasource.username=root
spring.datasource.password=your_password
spring.app.jwtSecret=your_jwt_secret
stripe.secret.key=${STRIPE_SECRET_KEY}
```

### Build
```bash
mvn clean install
```

## Running the Application
```bash
mvn spring-boot:run
```

Or run `SbEComApplication.java` from your IDE.

Access the backend at: `http://localhost:8080`

## API Endpoints
Extensive RESTful API support covering:

- **Auth**: `/api/auth/signin`, `/signup`, `/signout`, `/user`
- **Addresses**: `/api/addresses`, `/api/users/addresses`
- **Cart**: `/api/carts`, `/api/cart/products/{productId}`
- **Categories**: `/api/public/categories`, `/api/admin/categories`
- **Orders**: `/api/order`, `/api/order/stripe-client-secret`
- **Products**: `/api/public/products`, `/api/admin/products`
(Full descriptions and payloads in source)

## Error Handling
Centralized in `MyGlobalExceptionHandler` for:
- `MethodArgumentNotValidException` → 400
- `ResourceNotFoundException` → 404
- `APIException` → 400
- `AuthEntryPointJwt` → 401 with structured JSON

## Project Structure
Follows layered architecture:
```
sb-ecom/
├── config/
├── controller/
├── exceptions/
├── model/
├── payload/
├── repositories/
├── security/
├── service/
├── util/
└── resources/
```

## Initial Data Setup
At startup:
- Creates roles: `ROLE_USER`, `ROLE_SELLER`, `ROLE_ADMIN`
- Creates default users: 
  - `user1/password1`
  - `seller1/password2`
  - `admin/adminPass` (with all roles)

## Contributing
1. Fork the repo
2. Create your feature branch: `git checkout -b feature/AmazingFeature`
3. Commit: `git commit -m 'Add some AmazingFeature'`
4. Push: `git push origin feature/AmazingFeature`
5. Open a Pull Request

## License
Distributed under the MIT License.

## Contact
Your Name - [your_email@example.com](mailto:your_email@example.com)  
Project Link: [https://github.com/your-username/sb-ecom](https://github.com/your-username/sb-ecom)
