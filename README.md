# 🛒 GreenCart - Full-Stack Grocery Delivery Application

GreenCart is a modern, responsive full-stack grocery e-commerce web application. It features a complete customer shopping experience, shopping cart management, address management, Stripe payment processing, and a dedicated seller/admin dashboard for inventory and order management.

---

## 🚀 Tech Stack

### Frontend (`client/`)
- **Framework**: React 19 + Vite
- **Styling**: Tailwind CSS
- **Routing**: React Router DOM (v7)
- **HTTP Client**: Axios
- **Notifications**: React Hot Toast

### Backend (`server/`)
- **Runtime**: Node.js & Express.js (ES Modules)
- **Database**: MongoDB (via Mongoose ODM)
- **Authentication**: JWT (JSON Web Tokens) & BcryptJS
- **Media Storage**: Cloudinary & Multer
- **Payment Processing**: Stripe API & Webhooks

---

## 📁 Project Structure

```text
greencart/
├── client/                 # React frontend application
│   ├── public/             # Static public assets
│   ├── src/
│   │   ├── assets/         # Images, icons, and asset maps
│   │   ├── components/     # UI components (Navbar, Footer, ProductCard, etc.)
│   │   ├── context/        # App context and global state management
│   │   ├── pages/          # Customer & Seller views
│   │   └── main.jsx        # App entry point
│   ├── .env.example        # Frontend environment variables template
│   └── package.json
│
├── server/                 # Express REST API backend
│   ├── configs/            # Database, Cloudinary, and Multer configurations
│   ├── controllers/        # Route controllers (user, seller, product, cart, order)
│   ├── middlewares/        # Authentication middlewares (user and seller)
│   ├── models/             # Mongoose schemas (User, Product, Order, Address)
│   ├── routes/             # API endpoints
│   ├── .env.example        # Backend environment variables template
│   ├── server.js           # Server entry point
│   └── package.json
│
├── .gitignore              # Git ignore rules for node_modules and .env files
└── README.md               # Project documentation
```

---

## 🛠️ Prerequisites

Ensure you have the following installed on your machine:
- **Node.js** (v18.x or later recommended): [Download Node.js](https://nodejs.org/en/download/)
- **npm** (comes with Node.js)
- **MongoDB Atlas** account (or local MongoDB): [Register for MongoDB Atlas](https://www.mongodb.com/cloud/atlas/register)
- **Cloudinary** account (for product image hosting): [Register for Cloudinary](https://cloudinary.com/users/register_free)
- **Stripe** account *(Optional: only needed for online card payments)*: [Stripe Dashboard](https://dashboard.stripe.com/login)

---

## ⚙️ Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/PRABHAT00007/greencart.git
cd greencart
```

---

### 2. Backend Setup (`server`)

1. Navigate to the server folder:
   ```bash
   cd server
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file from the example template:
   ```bash
   cp .env.example .env
   ```
   *(On Windows PowerShell: `Copy-Item .env.example .env`)*

4. Configure your `.env` variables:
   ```env
   # Server Port & Secrets
   JWT_SECRET=your_jwt_secret_key
   NODE_ENV=development

   # Admin / Seller Credentials
   SELLER_EMAIL=admin@example.com
   SELLER_PASSWORD=your_secure_password

   # MongoDB Connection
   MONGODB_URI=your_mongodb_connection_string

   # Cloudinary Setup (for uploading product images)
   CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
   CLOUDINARY_API_KEY=your_cloudinary_api_key
   CLOUDINARY_API_SECRET=your_cloudinary_api_secret

   # Stripe Setup (Optional for online payments)
   STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key
   STRIPE_SECRET_KEY=your_stripe_secret_key
   STRIPE_WEBHOOK_SECRET=your_stripe_webhook_secret
   ```

5. Start the backend development server:
   ```bash
   npm run server
   ```
   The server will start running on `http://localhost:4000`.

---

### 3. Frontend Setup (`client`)

1. Open a new terminal and navigate to the client directory:
   ```bash
   cd client
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file:
   ```bash
   cp .env.example .env
   ```
   *(On Windows PowerShell: `Copy-Item .env.example .env`)*

4. Configure the client `.env` variables:
   ```env
   VITE_CURRENCY = '$'
   VITE_BACKEND_URL = "http://localhost:4000"
   ```

5. Start the frontend development server:
   ```bash
   npm run dev
   ```
   The Vite client will launch (typically at `http://localhost:5173`).

---

## ✨ Key Features

- **Customer Experience**:
  - Browse grocery items by category (Vegetables, Fruits, Dairy, Bakery, Beverages, etc.)
  - Search and filter products
  - Interactive shopping cart with quantity controls
  - Save and manage multiple delivery addresses
  - Cash on Delivery (COD) and Stripe card payment options
  - Order tracking and detailed order history
- **Seller & Admin Portal**:
  - Dedicated seller dashboard login
  - Add new products with multi-image upload via Cloudinary
  - Manage product inventory and pricing
  - View incoming orders and update delivery statuses (Placed, Packed, Shipped, Delivered)

---

## 🚢 Deployment (Vercel)

Both the frontend and backend include pre-configured `vercel.json` files for seamless deployment on Vercel.

### Deploy Backend:
1. Connect your GitHub repository to [Vercel](https://vercel.com/).
2. Set the root directory to `server`.
3. Add the environment variables from your `server/.env` (set `NODE_ENV = production`).
4. Deploy to obtain your production backend URL.

### Deploy Frontend:
1. Create a new project on Vercel pointing to the same repository.
2. Set the root directory to `client`.
3. Add `VITE_BACKEND_URL` pointing to your deployed backend URL.
4. Deploy the frontend application.
5. In `server/server.js`, ensure the deployed frontend domain is included in the allowed CORS origins.
