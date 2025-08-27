# School Management System

This project is a comprehensive School Management System built using the MERN stack (MongoDB, Express, React, Node) with TypeScript. It provides a robust platform for managing various aspects of a school, including student information, attendance tracking, grade management, fee processing, timetable scheduling, and communication through announcements.

## Features

- **Authentication and Role Management**: Secure login and role-based access control for different user types (admin, teacher, student, guardian).
- **Core Entities Management**: CRUD operations for managing students, teachers, classes, subjects, and enrollments.
- **Attendance Tracking**: Record and manage student attendance efficiently.
- **Gradebook Functionality**: Manage and track student grades and assignments.
- **Fee Management**: Handle invoicing and payment processing for student fees.
- **Timetable Scheduling**: Create and manage class schedules and timetables.
- **Messaging/Announcements**: Send and manage announcements to students and staff.

## Project Structure

```
school-management-system
├── package.json
├── backend
│   ├── src
│   │   ├── app.ts
│   │   ├── config
│   │   │   └── index.ts
│   │   ├── controllers
│   │   │   └── index.ts
│   │   ├── middlewares
│   │   │   └── auth.ts
│   │   ├── models
│   │   │   └── index.ts
│   │   ├── routes
│   │   │   └── index.ts
│   │   ├── services
│   │   │   └── index.ts
│   │   ├── types
│   │   │   └── index.ts
│   │   └── utils
│   │       └── index.ts
│   ├── package.json
│   ├── tsconfig.json
│   └── README.md
├── frontend
│   ├── src
│   │   ├── App.tsx
│   │   ├── index.tsx
│   │   ├── components
│   │   │   └── index.tsx
│   │   ├── pages
│   │   │   └── index.tsx
│   │   ├── routes
│   │   │   └── index.tsx
│   │   ├── services
│   │   │   └── api.ts
│   │   ├── types
│   │   │   └── index.ts
│   │   └── utils
│   │       └── index.ts
│   ├── package.json
│   ├── tsconfig.json
│   └── README.md
├── README.md
└── DEVELOPMENT_GUIDE.md
```

## Getting Started

### Prerequisites

- Node.js
- MongoDB
- TypeScript

The project also includes VS Code configuration files for debugging and task automation:
- `.vscode/launch.json` - Debug configurations
- `.vscode/tasks.json` - Common tasks
- `.vscode/settings.json` - Project-specific settings

### Installation

1. Clone the repository:
   ```
   git clone <repository-url>
   ```

2. Install dependencies from the root directory (this will install dependencies for both backend and frontend):
   ```
   npm install
   ```

Alternatively, you can install dependencies separately for each part:

2a. Navigate to the backend directory and install dependencies:
   ```
   cd backend
   npm install
   ```

2b. Navigate to the frontend directory and install dependencies:
   ```
   cd frontend
   npm install
   ```

### Running the Application

You can run both the backend and frontend simultaneously from the root directory:
```
npm start
```

This will start both servers concurrently. The backend will be available at `http://localhost:5000` and the frontend at `http://localhost:3000`.

Alternatively, you can run them separately:

1. Start the backend server:
   ```
   cd backend
   npm run dev
   ```

2. Start the frontend application:
   ```
   cd frontend
   npm start
   ```

The backend will be available at `http://localhost:5000` and the frontend at `http://localhost:3000`.

### Available Root Scripts

The root package.json includes several helpful scripts for managing the monorepo:

- `npm install` - Install dependencies for both backend and frontend
- `npm start` - Start both backend and frontend servers concurrently
- `npm run build` - Build both backend and frontend applications
- `npm test` - Run tests for both backend and frontend
- `npm run dev` - Start both backend and frontend in development mode

### Environment Variables

Create a `.env` file in the backend directory with the following variables:

```
PORT=5000
MONGO_URI=mongodb://localhost:27017/school_management
JWT_SECRET=your_jwt_secret_here
JWT_EXPIRATION=1h
```

### Database Setup

Make sure MongoDB is running on your system. If you don't have MongoDB installed, you can:

1. Download and install MongoDB from [mongodb.com](https://www.mongodb.com/try/download/community)
2. Use a cloud MongoDB service like MongoDB Atlas
3. Use Docker to run MongoDB locally

## Development

For detailed development instructions, please refer to the [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md) file.

## API Documentation

Refer to the backend README for detailed API usage instructions.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any enhancements or bug fixes.

## License

This project is licensed under the MIT License.