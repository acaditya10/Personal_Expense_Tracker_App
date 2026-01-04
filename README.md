# Personal Expense Tracker App

A full-stack Personal Expense Tracker application built with the MERN stack (MongoDB, Express, React, Node.js).

## Project Structure

- **frontend/**: React application using Vite and Tailwind CSS.
- **backend/**: Node.js/Express API connected to MongoDB.

## Features

- User Authentication (Clerk/JWT)
- Add, Edit, Delete Income and Expenses (Assumed)
- Visualization with Charts (Recharts)
- Download Reports as Excel
- Responsive Design

## Getting Started

### Prerequisites

- Node.js (v18+ recommended)
- MongoDB Database (Local or Atlas)

### Installation

1.  **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd Personal_Expense_Tracker_App
    ```

2.  **Install Backend Dependencies:**
    ```bash
    cd backend
    npm install
    ```
    Create a `.env` file in the `backend` directory with your Mongo URI and JWT Secret/Clerk Keys.

3.  **Install Frontend Dependencies:**
    ```bash
    cd ../frontend
    npm install
    ```
    Create a `.env` file in `frontend` if necessary (e.g., for Clerk Publishable Key).

### Running the Application

**Backend:**
```bash
cd backend
npm start
# or for development
npm run dev
```

**Frontend:**
```bash
cd frontend
npm run dev
```

The frontend will usually run on `http://localhost:5173`.

## Deployment

Build the frontend:
```bash
cd frontend
npm run build
```
