# ContactManagementApp

# Project Description
The Contact Management System allows users to perform CRUD operations on contact data. Users can add, view, update, and delete contacts via a user-friendly React-based frontend integrated with Material-UI components. The backend is powered by Node.js and Express, with MongoDB serving as the database for storing contact information.

This application is particularly useful in business settings to manage customer/client relationships efficiently.

# Setup Instructions
Prerequisites
Node.js installed (v14+ recommended).
MongoDB installed locally or hosted (e.g., MongoDB Atlas).

# Backend Setup

Clone the repository:
git clone <repository_url>
cd contact-management-backend

Install dependencies:
npm install

Create a .env file in the root directory with the following content:
MONGO_URI=mongodb://localhost:27017/contact_management
PORT=5000

Start the backend server:
node server.js

Ensure the server is running at http://localhost:5000.

# Frontend Setup
Navigate to the frontend directory:
cd ../contact-management-frontend

Install dependencies:
npm install

Start the React development server:
npm start
Access the frontend at http://localhost:3000.

# Database Schema
The MongoDB schema for storing contacts is defined as:
const ContactSchema = new mongoose.Schema({
  firstName: { type: String, required: true },
  lastName: { type: String, required: true },
  email: { type: String, required: true, unique: true },
  phoneNumber: { type: String, required: true },
  company: { type: String },
  jobTitle: { type: String },
}, { timestamps: true });


# App Features
Frontend:
Contact Form: Users can add or edit contacts using Material-UI components.
Contact Table: Displays all contacts with sorting and pagination, enabling efficient browsing.
Actions: Edit and delete actions are available for each contact.

Backend:
API Endpoints:
POST /contacts: Add a new contact.
GET /contacts: Retrieve all contacts.
PUT /contacts/:id: Update an existing contact.
DELETE /contacts/:id: Remove a contact.
Validation: Ensures required fields are present, and duplicate emails are rejected.

# Technical Decisions
MongoDB: Chosen for its flexibility, ease of use, and compatibility with JSON-based data structures.
Material-UI: Provides modern UI components and saves development time with a consistent design system.
Axios: Simplifies HTTP requests between the frontend and backend.
Modular Architecture: Clean separation of concerns between controllers, routes, and the frontend.

# Challenges and Solutions
Challenge 1: Duplicate Email Validation
Problem: Preventing duplicate email entries in the database.
Solution: Used the unique constraint in MongoDB and added error handling in the POST /contacts endpoint to return appropriate messages when duplicates are detected.

Challenge 2: Pagination and Sorting
Problem: Managing large contact lists in the frontend.
Solution: Implemented Material-UI Table with built-in pagination and sorting options for better user experience.

Challenge 3: API Error Handling
Problem: Displaying meaningful error messages in the frontend.
Solution: Added robust error handling in the backend, ensuring clear and actionable messages are sent to the frontend.

Challenge 4: Managing State for Edit Functionality
Problem: Keeping track of the contact being edited.
Solution: Used React state (useState) to store the selected contact's data, passed it as props to the ContactForm, and reset the state after successful updates.

# How the App Works
The frontend sends HTTP requests to the backend using Axios.
The backend processes the requests and interacts with the MongoDB database to perform CRUD operations.
The responses are sent back to the frontend to update the UI dynamically.
Material-UI components ensure the UI is clean, consistent, and responsive.
