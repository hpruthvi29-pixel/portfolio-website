# Personal Portfolio Website

A modern, production-ready MERN stack portfolio website with admin dashboard, dark mode, and responsive design.

## Features

- Modern UI with Tailwind CSS and Framer Motion animations
- Dark/Light mode with system preference detection
- Fully responsive design (mobile, tablet, desktop)
- Dynamic project management with CRUD operations
- Admin dashboard with JWT authentication
- Contact form with MongoDB storage
- Project search, filter, and pagination
- Resume download and preview section
- Typing animation in hero section
- Lazy-loaded components for optimal performance
- Toast notifications for user feedback
- SEO optimized with meta tags

## Tech Stack

| Layer    | Technology                     |
| -------- | ------------------------------ |
| Frontend | React, Vite, Tailwind CSS, Framer Motion, React Router |
| Backend  | Node.js, Express.js            |
| Database | MongoDB, Mongoose ODM          |
| Auth     | JWT, bcrypt                    |
| Uploads  | Multer                         |
| Security | Helmet, CORS, Rate Limiting    |

## Project Structure

```
portfolio-website/
├── client/              # React frontend
│   ├── public/
│   ├── src/
│   │   ├── components/  # Reusable UI components
│   │   ├── pages/       # Page components
│   │   ├── layouts/     # Layout wrappers
│   │   ├── context/     # React context providers
│   │   ├── services/    # API service functions
│   │   ├── styles/      # Global styles
│   │   ├── App.jsx      # Root component with routing
│   │   └── main.jsx     # Entry point
│   └── ...config files
├── server/              # Express backend
│   ├── config/          # Database configuration
│   ├── controllers/     # Route controllers
│   ├── middleware/       # Auth, error, validation middleware
│   ├── models/          # Mongoose schemas
│   ├── routes/          # API route definitions
│   ├── utils/           # Helper utilities
│   ├── app.js           # Express app setup
│   └── server.js        # Entry point
├── .gitignore
├── package.json         # Root scripts
└── README.md
```

## Installation

### Prerequisites

- Node.js 18+
- MongoDB Atlas account (or local MongoDB)
- Git

### Clone & Setup

```bash
git clone https://github.com/yourusername/portfolio-website.git
cd portfolio-website
npm run install:all
```

### Environment Variables

Create `server/.env`:

```env
PORT=5000
NODE_ENV=development
MONGO_URI=mongodb+srv://<user>:<password>@cluster.mongodb.net/portfolio?retryWrites=true&w=majority
JWT_SECRET=your_jwt_secret_key_change_in_production
JWT_EXPIRE=7d
ADMIN_EMAIL=admin@portfolio.com
ADMIN_PASSWORD=Admin@123
FRONTEND_URL=http://localhost:5173
```

### Run Locally

```bash
# Run backend (http://localhost:5000)
npm run server:dev

# Run frontend (http://localhost:5173)
npm run client

# Run both concurrently
npm run dev
```

### Build for Production

```bash
npm run client:build
```

## API Documentation

### Authentication

| Method | Endpoint         | Description    | Auth Required |
| ------ | ---------------- | -------------- | ------------- |
| POST   | `/api/auth/login` | Admin login    | No            |
| GET    | `/api/auth/me`    | Get admin info | Yes           |

### Projects

| Method | Endpoint              | Description          | Auth Required |
| ------ | --------------------- | -------------------- | ------------- |
| GET    | `/api/projects`       | Get all projects     | No            |
| GET    | `/api/projects/:id`   | Get single project   | No            |
| POST   | `/api/projects`       | Create project       | Yes           |
| PUT    | `/api/projects/:id`   | Update project       | Yes           |
| DELETE | `/api/projects/:id`   | Delete project       | Yes           |

Query params for GET `/api/projects`: `page`, `limit`, `category`, `search`, `featured`, `status`

### Contact

| Method | Endpoint              | Description          | Auth Required |
| ------ | --------------------- | -------------------- | ------------- |
| POST   | `/api/contact`        | Send message         | No            |
| GET    | `/api/contact`        | Get messages         | Yes           |
| DELETE | `/api/contact/:id`    | Delete message       | Yes           |

## Deployment

### Frontend → Vercel

1. Push code to GitHub
2. Import `client` folder as a new Vercel project
3. Set build command: `npm run build`
4. Set output directory: `dist`
5. Add environment variable for production API URL

### Backend → Render

1. Create a new Web Service on Render
2. Connect GitHub repository
3. Set root directory: `server`
4. Build command: `npm install`
5. Start command: `npm start`
6. Add environment variables from `.env`

### Database → MongoDB Atlas

1. Create a free cluster on MongoDB Atlas
2. Create a database user
3. Get connection string and add to server `.env`
4. Whitelist Render/Vercel IP addresses or allow all (0.0.0.0/0 for development)

## Admin Panel

Navigate to `/admin/login` and sign in with:

- Email: `admin@portfolio.com`
- Password: `Admin@123`

The admin panel allows you to:
- View dashboard statistics
- Create, edit, and delete projects
- Upload project images
- View and delete contact messages

## Pages

- **Home** - Hero with typing animation, featured projects
- **About** - Profile, timeline, achievements
- **Skills** - Categorized skills with animated progress bars
- **Projects** - Search, filter, pagination, project cards
- **Resume** - Download resume, certifications, achievements
- **Contact** - Contact form with validation
- **Admin** - Dashboard, project CRUD, message management

## Security

- Passwords hashed with bcrypt (12 salt rounds)
- JWT authentication with token expiry
- Input validation and sanitization
- Helmet for secure HTTP headers
- CORS configured for frontend origin
- Rate limiting on API routes
- File type validation for uploads
- NoSQL injection prevention

## Performance

- React.lazy for code splitting
- Image lazy loading
- Component memoization
- Paginated API responses
- Optimized MongoDB queries
- Gzip compression

## License

MIT
