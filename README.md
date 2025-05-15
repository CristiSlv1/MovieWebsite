# Movie Application

A full-stack movie application with user authentication, movie management, and advanced user activity monitoring.

## Features

- �� Movie browsing and management
- 👤 User authentication and authorization
- ⭐ Movie reviews and ratings
- 🔍 Advanced search and filtering
- 📊 Genre statistics
- 🔒 User activity monitoring system
- 📝 Activity logging
- 🚨 Suspicious activity detection

## Tech Stack

### Backend
- Node.js with Express
- TypeScript
- PostgreSQL with TypeORM
- JWT Authentication
- WebSocket for real-time updates

### Frontend
- React
- TypeScript
- Tailwind CSS
- Modern UI/UX design

## Prerequisites

- Node.js (v14 or higher)
- PostgreSQL (v12 or higher)
- npm or yarn

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd movie-app
```

2. Install backend dependencies:
```bash
cd backend
npm install
```

3. Install frontend dependencies:
```bash
cd frontend
npm install
```

4. Configure the database:
- Create a PostgreSQL database named `movies_db`
- Update the database configuration in `backend/src/data-source.ts` if needed

## Configuration

1. Backend Environment Variables:
Create a `.env` file in the backend directory:
```env
JWT_SECRET=your-secret-key
DB_HOST=localhost
DB_PORT=5432
DB_USERNAME=postgres
DB_PASSWORD=your-password
DB_NAME=movies_db
```

2. Frontend Environment Variables:
Create a `.env` file in the frontend directory:
```env
REACT_APP_API_URL=http://localhost:3001
```

## Running the Application

1. Start the backend server:
```bash
cd backend
npm run dev
```

2. Start the frontend development server:
```bash
cd frontend
npm start
```

The application will be available at:
- Frontend: http://localhost:3000
- Backend: http://localhost:3001

## User Activity Monitoring

The application includes a sophisticated user activity monitoring system with two levels of detection:

### Basic Monitoring
- Runs every 60 seconds
- Flags users with more than 5 total actions
- Stores monitored users in memory
- No time window restriction

### Advanced Monitoring
- Runs every hour
- Flags users with more than 100 actions within the last hour
- Updates the `isMonitored` flag in the database
- Has a time window restriction (only looks at last hour's actions)

### Testing the Monitoring System

You can test the monitoring system using the provided simulation script:
```bash
cd backend
npx ts-node src/scripts/simulateSuspiciousActivity.ts
```

## API Endpoints

### Authentication
- `POST /api/register` - Register a new user
- `POST /api/login` - Login user
- `GET /api/user` - Get current user info

### Movies
- `GET /api/movies` - Get all movies (with pagination)
- `GET /api/movies/:id` - Get movie by ID
- `POST /api/movies` - Create new movie (admin only)
- `PUT /api/movies/:id` - Update movie (admin only)
- `DELETE /api/movies/:id` - Delete movie (admin only)

### Reviews
- `GET /api/movies/:id/reviews` - Get reviews for a movie
- `POST /api/movies/:id/reviews` - Add a review

### Monitoring
- `GET /api/monitored-users` - Get list of monitored users (admin only)

## Project Structure
    movie-app/
    ├── backend/
    │ ├── src/
    │ │ ├── entities/ # Database entities
    │ │ ├── routes/ # API routes
    │ │ ├── services/ # Business logic
    │ │ ├── monitoring/ # Monitoring system
    │ │ ├── scripts/ # Utility scripts
    │ │ └── data-source.ts # Database configuration
    │ └── package.json
    └── frontend/
    ├── src/
    │ ├── components/ # React components
    │ ├── pages/ # Page components
    │ ├── services/ # API services
    │ └── App.tsx # Main application component
    └── package.json


## Security Features

- JWT-based authentication
- Role-based access control (User/Admin)
- User activity monitoring
- Suspicious activity detection
- Secure password hashing
- Protected API endpoints

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- TypeORM for database management
- Express.js for the backend framework
- React for the frontend framework
- Tailwind CSS for styling