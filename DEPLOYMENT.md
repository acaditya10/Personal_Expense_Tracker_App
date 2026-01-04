# Deployment Guide: Personal Expense Tracker

This guide outlines the steps to deploy your MERN stack application. We will use **Render** for the Backend (Node.js/Express) and **Vercel** for the Frontend (React/Vite).

## Prerequisites
1.  **GitHub Repository**: Ensure your code is pushed to GitHub (Already done!).
2.  **MongoDB Atlas**: You need a cloud database.
    -   Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas).
    -   Create a free cluster.
    -   Get your connection string (URI). It looks like: `mongodb+srv://<username>:<password>@cluster0.mongodb.net/?retryWrites=true&w=majority`

---

## Part 1: Deploy Backend (Render)
Render is excellent for hosting Node.js APIs.

1.  **Sign Up/Login** to [Render](https://render.com/).
2.  Click **"New +"** -> **"Web Service"**.
3.  Connect your GitHub repository.
4.  **Configure Service**:
    -   **Name**: `expense-tracker-api` (or similar)
    -   **Root Directory**: `backend` (Important! Your server is in this subfolder).
    -   **Environment**: `Node`
    -   **Build Command**: `npm install`
    -   **Start Command**: `npm start`
5.  **Environment Variables** (Scroll down to "Advanced"):
    -   `MONGO_URI`: *Paste your MongoDB connection string here*.
    -   `JWT_SECRET`: *Enter a secure random string*.
    -   `CLIENT_URL`: *Leave blank for now, we will update this after deploying the frontend*.
6.  Click **"Create Web Service"**.
7.  **Wait**: Render will build and deploy. Once finished, copy the **Service URL** (e.g., `https://expense-tracker-api.onrender.com`).

---

## Part 2: Deploy Frontend (Vercel)
Vercel is optimized for Vite/React apps.

1.  **Sign Up/Login** to [Vercel](https://vercel.com/).
2.  Click **"Add New..."** -> **"Project"**.
3.  Import your GitHub repository.
4.  **Configure Project**:
    -   **Framework Preset**: Vite (should detect auto-magically).
    -   **Root Directory**: Click "Edit" and select `frontend`.
5.  **Environment Variables**:
    -   `VITE_API_BASE_URL`: *Paste your Render Backend URL here* (e.g., `https://expense-tracker-api.onrender.com`).
    -   `VITE_CLERK_PUBLISHABLE_KEY`: *Your Clerk Key (if using Clerk)*.
6.  Click **"Deploy"**.
7.  **Wait**: Vercel will build and assign a domain (e.g., `https://expense-tracker-app.vercel.app`).

---

## Part 3: Connect Them
Now that both are up, tell the Backend to allow requests from the Frontend.

1.  Go back to **Render Dashboard** -> Select your Backend service.
2.  Go to **"Environment"**.
3.  Add/Update `CLIENT_URL` with your **Vercel Frontend URL** (e.g., `https://expense-tracker-app.vercel.app`).
    -   *Note: Remove any trailing slash `/` from the URL*.
4.  Render will auto-redeploy.

**Done!** Your app is now live.
