# Full-Stack Todo Application

A modern todo application built with React, Node.js, Express, and MongoDB.

## Features

- ✅ Create, read, update, and delete todos
- 🔍 Search and filter functionality
- 💾 MongoDB persistence with proper date handling
- 🎨 Beautiful, responsive UI with Tailwind CSS
- ⚡ Real-time updates
- 🔄 Error handling and loading states

## Tech Stack

### Frontend
- **React 18** with TypeScript
- **Tailwind CSS** for styling
- **Axios** for API calls
- **Lucide React** for icons
- **Vite** for development and building

### Backend
- **Node.js** with Express
- **MongoDB** with Mongoose ODM
- **CORS** for cross-origin requests
- **dotenv** for environment variables

## Prerequisites

Before running this application, make sure you have:

1. **Node.js** (v16 or higher)
2. **MongoDB** installed and running locally
   - Download from: https://www.mongodb.com/try/download/community
   - Default connection: `mongodb://localhost:27017`

## Installation & Setup

### 1. Install Dependencies

```bash
# Install frontend dependencies
npm install

# Install backend dependencies
cd server
npm install
cd ..
```

### 2. Start MongoDB

Make sure MongoDB is running on your system:

```bash
# On macOS with Homebrew
brew services start mongodb-community

# On Windows (if installed as service)
net start MongoDB

# Or run manually
mongod
```

### 3. Environment Configuration

The server is pre-configured with these default settings in `server/.env`:
- Port: 5000
- MongoDB URI: `mongodb://localhost:27017/todoapp`
- Environment: development

### 4. Start the Application

You have several options to run the application:

#### Option 1: Run both frontend and backend together
```bash
npm run dev:full
```

#### Option 2: Run separately
```bash
# Terminal 1 - Start backend server
npm run dev:server

# Terminal 2 - Start frontend
npm run dev
```

### 5. Access the Application

- **Frontend**: http://localhost:5173
- **Backend API**: http://localhost:5000
- **Health Check**: http://localhost:5000/api/health

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/todos` | Get all todos |
| POST | `/api/todos` | Create a new todo |
| PUT | `/api/todos/:id` | Update a todo |
| DELETE | `/api/todos/:id` | Delete a todo |
| DELETE | `/api/todos/completed/all` | Delete all completed todos |
| GET | `/api/health` | Server health check |

## Database Schema

```javascript
{
  _id: ObjectId,
  text: String (required),
  completed: Boolean (default: false),
  createdAt: Date (default: now),
  updatedAt: Date (auto-updated)
}
```

## Project Structure

```
├── src/                    # Frontend React application
│   ├── components/         # React components
│   ├── hooks/             # Custom React hooks
│   ├── services/          # API service layer
│   ├── types/             # TypeScript type definitions
│   └── App.tsx            # Main application component
├── server/                # Backend Node.js application
│   ├── models/            # Mongoose models
│   ├── routes/            # Express routes
│   ├── .env               # Environment variables
│   └── server.js          # Main server file
└── README.md
```

## Development Tips

1. **MongoDB Connection Issues**: Ensure MongoDB is running and accessible at `mongodb://localhost:27017`
2. **CORS Issues**: The backend is configured to accept requests from `http://localhost:5173`
3. **Port Conflicts**: Change ports in `.env` (backend) or `vite.config.ts` (frontend) if needed
4. **Data Persistence**: All todos are stored in MongoDB and will persist between sessions

## Troubleshooting

### Common Issues

1. **"Failed to load todos"**
   - Check if MongoDB is running
   - Verify backend server is running on port 5000
   - Check network connectivity

2. **"ECONNREFUSED" errors**
   - Ensure MongoDB service is started
   - Check if ports 5000 and 5173 are available

3. **CORS errors**
   - Verify the frontend is running on port 5173
   - Check CORS configuration in `server/server.js`

### MongoDB Commands

```bash
# Connect to MongoDB shell
mongosh

# Show databases
show dbs

# Use the todo database
use todoapp

# Show collections
show collections

# View all todos
db.todos.find()

# Clear all todos
db.todos.deleteMany({})
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is open source and available under the MIT License.