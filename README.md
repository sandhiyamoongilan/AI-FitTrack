# 🏋️ AI FitTrack

### Personalized Fitness Recommendations Powered by Artificial Intelligence

AI FitTrack is a secure and scalable **AI-powered fitness tracking and recommendation backend** designed to simplify workout management and provide intelligent, personalized fitness guidance.

The system enables authenticated users to securely maintain their workout records, search and manage workout history, and receive AI-generated recommendations based on their **age, fitness goals, experience level, and workout statistics**.

The backend is developed using **Node.js, Express.js, MongoDB, and Mongoose**, with **Google Gemini AI** integrated through a dedicated service layer. The application follows a modular **Model–View–Controller (MVC) architecture**, making it maintainable, scalable, and suitable for integration with web applications, mobile applications, and third-party API clients.

---

## 📌 Table of Contents

* [Project Overview](#-project-overview)
* [Problem Statement](#-problem-statement)
* [Proposed Solution](#-proposed-solution)
* [Objectives](#-objectives)
* [Key Features](#-key-features)
* [AI Capabilities](#-ai-capabilities)
* [System Architecture](#-system-architecture)
* [Technology Stack](#-technology-stack)
* [Project Structure](#-project-structure)
* [Database Design](#-database-design)
* [Application Workflow](#-application-workflow)
* [API Modules](#-api-modules)
* [Security](#-security)
* [Installation and Setup](#-installation-and-setup)
* [Environment Configuration](#-environment-configuration)
* [API Testing](#-api-testing)
* [Hardware and Software Requirements](#-hardware-and-software-requirements)
* [Project Outcome](#-project-outcome)
* [Future Enhancements](#-future-enhancements)
* [Demo and Resources](#-demo-and-resources)
* [Project Information](#-project-information)

---

# 📖 Project Overview

Many fitness enthusiasts maintain their workout information manually using notebooks or spreadsheets. This makes it difficult to maintain an organized workout history, monitor progress, search previous activities, and determine whether their workout routine aligns with their fitness goals.

**AI FitTrack** addresses these challenges through a centralized backend system that combines secure workout management with AI-powered fitness guidance.

The system provides RESTful APIs through which authenticated users can:

* Register and securely log in
* Manage personal workout records
* Search workout history
* View workout statistics
* Generate personalized workout recommendations
* Obtain AI-generated fitness insights

The application uses JWT authentication to protect personal workout information, while passwords are securely hashed using bcrypt.js before being stored in MongoDB.

---

# ❗ Problem Statement

Traditional manual fitness tracking creates several challenges:

* Difficulty maintaining a centralized workout record
* Inaccurate or inconsistent manual tracking
* Lack of secure authentication for personal fitness data
* Difficulty searching previous workouts
* Lack of personalized workout recommendations
* Limited understanding of overall workout performance
* Manual calculation of workout duration and calories burned
* Lack of intelligent fitness guidance

These limitations create a need for a secure and intelligent system that can automate workout management while providing personalized recommendations.

---

# 💡 Proposed Solution

AI FitTrack provides a centralized and secure backend where users can register, authenticate, and manage their workout records through RESTful APIs.

The system supports complete **CRUD operations** for workouts and provides search functionality based on workout name, category, and workout date.

The integration of **Google Gemini AI** enables the system to analyze user information and workout statistics and generate personalized workout recommendations and fitness insights.

Security is implemented through:

* JWT authentication
* Password hashing
* Protected middleware
* Input validation
* MongoDB schema validation
* Centralized error handling
* Environment-based configuration

---

# 🎯 Objectives

The primary objectives of AI FitTrack are:

1. To provide a centralized platform for managing workout records.
2. To implement secure user authentication and authorization.
3. To provide complete workout CRUD functionality.
4. To enable efficient searching of workout history.
5. To integrate Google Gemini AI for personalized fitness recommendations.
6. To analyze workout statistics and generate meaningful fitness insights.
7. To develop a modular and scalable backend architecture.
8. To provide standardized JSON-based REST API responses.
9. To maintain secure storage of user and workout information.

---

# ✨ Key Features

## 🔐 1. Secure User Authentication

AI FitTrack provides secure authentication functionality using **JWT**.

### Features

* User registration
* Secure login
* Password encryption using bcrypt.js
* JWT token generation
* Protected API routes
* User profile retrieval
* Authentication middleware

Every protected API request is validated using the JWT token before allowing access to sensitive resources.

---

## 🏋️ 2. Workout Management

Authenticated users can manage their workout records using RESTful APIs.

### Supported Operations

* Create workout
* View all workouts
* Retrieve workout by ID
* Update workout
* Delete workout

Each workout record is associated with its authenticated user.

---

## 🔎 3. Workout Search

The system provides search functionality to make workout history easier to access.

Users can search workouts using:

* Workout name
* Workout category
* Workout date

---

## 🤖 4. AI-Powered Workout Recommendations

Google Gemini AI is integrated through a dedicated service layer.

The user provides:

* Age
* Fitness goal
* Experience level

The AI generates:

* Personalized workout plans
* Weekly exercise suggestions
* Beginner/intermediate/advanced recommendations
* Training tips
* Safety recommendations
* Motivational guidance

---

## 📊 5. AI Fitness Insights

AI FitTrack can analyze workout statistics including:

* Total workouts
* Average workout duration
* Total calories burned

Based on these values, the AI generates:

* Performance analysis
* Improvement suggestions
* Motivational advice
* Fitness progress summaries

---

## 🛡️ 6. Centralized Error Handling

The backend provides standardized JSON error responses for situations such as:

* Invalid credentials
* Missing authentication tokens
* Validation errors
* Database errors
* Internal server errors

---

# 🧠 AI Capabilities

The AI module communicates with **Google Gemini** through a dedicated service layer.

### Recommendation Flow

```text
User Information
      │
      ├── Age
      ├── Fitness Goal
      └── Experience Level
             │
             ▼
       Gemini AI Service
             │
             ▼
   Personalized Recommendation
             │
             ├── Workout Plan
             ├── Exercise Suggestions
             ├── Training Tips
             ├── Safety Tips
             └── Motivation
```

### Fitness Insight Flow

```text
Workout Statistics
      │
      ├── Total Workouts
      ├── Average Duration
      └── Calories Burned
             │
             ▼
       Gemini AI Service
             │
             ▼
       Fitness Insights
             │
             ├── Performance Analysis
             ├── Improvement Suggestions
             ├── Motivation
             └── Progress Summary
```

---

# 🏗️ System Architecture

AI FitTrack follows a layered architecture based on the **MVC design pattern**.

```text
                    Client Layer
             React / Mobile App / Postman
                         │
                         ▼
                  Express Server
                         │
                         ▼
                    API Routes
                         │
                         ▼
              Authentication Middleware
                         │
                         ▼
                    Controllers
                    /         \
                   /           \
                  ▼             ▼
             Services         Models
                │                │
                ▼                ▼
          Google Gemini       Mongoose
                                  │
                                  ▼
                               MongoDB
```

The architecture separates routing, authentication, business logic, database operations, and AI services into independent modules.

This separation improves:

* Maintainability
* Scalability
* Code organization
* Reusability
* Security
* Testing
* Future extensibility

---

# 🧩 Architecture Components

## Client Layer

The client layer can be represented by:

* React application
* Mobile application
* Postman
* Other API consumers

It sends HTTP requests and receives JSON responses.

## Express Server

The Express server acts as the central gateway.

Responsibilities include:

* Starting the HTTP server
* Parsing JSON requests
* Enabling CORS
* Registering routes
* Connecting middleware
* Handling centralized errors

## Authentication Middleware

The authentication middleware:

1. Reads the Authorization header
2. Extracts the JWT token
3. Verifies the token
4. Decodes user information
5. Attaches user information to the request
6. Rejects unauthorized requests

## Route Layer

Routes map HTTP requests to their respective controller functions.

## Controller Layer

Controllers handle:

* Request validation
* Business logic
* Database operations
* AI service invocation
* JSON responses

## Service Layer

The service layer contains reusable application logic.

Major services include:

* Gemini AI Service
* JWT Service
* Password Service

## Database Layer

MongoDB stores persistent application data, while Mongoose provides schema definitions, validation, relationships, and database operations.

---

# 🛠️ Technology Stack

| Technology             | Purpose                                           |
| ---------------------- | ------------------------------------------------- |
| **Node.js**            | Backend runtime environment                       |
| **Express.js**         | RESTful API development                           |
| **MongoDB**            | NoSQL database                                    |
| **Mongoose**           | MongoDB ODM and schema management                 |
| **Google Gemini AI**   | Personalized recommendations and fitness insights |
| **JWT**                | Authentication and API protection                 |
| **bcrypt.js**          | Password hashing                                  |
| **dotenv**             | Environment variable management                   |
| **CORS**               | Cross-origin resource sharing                     |
| **Postman**            | API testing                                       |
| **Visual Studio Code** | Development environment                           |

The project documentation specifies Node.js v16 or above and npm v8 or above as the primary runtime requirements.

---

# 📂 Project Structure

The backend is organized into independent modules following the MVC architecture.

```text
AI-FitTrack-API/
│
└── server/
    │
    ├── config/
    │   └── db.js
    │
    ├── controllers/
    │   ├── authController.js
    │   ├── workoutController.js
    │   └── aiController.js
    │
    ├── middleware/
    │   └── authentication/
    │
    ├── models/
    │   ├── User.js
    │   └── Workout.js
    │
    ├── routes/
    │   ├── authentication/
    │   ├── workout/
    │   └── ai/
    │
    ├── services/
    │   ├── geminiService.js
    │   ├── jwtService.js
    │   └── passwordService.js
    │
    ├── .env
    ├── package.json
    └── server.js
```

> **Note:** Keep the folder names in this section synchronized with the actual files you upload to GitHub.

---

# 🗄️ Database Design

AI FitTrack uses **MongoDB** as its primary database and **Mongoose** as the Object Data Modeling library.

The system contains two primary collections:

### 👤 Users Collection

Stores user authentication and profile information.

| Field       | Type     | Description          |
| ----------- | -------- | -------------------- |
| `_id`       | ObjectId | Primary key          |
| `name`      | String   | User name            |
| `email`     | String   | Unique email address |
| `password`  | String   | Encrypted password   |
| `createdAt` | Date     | Record creation time |
| `updatedAt` | Date     | Last update time     |

### 🏋️ Workouts Collection

Stores workout information associated with authenticated users.

| Field            | Type     | Description         |
| ---------------- | -------- | ------------------- |
| `_id`            | ObjectId | Primary key         |
| `user`           | ObjectId | Reference to User   |
| `workoutName`    | String   | Workout name        |
| `category`       | String   | Workout category    |
| `duration`       | Number   | Duration in minutes |
| `caloriesBurned` | Number   | Calories burned     |
| `workoutDate`    | Date     | Workout date        |
| `createdAt`      | Date     | Creation timestamp  |
| `updatedAt`      | Date     | Update timestamp    |

A single user can have multiple workout records, creating a **one-to-many relationship** between Users and Workouts.

---

# 🔄 Application Workflow

```text
1. User Registration
        ↓
2. User Login
        ↓
3. JWT Token Generated
        ↓
4. Token Used for Protected APIs
        ↓
5. User Creates / Manages Workouts
        ↓
6. Workout Data Stored in MongoDB
        ↓
7. User Requests AI Recommendation
        ↓
8. Gemini AI Processes User Information
        ↓
9. Personalized Recommendation Returned
```

For fitness insights:

```text
Workout Statistics
        ↓
Gemini AI Service
        ↓
AI Analysis
        ↓
Fitness Insights
        ↓
JSON Response
```

---

# 🔗 API Modules

## Authentication APIs

| Method | Function         |
| ------ | ---------------- |
| POST   | Register User    |
| POST   | Login User       |
| GET    | Get User Profile |

## Workout APIs

| Method | Function          |
| ------ | ----------------- |
| POST   | Add Workout       |
| GET    | Get All Workouts  |
| GET    | Get Workout by ID |
| GET    | Search Workouts   |
| PUT    | Update Workout    |
| DELETE | Delete Workout    |

## AI APIs

| Function               | Description                                       |
| ---------------------- | ------------------------------------------------- |
| Workout Recommendation | Generates personalized workout guidance           |
| Fitness Insights       | Analyzes workout statistics and provides insights |

The documented API modules cover authentication, workout management, workout search, AI recommendations, and AI fitness insights.

---

# 🔒 Security

Security is an important component of AI FitTrack.

The system implements:

### JWT Authentication

Protected APIs require a valid JWT token.

### Password Protection

Passwords are hashed using **bcrypt.js** before being stored in MongoDB.

### Protected Resources

Authentication middleware prevents unauthorized access to personal workout information.

### Environment Variables

Sensitive configuration such as:

* MongoDB connection string
* JWT secret
* Gemini API key

is stored through environment variables rather than hard-coded into the application.

### Validation

Mongoose schemas provide validation rules for user and workout data.

---

# ⚙️ Installation and Setup

## Prerequisites

Make sure the following are installed:

* Node.js v16+
* npm v8+
* MongoDB
* Postman or Thunder Client
* Visual Studio Code or another code editor

## Step 1 — Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd AI-FitTrack-API
```

## Step 2 — Navigate to Server

```bash
cd server
```

## Step 3 — Install Dependencies

```bash
npm install
```

The documented dependencies include:

```bash
npm install express mongoose dotenv bcryptjs jsonwebtoken cors
```

For development:

```bash
npm install --save-dev nodemon
```

## Step 4 — Configure MongoDB

Start your local MongoDB server or use a MongoDB deployment and obtain the connection string.

## Step 5 — Configure Environment Variables

Create a `.env` file in the server directory.

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key
GEMINI_API_KEY=your_google_gemini_api_key
```

The project documentation specifies these environment variables for server, MongoDB, JWT, and Gemini configuration.

## Step 6 — Start the Application

```bash
npm start
```

For development using Nodemon:

```bash
npm run dev
```

---

# 🧪 API Testing

The project uses **Postman** for API testing.

Testing is performed across three major areas:

### 1. Authentication Testing

* Register User
* Login User
* Get Profile

### 2. Workout Testing

* Add Workout
* Get All Workouts
* Get Workout by ID
* Update Workout
* Delete Workout

### 3. AI Testing

* Workout Recommendation
* Fitness Insights

This testing process verifies authentication, request handling, database operations, workout management, and AI integration.

---

# 💻 Hardware and Software Requirements

## Software Requirements

* Windows 10/11, macOS, or Linux
* Node.js v16 or above
* npm v8 or above
* Express.js
* MongoDB
* Postman
* Visual Studio Code or similar IDE

## Hardware Requirements

* **Processor:** Intel Core i5 8th Gen or above / AMD Ryzen 5 or equivalent
* **RAM:** 8 GB minimum, 16 GB recommended
* **Storage:** At least 1 GB available workspace

---

# 📈 Project Outcome

AI FitTrack provides a centralized backend solution for managing personal workout information while reducing the need for manual record keeping.

The system combines:

* Secure authentication
* Workout CRUD operations
* Workout searching
* MongoDB data management
* RESTful API design
* Google Gemini AI integration
* Personalized workout recommendations
* AI-powered fitness insights

The modular MVC architecture also provides a foundation for future expansion without requiring major architectural changes.

---

# 🚀 Future Enhancements

The project can be further extended with:

* 🥗 Nutrition tracking
* 📏 BMI calculation
* ⌚ Wearable device integration
* 🔔 Workout reminders
* 📊 Advanced fitness analytics dashboards
* 📱 Dedicated mobile application
* Additional personalized fitness features

These extensions can be incorporated while maintaining the existing modular architecture.

---

# 🎥 Demo & Project Resources

### 🎬 Project Demo

[Watch the AI FitTrack Demo](https://drive.google.com/file/d/1KswrctSaPI0eOYyJ3GkbbVHvHsU3EfZJ/view?usp=sharing)

### 🧪 API Testing Video

[Watch API Testing Demonstration](https://drive.google.com/file/d/1TCXG48a-78ryxF3gipdRMwRBwuhAgPaa/view?usp=drive_link)

### 📁 Project Resources

[Access Project Resources](https://drive.google.com/drive/folders/1hwmKxkHQkUI62JR1svI3xCQ2ShZ6Lj9y)

The above resources are provided in the project documentation.

---

# 📌 Project Highlights

| Area                    | Implementation               |
| ----------------------- | ---------------------------- |
| Backend                 | Node.js + Express.js         |
| Database                | MongoDB + Mongoose           |
| Architecture            | MVC                          |
| Authentication          | JWT                          |
| Password Security       | bcrypt.js                    |
| Artificial Intelligence | Google Gemini                |
| API Style               | RESTful                      |
| API Response            | JSON                         |
| Testing                 | Postman                      |
| AI Feature              | Personalized Recommendations |
| AI Analytics            | Fitness Insights             |

---

# 👩‍💻 Project Information

**Project Name:** AI FitTrack
**Project Type:** AI-Powered Fitness Tracking Backend
**Architecture:** Model–View–Controller (MVC)
**Primary Technologies:** Node.js, Express.js, MongoDB, Mongoose
**AI Technology:** Google Gemini AI
**Authentication:** JWT
**API Testing:** Postman

---

## ⭐ Conclusion

AI FitTrack demonstrates the integration of **backend development, database management, secure authentication, RESTful API design, and generative AI** into a practical fitness application.

By combining structured workout management with AI-powered recommendations and fitness insights, the project provides a scalable foundation for intelligent fitness applications and can be further extended with nutrition, wearable-device, reminder, and analytics capabilities.
