# How to Preview the School Management System on Localhost

## Overview

This document provides step-by-step instructions on how to set up and preview the School Management System on your local machine.

## Prerequisites

Before you begin, ensure you have the following installed on your system:
1. Node.js (version 14 or higher)
2. npm (Node Package Manager)
3. MongoDB (for database functionality)
4. Git (to clone the repository)

The project also includes VS Code configuration files for debugging and task automation:
- `.vscode/launch.json` - Debug configurations
- `.vscode/tasks.json` - Common tasks
- `.vscode/settings.json` - Project-specific settings

## Setup Instructions

### Step 1: Clone the Repository

Open your terminal or command prompt and run:

```bash
git clone <repository-url>
cd school-management-system
```

### Step 2: Install Dependencies

Install dependencies from the root directory (this will install dependencies for both backend and frontend):

```bash
npm install
```

Alternatively, you can install dependencies separately for each part:

#### Backend Setup

Navigate to the backend directory and install dependencies:

```bash
cd backend
npm install
```

Create a `.env` file in the backend directory with the following content:

```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/school_management
JWT_SECRET=your_jwt_secret_here
JWT_EXPIRATION=1h
```

### Step 3: Frontend Setup

Open a new terminal window/tab and navigate to the frontend directory:

```bash
cd frontend
npm install
```

Alternatively, if you installed dependencies from the root directory, you can skip this step.

### Step 4: Start MongoDB

Make sure MongoDB is running on your system. If you have MongoDB installed locally, you can start it with:

```bash
mongod
```

If you don't have MongoDB installed, you can:
1. Download and install MongoDB from [mongodb.com](https://www.mongodb.com/try/download/community)
2. Use a cloud MongoDB service like MongoDB Atlas
3. Use Docker to run MongoDB locally

## Running the Application

### Option 1: Run Both from Root Directory (Recommended)

You can run both the backend and frontend simultaneously from the root directory:

```bash
npm start
```

This will start both servers concurrently. The backend will be available at `http://localhost:5000` and the frontend at `http://localhost:3000`.

### Option 2: Run Backend and Frontend Separately (Recommended for Development)

1. Start the backend server:
   In the first terminal (in the backend directory):
   ```bash
   npm run dev
   ```
   
   The backend will be available at `http://localhost:5000`

2. Start the frontend development server:
   In the second terminal (in the frontend directory):
   ```bash
   npm start
   ```
   
   The frontend will be available at `http://localhost:3000`

### Option 3: Run Both with Concurrently

To run both servers simultaneously, you can install `concurrently` globally:

```bash
npm install -g concurrently
```

Then from the root directory, run:

```bash
concurrently "cd backend && npm run dev" "cd frontend && npm start"
```

## Accessing the Application

Once both servers are running:

1. Open your web browser
2. Navigate to `http://localhost:3000`
3. You should see the School Management System homepage

## Default Pages

The application currently includes:

1. **Home Page** (`/`): Welcome page with basic information
2. **Login Page** (`/login`): User authentication page
3. **Dashboard Page** (`/dashboard`): Main application dashboard (requires authentication)

## API Endpoints

The backend API is accessible at `http://localhost:5000/api`

Available endpoints:
- `GET /api/test` - Test endpoint that returns a success message
- `GET /api/health` - Health check endpoint

## Troubleshooting

### Common Issues and Solutions

1. **Port already in use**
   - Solution: Change the PORT in the backend `.env` file to a different port (e.g., 5001)

2. **MongoDB connection failed**
   - Solution: Ensure MongoDB is running and the connection string in `.env` is correct
   - If using MongoDB Atlas, update the `MONGO_URI` with your Atlas connection string

3. **CORS errors**
   - Solution: Check the CORS configuration in `backend/src/app.ts`

4. **Frontend not connecting to backend**
   - Solution: Ensure the backend API URL in `frontend/src/services/api.ts` matches your backend URL

5. **"Module not found" errors**
   - Solution: Run `npm install` in both frontend and backend directories

### Debugging Tips

1. Check the console logs in both backend and frontend terminals
2. Verify all environment variables are set correctly
3. Ensure all dependencies are installed with `npm install`
4. Check that MongoDB is running and accessible

## Development Workflow

### Backend Development

1. All backend code is in the `backend/src/` directory
2. The main server file is `backend/src/app.ts`
3. Routes are defined in `backend/src/routes/`
4. Models are defined in `backend/src/models/`

### Frontend Development

1. All frontend code is in the `frontend/src/` directory
2. The main application component is `frontend/src/App.tsx`
3. Routing is handled in `frontend/src/routes/`
4. Pages are in `frontend/src/pages/`
5. Components are in `frontend/src/components/`

## Building for Production

You can build both backend and frontend from the root directory:

```bash
npm run build
```

### Backend Build

```bash
cd backend
npm run build
```

### Frontend Build

```bash
cd frontend
npm run build
```

The production build will be in the `frontend/build/` directory.

## Next Steps

To fully implement the application, you would need to:

1. Implement the missing page components (LoginPage, DashboardPage, etc.)
2. Create the UI component library (Button, Input, Card, etc.)
3. Implement the complete backend API endpoints
4. Create the database models and connect them to the API
5. Implement authentication and authorization
6. Add state management to the frontend

For detailed development instructions, please refer to the [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md) file.

## Available Root Scripts

The root package.json includes several helpful scripts for managing the monorepo:

- `npm install` - Install dependencies for both backend and frontend
- `npm start` - Start both backend and frontend servers concurrently
- `npm run build` - Build both backend and frontend applications
- `npm test` - Run tests for both backend and frontend
- `npm run dev` - Start both backend and frontend in development mode