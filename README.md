# Blog App

A full-stack **Blog Application** built using **Node.js, Express, MongoDB, and EJS**. The application allows users to create, edit, delete, and view blog posts with authentication and authorization features.

## Features
- **User Authentication**: Users can register, login, and manage their blogs securely.
- **CRUD Operations**: Create, read, update, and delete blog posts.
- **Image Uploads**: Supports uploading images via Cloudinary.
- **Comments & Reviews**: Users can leave comments on blog posts.
- **Flash Messages**: Provides success and error notifications.
- **Session Management**: Secure session handling with MongoDB store.
- **Error Handling**: Centralized error handling for better debugging.

## Tech Stack
- **Backend**: Node.js, Express.js, MongoDB, Mongoose
- **Frontend**: EJS, Bootstrap, JavaScript
- **Authentication**: Passport.js (Local Strategy)
- **File Storage**: Cloudinary API
- **Session Store**: MongoDB with `connect-mongo`

## Installation

### Prerequisites
Make sure you have the following installed:
- **Node.js** (v14 or later)
- **MongoDB** (Local or MongoDB Atlas)
- **Cloudinary Account** (for image uploads)

### Setup
1. **Clone the Repository**
   ```sh
   git clone https://github.com/yourusername/blog-app.git
   cd blog-app
   ```
2. **Install Dependencies**
   ```sh
   npm install
   ```
3. **Set Up Environment Variables**
   Create a `.env` file in the root directory and add the following:
   ```env
   ATLASDB_URL=your_mongodb_connection_string
   SECRET=your_session_secret
   CLOUD_NAME=your_cloudinary_name
   CLOUD_API_KEY=your_cloudinary_api_key
   CLOUD_API_SECRET=your_cloudinary_api_secret
   ```
4. **Start the Server**
   ```sh
   npm start
   ```
   The server will start at **http://localhost:8080**.

## Project Structure
```
blog-app/
│-- models/           # Mongoose schemas (User, Blog, Review)
│-- routes/           # Express routes (blog, user, review)
│-- views/            # EJS templates
│-- public/           # Static files (CSS, JS, images)
│-- middleware.js     # Middleware functions
│-- cloudConfig.js    # Cloudinary configuration
│-- app.js            # Main server file
│-- .env              # Environment variables
│-- package.json      # Dependencies and scripts
│-- README.md         # Project documentation
```

## API Endpoints
| Method | Route                      | Description |
|--------|----------------------------|-------------|
| GET    | `/`                         | Redirects to blogs |
| GET    | `/blogs`                    | List all blogs |
| GET    | `/blogs/:id`                | Show blog details |
| POST   | `/blogs`                    | Create new blog (Authenticated) |
| PUT    | `/blogs/:id`                | Edit blog (Owner only) |
| DELETE | `/blogs/:id`                | Delete blog (Owner only) |
| POST   | `/blogs/:id/reviews`        | Add a review |
| DELETE | `/blogs/:id/reviews/:reviewId` | Delete a review (Author only) |
| GET    | `/register`                 | Show register form |
| POST   | `/register`                 | Register new user |
| GET    | `/login`                    | Show login form |
| POST   | `/login`                    | Authenticate user |
| GET    | `/logout`                   | Logout user |

## Security Measures
- **Authentication & Authorization**: Passport.js for secure login and role-based access control.
- **Session Management**: Sessions are securely stored in MongoDB.
- **Input Validation**: JOI validation to prevent malformed data.
- **Error Handling**: Centralized error handling for better debugging.
