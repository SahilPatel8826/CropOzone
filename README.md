# CropOzone 🌾

A full-stack MERN e-commerce platform for buying and selling crops, seeds, and agricultural produce — built with a customer-facing storefront and a complete admin dashboard for managing products, orders, and users.

## Features

**Customer**
- Browse products by collection, category, and region with sorting and filtering
- Product detail pages with similar-product recommendations
- Cart with guest cart merging on login
- Checkout flow with PayPal integration
- Order placement, order history, and order detail tracking
- User registration, login, and profile management (JWT-based auth)
- Newsletter subscription

**Admin**
- Dashboard for managing products, orders, and users
- Create, edit, and delete products (with image upload via Cloudinary)
- Order management with status updates
- Role-protected admin routes

## Tech Stack

**Frontend**
- React 18 + Vite
- Redux Toolkit (state management, incl. cart and auth)
- React Router v7
- Tailwind CSS
- Axios
- PayPal React SDK
- Sonner (toast notifications)

**Backend**
- Node.js + Express 5
- MongoDB + Mongoose
- JWT for authentication
- bcryptjs for password hashing
- Multer + Cloudinary for image uploads
- CORS, dotenv

## Project Structure

```
CropOzone/
├── backend/
│   ├── config/          # Database connection
│   ├── data/            # Seed product data
│   ├── middleware/      # Auth middleware
│   ├── models/          # Mongoose schemas (User, Product, Cart, Order, Checkout, Subscriber)
│   ├── routes/          # API route handlers
│   ├── utils/           # Cloudinary config
│   ├── seed_images/     # Sample product images
│   ├── seeder.js        # Database seeding script
│   └── server.js        # App entry point
└── frontend/
    ├── src/
    │   ├── components/  # Admin, Cart, Common, Layout, Products
    │   ├── pages/       # Route-level pages
    │   ├── redux/       # Redux store and slices
    │   ├── App.jsx
    │   └── main.jsx
    └── vite.config.js
```

## Getting Started

### Prerequisites
- Node.js (v18+ recommended)
- MongoDB (local instance or a hosted URI, e.g. MongoDB Atlas)
- Cloudinary account (for image uploads)
- PayPal developer account (for checkout)

### 1. Clone the repository
```bash
git clone https://github.com/SahilPatel8826/CropOzone.git
cd CropOzone
```

### 2. Backend setup
```bash
cd backend
npm install
```

Create a `.env` file in `backend/` with the following:
```env
PORT=3000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
```

Run the server:
```bash
npm run dev      # development (nodemon)
npm start        # production
```

Optionally seed the database with sample products:
```bash
npm run seed
```

### 3. Frontend setup
```bash
cd frontend
npm install
```

Create a `.env` file in `frontend/` with:
```env
VITE_BACKEND_URL=http://localhost:3000
VITE_PAYPAL_CLIENT_ID=your_paypal_client_id
```

Run the dev server:
```bash
npm run dev
```

The frontend will be available at `http://localhost:5173` and will proxy API requests to the backend at `http://localhost:3000`.

## API Overview

| Route | Description |
|---|---|
| `/api/users` | Registration, login, profile |
| `/api/products` | Product listing, details, best-sellers, new arrivals, similar products |
| `/api/cart` | Add/update/remove cart items, merge guest cart |
| `/api/checkout` | Create checkout, mark as paid, finalize order |
| `/api/orders` | User order history and order details |
| `/api/upload` | Image upload (Cloudinary) |
| `/api/subscribe` | Newsletter subscription |
| `/api/admin/users` | Admin: manage users |
| `/api/admin/products` | Admin: manage products |
| `/api/admin/orders` | Admin: manage orders |

Most write operations and all `/api/admin/*` routes are protected by JWT auth (`protect`) and, for admin routes, an additional `admin` role check.

## License

ISC
