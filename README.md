
### HNG Boilerplate stage 3   Documentation

## Overview
This is the API documentation for the NodeNinja Team HNG Boilerplate API. You can use this API to manage users, organizations, emails, payments, and settings.


## Database Design
Here’s the database schema used in the project:

![Database Schema](file:///mnt/data/WhatsApp%20Image%202024-07-13%20at%2007.20.04.jpeg)

### Users Table
- `id` (int, primary key)
- `username` (varchar)
- `email` (varchar)
- `password` (varchar)
- `first_name` (varchar)
- `last_name` (varchar)
- `created_at` (timestamp)

### Organizations Table
- `id` (int, primary key)
- `name` (varchar)
- `created_at` (timestamp)

### Organization_Users Table
- `organization_id` (int, foreign key)
- `user_id` (int, foreign key)
- `role` (varchar)

### Emails Table
- `id` (int, primary key)
- `recipient` (varchar)
- `subject` (varchar)
- `body` (text)
- `sent_at` (timestamp)

### Payments Table
- `id` (int, primary key)
- `user_id` (int, foreign key)
- `organization_id` (int, foreign key)
- `amount` (decimal)
- `currency` (varchar)
- `status` (varchar)
- `created_at` (timestamp)

### Settings Table
- `user_id` (int, foreign key)
- `settings_key` (varchar)
- `settings_value` (varchar)

### Notifications Table
- `id` (int, primary key)
- `user_id` (int, foreign key)
- `message` (text)
- `is_read` (boolean)
- `created_at` (timestamp)

### Activity_Log Table
- `id` (int, primary key)
- `user_id` (int, foreign key)
- `action` (varchar)
- `timestamp` (timestamp)

### Invites Table
- `id` (int, primary key)
- `user_id` (int, foreign key)
- `invite_code` (varchar)
- `created_at` (timestamp)
- `expires_at` (timestamp)

### Random_Data Table
- `id` (int, primary key)
- `user_id` (int, foreign key)
- `data` (json)
- `created_at` (timestamp)

### Waitlist Table
- `id` (int, primary key)
- `email` (varchar)
- `joined_at` (timestamp)

## API Endpoints
All API endpoints are defined in the OpenAPI specification. Here's a summary:n 

OpenApi Api design : https://app.swaggerhub.com/apis/DANIELMWIHOTI_1/Node-project/1.0.0

### User Endpoints
- **POST /api/users/register**: Register a new user
- **POST /api/users/login**: Login a user
- **GET /api/users/{userId}**: Get user profile
- **PUT /api/users/{userId}**: Update user profile

### Organization Endpoints
- **POST /api/organizations**: Create a new organization
- **GET /api/organizations/{organizationId}**: Get organization details
- **POST /api/organizations/{organizationId}/users**: Add a user to an organization

### Email Endpoints
- **POST /api/emails/send**: Send an email

### Payment Endpoints
- **POST /api/payments**: Create a payment
- **GET /api/payments/{paymentId}**: Get payment details

### Settings Endpoints
- **GET /api/settings/{userId}**: Get user settings

## Scripts
Here are some useful npm scripts that you can use during development and production:
- `npm run build`: Compiles the TypeScript code to JavaScript.
- `npm run start:dev`: Starts the development server with live reloading.
- `npm run start`: Starts the production server.
- `npm run test`: Runs the test suite (if available).
- `npm run lint`: Runs the linter to check for code style issues.

## Additional Resources
- [Node.js Documentation](https://nodejs.org/en/docs/)
- [TypeScript Documentation](https://www.typescriptlang.org/docs/)
- [Express Documentation](https://expressjs.com/)

By following these steps, you should have your Node.js and TypeScript application up and running. If you encounter any issues, please refer to the documentation of the respective tools or seek help from the community.

## Versioning
This project is versioned to ensure backward compatibility and easy maintenance. The current version is 1.0.0.

