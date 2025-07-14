# Sb-ecom: E-commerce Backend Application

## Table of Contents
- [About the Project](#about-the-project)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [API Endpoints](#api-endpoints)
  - [Authentication & Authorization](#authentication--authorization)
  - [Address Management](#address-management)
  - [Cart Management](#cart-management)
  - [Category Management](#category-management)
  - [Order Management](#order-management)
  - [Product Management](#product-management)
- [Error Handling](#error-handling)
- [Project Structure](#project-structure)


## About the Project
Sb-ecom is a robust and scalable **e-commerce backend application** built with Spring Boot. It provides a comprehensive set of APIs to manage users, products, orders, categories, carts, and payments, enabling the foundation for a complete e-commerce platform. This project focuses on a clean architecture, secure authentication using JWT, and efficient data handling with MySQL.

The application is designed to be the backbone for a modern e-commerce website, handling all server-side logic and data persistence.

## Features
This application offers a wide range of functionalities to support a modern e-commerce system:

### User Management:
- User registration and login using JWT for secure authentication
- Role-based access control (RBAC) with ROLE_USER, ROLE_SELLER, and ROLE_ADMIN roles
- User profile management
- **Authentication Utilities:** AuthUtil provides convenient methods to retrieve details of the currently logged-in user (email, ID, or the full User object) from the Spring Security context

### Product Catalog:
- CRUD operations (Create, Retrieve, Update, Delete) for products
- Products are associated with categories

### Category Management:
- CRUD operations for product categories

### Shopping Cart:
- Add, update quantity, and remove items from a user's shopping cart
- View detailed cart contents

### Order Management:
- Place new orders from the shopping cart
- View order history for authenticated users
- Manage order status (e.g., pending, shipped, delivered) by administrators

### Payment Integration:
- Secure payment processing using Stripe API

### Address Management:
- Allows users to manage multiple shipping addresses

### Robust Error Handling:
- Centralized exception handling via MyGlobalExceptionHandler to provide consistent and informative error responses

### Security:
- JSON Web Token (JWT) based authentication and authorization using jjwt library
- Password encoding using BCryptPasswordEncoder
- Configured CORS to allow requests from specified frontend URLs

### Data Mapping:
- Uses ModelMapper for efficient object-to-object mapping (e.g., between entities and DTOs)

### Initial Data Setup:
- CommandLineRunner to automatically create default roles and initial users upon application startup

## Technologies Used

### Core Stack
| Technology | Purpose |
|------------|---------|
| Java 21 | Core programming language |
| Spring Boot 3.5.0 | Application framework |
| Spring Data JPA | Database interactions |
| Spring Security | Authentication & authorization |
| MySQL | Relational database |

### Key Libraries
| Library | Usage |
|---------|-------|
| Lombok | Reduce boilerplate code |
| ModelMapper 3.0.0 | Object mapping |
| JJWT 0.12.6 | JWT implementation |
| Stripe Java 29.0.0 | Payment processing |

### Development Tools
| Tool | Purpose |
|------|---------|
| Maven | Dependency management |
| MySQL Connector/J | Database connectivity |
| Jackson Databind | JSON processing |

### Database:
- MySQL
- MySQL Connector/J

### Security:
- JJWT (io.jsonwebtoken)
- Spring Security Test

### Payment Gateway:
- Stripe Java Library 29.0.0

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





