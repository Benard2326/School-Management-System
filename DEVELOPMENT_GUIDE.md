# School Management System - Development Guide

## Overview

This guide explains how to set up and run the School Management System locally on your machine.

## Prerequisites

Before you begin, ensure you have the following installed:
- Node.js (version 14 or higher)
- npm (Node Package Manager)
- MongoDB (for database functionality)

The project also includes VS Code configuration files for debugging and task automation:
- `.vscode/launch.json` - Debug configurations
- `.vscode/tasks.json` - Common tasks
- `.vscode/settings.json` - Project-specific settings

## Project Structure

The project is organized as a MERN stack application:
```
school-management-system/
├── package.json
├── backend/
│   ├── src/
│   │   ├── app.ts (Express server)
│   │   ├── config/
│   │   ├── controllers/
│   │   ├── middlewares/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── types/
│   │   └── utils/
│   ├── package.json
│   └── tsconfig.json
├── frontend/
│   ├── src/
│   │   ├── App.tsx
│   │   ├── index.tsx
│   │   ├── components/
│   │   ├── pages/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── types/
│   │   └── utils/
│   ├── package.json
│   └── tsconfig.json
├── README.md
└── DEVELOPMENT_GUIDE.md
```

## Setup Instructions

### 1. Clone the Repository

```bash
git clone <repository-url>
cd school-management-system
```

### 2. Install Dependencies

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

#### Frontend Setup

Navigate to the frontend directory and install dependencies:

```bash
cd ../frontend
npm install
```

### 4. Start MongoDB

Make sure MongoDB is running on your system. If you have MongoDB installed locally, you can start it with:

```bash
mongod
```

If you don't have MongoDB installed, you can use a cloud MongoDB service like MongoDB Atlas.

## Running the Application

### Option 1: Run Both from Root Directory (Recommended)

You can run both the backend and frontend simultaneously from the root directory:
```bash
npm start
```

This will start both servers concurrently. The backend will be available at `http://localhost:5000` and the frontend at `http://localhost:3000`.

### Option 2: Run Backend and Frontend Separately

1. Start the backend server:
```bash
cd backend
npm run dev
```

The backend will be available at `http://localhost:5000`

2. Start the frontend development server:
```bash
cd frontend
npm start
```

The frontend will be available at `http://localhost:3000`

### Option 3: Run Both with Concurrently

If you prefer to use concurrently directly, you can install it globally:

```bash
npm install -g concurrently
```

Then from the root directory, run:

```bash
concurrently "cd backend && npm run dev" "cd frontend && npm start"
```

## API Endpoints

The backend API is accessible at `http://localhost:5000/api`

Some available endpoints:
- `GET /api/test` - Test endpoint
- `GET /api/health` - Health check

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

## Testing

You can run tests for both backend and frontend from the root directory:
```bash
npm test
```

### Backend Testing

To run backend tests:
```bash
cd backend
npm test
```

### Frontend Testing

To run frontend tests:
```bash
cd frontend
npm test
```

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

## Available Root Scripts

The root package.json includes several helpful scripts for managing the monorepo:

- `npm install` - Install dependencies for both backend and frontend
- `npm start` - Start both backend and frontend servers concurrently
- `npm run build` - Build both backend and frontend applications
- `npm test` - Run tests for both backend and frontend
- `npm run dev` - Start both backend and frontend in development mode

## Troubleshooting

### Common Issues

1. **Port already in use**: Change the PORT in the backend `.env` file
2. **MongoDB connection failed**: Ensure MongoDB is running and the connection string is correct
3. **CORS errors**: Check the CORS configuration in `backend/src/app.ts`

### Debugging Tips

1. Check the console logs in both backend and frontend
2. Verify all environment variables are set correctly
3. Ensure all dependencies are installed with `npm install`

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Write tests if applicable
5. Submit a pull request

## Additional Resources

- [Express.js Documentation](https://expressjs.com/)
- [React Documentation](https://reactjs.org/)
- [MongoDB Documentation](https://docs.mongodb.com/)
- [TypeScript Documentation](https://www.typescriptlang.org/)