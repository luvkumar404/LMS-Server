# LMS Server

This is the backend server for a Learning Management System (LMS). It provides APIs for managing users, courses, lectures, course progress, and payments.

## Features

*   User authentication and authorization
*   Course creation, retrieval, and management
*   Lecture creation and management within courses
*   Tracking user progress through courses
*   Payment integration with Stripe and Razorpay
*   File uploads for course thumbnails and user avatars

## Getting Started

### Prerequisites

*   Node.js and npm installed
*   MongoDB database
*   Cloudinary account for media storage
*   Stripe and/or Razorpay account for payment processing

### Installation

1.  Clone the repository:
    ```bash
    git clone https://github.com/luvkumar404/LMS-Server.git
    ```
2.  Install the dependencies:
    ```bash
    npm install
    ```
3.  Create a `.env` file in the root directory and add the following environment variables (refer to `env.example`):
    ```
    PORT=5000
    MONGO_URI=<your_mongodb_uri>
    JWT_SECRET=<your_jwt_secret>
    CLOUDINARY_CLOUD_NAME=<your_cloudinary_cloud_name>
    CLOUDINARY_API_KEY=<your_cloudinary_api_key>
    CLOUDINARY_API_SECRET=<your_cloudinary_api_secret>
    STRIPE_SECRET_KEY=<your_stripe_secret_key>
    STRIPE_WEBHOOK_SECRET=<your_stripe_webhook_secret>
    RAZORPAY_KEY_ID=<your_razorpay_key_id>
    RAZORPAY_KEY_SECRET=<your_razorpay_key_secret>
    CORS_ORIGIN=*
    ```
4.  Start the server:
    ```bash
    npm run dev
    ```

The server will be running on `http://localhost:5000`.

## API Endpoints

### Health

*   `GET /api/health`: Check the health of the server.

### User

*   `POST /api/users/signup`: Create a new user account.
*   `POST /api/users/signin`: Authenticate a user.
*   `POST /api/users/signout`: Sign out a user.
*   `GET /api/users/profile`: Get the current user's profile.
*   `PATCH /api/users/profile`: Update the current user's profile.
*   `PATCH /api/users/change-password`: Change the user's password.
*   `DELETE /api/users/account`: Delete the user's account.

### Course

*   `GET /api/courses/published`: Get all published courses.
*   `GET /api/courses/search`: Search for courses.
*   `POST /api/courses`: Create a new course (instructor only).
*   `GET /api/courses`: Get all courses created by the instructor.
*   `GET /api/courses/c/:courseId`: Get the details of a course.
*   `PATCH /api/courses/c/:courseId`: Update the details of a course (instructor only).
*   `GET /api/courses/c/:courseId/lectures`: Get all lectures for a course.
*   `POST /api/courses/c/:courseId/lectures`: Add a new lecture to a course (instructor only).

### Course Progress

*   `GET /api/progress/:courseId`: Get the user's progress for a course.
*   `PATCH /api/progress/:courseId/lectures/:lectureId`: Update the user's progress for a lecture.
*   `PATCH /api/progress/:courseId/complete`: Mark a course as completed.
*   `PATCH /api/progress/:courseId/reset`: Reset the user's progress for a course.

### Course Purchase

*   `POST /api/purchase/checkout/create-checkout-session`: Initiate a Stripe checkout session.
*   `POST /api/purchase/webhook`: Handle Stripe webhooks.
*   `GET /api/purchase/course/:courseId/detail-with-status`: Get the purchase status of a course.
*   `GET /api/purchase`: Get all purchased courses for the user.

### Razorpay

*   `POST /api/razorpay/create-order`: Create a Razorpay order.
*   `POST /api/razorpay/verify-payment`: Verify a Razorpay payment.

### Media

*   `POST /api/media/upload-video`: Upload a video file.

## Technologies Used

*   **Node.js**: JavaScript runtime environment
*   **Express**: Web framework for Node.js
*   **MongoDB**: NoSQL database
*   **Mongoose**: ODM for MongoDB
*   **JSON Web Token (JWT)**: For authentication
*   **Bcryptjs**: For password hashing
*   **Multer**: For handling file uploads
*   **Cloudinary**: For cloud-based image and video management
*   **Stripe**: For payment processing
*   **Razorpay**: For payment processing
*   **Express Validator**: For request validation
*   **Helmet**: For securing HTTP headers
*   **HPP**: For preventing HTTP Parameter Pollution
*   **Express Rate Limit**: For rate limiting requests
*   **Express Mongo Sanitize**: For sanitizing user-supplied data to prevent MongoDB operator injection
*   **xss-clean**: For preventing cross-site scripting (XSS) attacks
*   **cors**: For enabling Cross-Origin Resource Sharing
*   **dotenv**: For managing environment variables
*   **morgan**: For logging HTTP requests
*   **nodemon**: For automatically restarting the server during development
