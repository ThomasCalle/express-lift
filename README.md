# Express Lift - Forklift Repair Services, Sales & Rentals Web Application

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Description

This repository contains the code and documentation for a web application created to streamline work order management, customer tracking, and invoicing for a forklift maintenance business. The application is designed to enhance operational efficiency by enabling centralized management of customer data and integration with QuickBooks.

---

## Table of Contents

- [Overview](#overview)
- [Project Goals](#project-goals)
- [Assigned User Story](#assigned-user-story)
- [Acceptance Criteria](#acceptance-criteria)
- [Tech Stack & Versioning](#tech-stack-versioning)
- [Database Setup](#database-setup)
  - [PostgreSQL](#postgresql)
  - [MySQL](#mysql)
- [Hosting Options](#hosting-options)
  - [AWS](#aws)
  - [Heroku](#heroku)
- [Error Handling and Troubleshooting](#error-handling-and-troubleshooting)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Development Guidelines](#development-guidelines)
- [Milestones](#milestones)
- [MVP (Minimum Viable Product)](#mvp-minimum-viable-product)
- [Usage Instructions](#usage-instructions)
- [License](#license)
- [Author](#author)
- [Acknowledgments](#acknowledgments)

---

## Overview

This project aims to build a functional, scalable, and secure web application tailored to the needs of a forklift maintenance business. The application will allow users to create and manage work orders, track customer information, and generate invoices that can be exported directly to QuickBooks for seamless accounting.

---

## Project Goals

- **Enhance Operational Efficiency**: Centralize work order creation and management, reducing time and minimizing errors.
- **Customer and Equipment Management**: Store and retrieve customer profiles and equipment details to improve service response times.
- **Simplified Invoicing**: Generate invoices that integrate with QuickBooks, automating financial processes and making it easier to track revenue.

---

## Assigned User Story

```
AS A forklift maintenance business owner
I NEED a comprehensive, centralized system to manage work orders, track customer and equipment data, and streamline invoicing
SO THAT I can improve operational efficiency, reduce manual errors, and elevate the overall quality of service delivery.
```

---

## Acceptance Criteria

```
GIVEN a robust, centralized work order management system,
WHEN an employee or administrator logs in,
THEN they are granted role-specific access to create, modify, and manage work orders and to view associated customer and equipment information as per their permissions.
WHEN an invoice is generated,
THEN the system provides seamless export functionality, integrating with QuickBooks for accurate and efficient accounting.
WHEN the system is accessed by an authorized user,
THEN it enforces SSL encryption to safeguard all sensitive data transfers, ensuring secure and compliant communication.
WHEN a system error or data input discrepancy arises,
THEN the user is provided with clear, actionable notifications to facilitate swift corrective measures and maintain data integrity.
```
---

## Tech Stack & Versioning

This project uses a standardized stack to ensure consistency and maintainability. Specific versions are listed below for compatibility.

- **Frontend**:
  - **React.js** (v18.2): Component-based UI
  - **HTML5/CSS3**: Structural and design elements
  - **React Router** (v6.4): Navigation and routing

- **Backend**:
  - **Node.js** (v18.0): JavaScript runtime environment
  - **Express.js** (v4.18): Backend framework for API routing

- **Database**:
  - **PostgreSQL** (v15.1) or **MySQL** (v8.0): Relational database for structured data

- **Hosting & Deployment**:
  - **AWS** or **Heroku** (finalized during deployment)

- **Security**:
  - **SSL Encryption**: Ensures secure data transfer
  - **bcrypt.js** (v5.0): Password hashing

- **API Integrations**:
  - **QuickBooks API**: For invoice export

---

## Database Setup

Both **PostgreSQL** and **MySQL** are viable options for this application, each offering unique benefits. Below are setup instructions and pros/cons for each database, allowing the team to choose the best solution based on project requirements and team familiarity.

### PostgreSQL

#### Setup Instructions:
1. Install PostgreSQL.
   ```bash
   sudo apt update
   sudo apt install postgresql postgresql-contrib
   ```
2. Start PostgreSQL service.
   ```bash
   sudo service postgresql start
   ```
3. Create a new database.
   ```bash
   sudo -u postgres createdb forklift_maintenance
   ```
4. Configure the connection in the `.env` file:
   ```plaintext
   DB_TYPE=postgres
   DB_HOST=localhost
   DB_PORT=5432
   DB_USER=your_username
   DB_PASS=your_password
   DB_NAME=forklift_maintenance
   ```

#### Pros and Cons of PostgreSQL:
- **Pros**:
  - Known for reliability and ACID compliance, which is essential for financial data integrity.
  - Better suited for complex queries and large data sets, providing advanced data types and indexing options.
- **Cons**:
  - Slightly steeper learning curve compared to MySQL.
  - Resource usage can be higher, impacting smaller hosting budgets.

### MySQL

#### Setup Instructions:
1. Install MySQL.
   ```bash
   sudo apt update
   sudo apt install mysql-server
   ```
2. Start MySQL service.
   ```bash
   sudo service mysql start
   ```
3. Create a new database.
   ```bash
   mysql -u root -p
   CREATE DATABASE forklift_maintenance;
   ```
4. Configure the connection in the `.env` file:
   ```plaintext
   DB_TYPE=mysql
   DB_HOST=localhost
   DB_PORT=3306
   DB_USER=your_username
   DB_PASS=your_password
   DB_NAME=forklift_maintenance
   ```

#### Pros and Cons of MySQL:
- **Pros**:
  - Easier to set up and manage, making it ideal for smaller teams and projects.
  - Lower memory footprint, which can be more budget-friendly for hosting.
- **Cons**:
  - Limited support for complex data structures compared to PostgreSQL.
  - Transactions can be less robust, potentially impacting complex workflows.


## Hosting Options

The choice between **AWS** and **Heroku** will depend on budget, scalability needs, and desired control. Below is an analysis of each option.

### AWS

- **Setup**: Requires manual configuration, including setup of EC2 instances and databases.
- **Pros**:
  - Excellent scalability options with more control over server resources.
  - Cost-effective for large-scale applications that might expand over time.
- **Cons**:
  - Steeper learning curve; requires knowledge of AWS services and management.
  - More time-consuming setup and maintenance, which could impact small team productivity.
- **Budget Estimate**: Approx. $90/month with basic EC2 and RDS, plus additional fees for storage and data transfer.

### Heroku

- **Setup**: Streamlined setup and deployment, with minimal manual configuration.
- **Pros**:
  - User-friendly; deployment is simplified with automatic server management.
  - Built-in scaling options, making it ideal for small to medium-sized applications.
- **Cons**:
  - Higher cost as traffic scales; may not be as cost-efficient for large applications.
  - Limited control over infrastructure customization.
- **Budget Estimate**: Approx. $75/month for the basic dyno and database tiers, with scalability adjustments.


## Error Handling and Troubleshooting

For this project, a structured error-handling protocol is essential to ensure smooth operation and clarity in debugging. The following practices will be followed:

1. **Development Environment**:
   - Log errors to the console for immediate visibility.
   - Use descriptive error messages to simplify debugging.

2. **Production Environment**:
   - Implement error logging to a dedicated file for review (e.g., using `winston` or `morgan`).
   - Use error monitoring services (e.g., Sentry) for real-time alerts on critical errors.
   - Display user-friendly error messages without revealing technical details.

3. **Troubleshooting FAQ**:
   - Common setup issues will be documented in a troubleshooting section, updated regularly as issues are identified.

## Getting Started

### Prerequisites
Ensure the following tools are installed:
- **Node.js** (v18.0 or higher)
- **NPM** or **Yarn**
- **PostgreSQL** or **MySQL** (depending on the chosen database)

### Installation Process

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/yourusername/forklift-maintenance-app.git
    ```
2. **Navigate into the Project Directory**:
    ```bash
    cd forklift-maintenance-app
    ```
3. **Install Dependencies**:
    ```bash
    npm install
    ```
4. **Set Up Environment Variables**:
   - Create a `.env` file in the root directory and include the following:
     ```plaintext
     DB_TYPE=your_database_type (postgres or mysql)
     DB_HOST=your_database_host
     DB_PORT=your_database_port
     DB_USER=your_database_user
     DB_PASS=your_database_password
     DB_NAME=forklift_maintenance
     QUICKBOOKS_CLIENT_ID=your_quickbooks_client_id
     QUICKBOOKS_CLIENT_SECRET=your_quickbooks_client_secret
     ```
5. **Initialize the Database**:
   - For PostgreSQL:
     ```bash
     sudo -u postgres psql -c "CREATE DATABASE forklift_maintenance;"
     ```
   - For MySQL:
     ```bash
     mysql -u root -p -e "CREATE DATABASE forklift_maintenance;"
     ```
6. **Run Database Migrations** (if applicable):
    ```bash
    npm run db:migrate
    ```
7. **Start the Development Server**:
    ```bash
    npm start
    ```

8. **Access the Application**:
   - Open your browser and go to `http://localhost:3000`.

## Project Structure

The project follows a modular folder structure to maintain clarity, organization, and scalability. Here’s an overview of each main directory and its purpose:

- **/src**: Contains the main application files.
  - **/components**: Holds reusable React components, each representing distinct parts of the user interface.
  - **/services**: Contains modules for handling data interactions, such as API requests, database interactions, and authentication logic.
  - **/routes**: Defines backend API routes that the application’s frontend interacts with for CRUD operations.
  - **/controllers**: Implements business logic for handling requests, managing data flow, and interacting with models.
  - **/models**: Defines database schemas and models (for PostgreSQL or MySQL) to standardize data structures throughout the application.

- **/public**: Includes static assets such as images, icons, and any other files directly accessible by the client.

- **/config**: Stores configuration files, such as the database connection setup and environment-specific configurations. This directory helps to centralize configuration to ease the deployment process and environment-specific adjustments.

- **/middleware**: Contains any custom middleware functions that manage authentication, error handling, and other pre-processing tasks before passing data to controllers.

- **/utils**: Contains utility functions and helper files used across various parts of the project, improving code reusability and reducing redundancy.

- **/logs** (optional in production): Stores log files for error handling and debugging. For production, logs may be redirected to a monitoring service like Sentry.

- **/tests**: Holds testing files for different parts of the application, with unit tests and integration tests. Following best practices, each major component, service, and route has a corresponding test file to ensure code stability.


## Development Guidelines

To maintain code quality and consistency throughout the project, the following development guidelines should be followed:

- **Code Style**: This project follows the Airbnb JavaScript style guide. All team members should install the Airbnb ESLint configuration to catch syntax or style issues.
- **Branching Strategy**: Use Gitflow for version control. Main branches include `main` for production-ready code and `develop` for integration. Feature branches (`feature/branch-name`) are used for individual tasks and merged into `develop` upon completion.
- **Commit Messages**: Follow a structured format:
  - **feat**: Adding new functionality.
  - **fix**: Fixing a bug or issue.
  - **docs**: Documentation changes.
  - **style**: Code style, formatting, missing semi-colons, etc.
  - **refactor**: Code refactoring without adding new features or fixing bugs.
  - **test**: Adding or modifying tests.
- **Testing**: Write unit tests for each major component and function using Jest. All new code should aim for 80% test coverage, with a mix of unit and integration tests.
- **Documentation**: Every function, component, and module should include JSDoc comments. These comments explain inputs, outputs, and functionality, aiding in code readability.

---

## Milestones

The project is divided into key milestones to ensure steady progress and clear deliverables.

1. **Milestone 1: Setup & Planning** - Week 1
   - Finalize project structure, tech stack, and basic configurations.
   - Set up the repository, environment variables, and continuous integration.
   - Basic backend setup with Express and database schema creation.

2. **Milestone 2: MVP Development** - Weeks 2-4
   - Implement user authentication (admin and employee roles).
   - Develop core functionalities for customer and equipment tracking.
   - Create the initial frontend interface for work order management.

3. **Milestone 3: Invoicing & QuickBooks Integration** - Weeks 5-6
   - Develop invoice generation with form validation.
   - Integrate QuickBooks API for exporting invoices.
   - Complete backend API for work orders, customer data, and parts management.

4. **Milestone 4: Testing & Refinement** - Week 7
   - Conduct thorough testing (unit, integration, and user acceptance).
   - Address issues identified during testing and optimize application performance.

5. **Milestone 5: Deployment & Documentation** - Week 8
   - Deploy the application to the selected hosting provider (AWS or Heroku).
   - Finalize README, user guide, and troubleshooting documentation.
   - Conduct a final review and prepare the application for handoff.

---

## MVP (Minimum Viable Product)

The MVP will focus on the core functionality needed to support the forklift maintenance business. The following features are prioritized:

- **User Authentication**: Secure login for admin and employee roles.
- **Work Order Management**: Basic CRUD operations to create, read, update, and delete work orders.
- **Customer & Equipment Management**: Store and retrieve customer information, equipment details, and track work orders.
- **Invoice Generation**: Generate invoices with basic form fields for customer and job information, and provide the option to export to QuickBooks.
- **Error Notifications**: Basic error handling for user actions like invalid inputs or failed operations.

Additional features, such as advanced analytics and user notifications, will be considered post-MVP if they align with project goals.

---

## Usage Instructions

1. **Navigating the Interface**:
   - Use the sidebar navigation to access the main sections: Work Orders, Customers, Equipment, and Invoices.
   - The dashboard displays key metrics and recent activity for easy reference.

2. **Managing Work Orders**:
   - Employees can create and edit work orders, assigning them to customers and linking equipment where applicable.
   - Admin users can approve or modify work orders as needed.

3. **Generating Invoices**:
   - Navigate to the Invoices section to create a new invoice.
   - Select the customer, add job details, and mark items on the checklist as "OK," "Replaced," or "N/A."
   - Export the completed invoice to QuickBooks for record-keeping.

4. **User Roles**:
   - Admins have access to all functionalities, including user management and application settings.
   - Employees can access work orders and invoices but have limited access to customer details and application settings.

---

## License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## Author

Developed by Thomas Calle. For any inquiries, feel free to reach out.

- GitHub: [ThomasCalle](https://github.com/ThomasCalle)
- LinkedIn: [https://linkedin.com/in/thomascalle](https://linkedin.com/in/thomascalle)

---

## Acknowledgments

Special thanks to contributors and those who provided input for project development and testing along 
