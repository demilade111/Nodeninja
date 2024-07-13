
### HNG Boilerplate stage 3   Documentation

## Overview
This is the API documentation for the HNG Boilerplate API. You can use this API to manage users, organizations, emails, payments, and settings.

## Folder Structure
```
|--- src
|    |--- controllers
|         |--- v1
|    |--- database
|    |--- interfaces
|    |--- middlewares
|    |--- routes
|         |--- v1
|    |--- services
|    |--- utils
|    |--- server.ts
|--- .env
|--- app.ts
|--- .gitignore
|--- package.json
|--- tsconfig.json
```

## Dependencies (Dev)
- Node.js
- TypeScript
- Express
- ts-node-dev
- [Other dependencies]

## Getting Started

### Prerequisites
Before you begin, ensure you have the following installed on your machine:
- Node.js (v14 or later)
- npm (Node Package Manager, included with Node.js)
- Git

### Contribution Guide

#### Getting Started
1. **Install Git**
   - If you don't have Git on your machine, [install it](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

2. **Fork this Repository**
   - Fork this repository by clicking on the fork button on the top of this page. This will create a copy of this repository in your account.

3. **Clone the Repository**
   - Clone this repository to your machine. Go to your GitHub account, open the forked repository, click on the code button, and then click the copy to clipboard icon.
   ```bash
   git clone "url you just copied"
   ```

   Example:
   ```bash
   git clone git@github.com:your-username/[app-name].git
   ```
   - Change to the repository directory on your computer:
   ```bash
   cd [app-name]
   ```

4. **Create a Branch**
   - Now create a branch using the `git switch` command:
   ```bash
   git switch -c your-new-branch-name
   ```

5. **Make Changes**
   - Make your changes to the codebase. Ensure your code follows the project's coding standards and guidelines.

6. **Run Tests**
   - Run the existing tests to ensure your changes do not break anything. If you added new functionality, write corresponding tests.
   ```bash
   npm run test
   ```

7. **Commit Changes**
   - Add your changes to the branch you just created using the `git add` command:
   ```bash
   git add .
   ```

8. **Push Changes to GitHub**
   - Push your changes using the command:
   ```bash
   git push -u origin your-branch-name
   ```

9. **Submit Your Changes for Review**
   - If you go to your repository on GitHub, you'll see a `Compare & pull request` button. Click on that button to submit the pull request.

## Setup Instructions

### 1. Clone the Repository
First, clone the repository to your local machine using Git.
```bash
git clone https://github.com/your-username/[app-name].git
cd [app-name]
```

### 2. Install Dependencies
Navigate to the project directory and install the required dependencies.
```bash
npm install
```

### 3. Configure Environment Variables
Create a `.env` file in the root directory of the project and add your environment-specific variables. You can use the provided `.env.example` file as a reference.
```bash
cp .env.example .env
```
Edit the `.env` file to match your environment configuration.

### 4. Compile TypeScript
Compile the TypeScript code to JavaScript.
```bash
npm run build
```

### 5. Run the Development Server
Start the development server with the following command. This will also watch for any changes in your code and automatically restart the server.
```bash
npm run start:dev
```

### 6. Run the Production Server
To run the application in a production environment, use the following command:
```bash
npm run start
```

### 7. Verify the Setup
Open your browser and navigate to `http://localhost:3000/api/v1/` to verify that the application is running correctly.

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
All API endpoints are defined in the OpenAPI specification. Here's a summary:

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

