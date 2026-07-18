# 🦷 Dental Health – Modern Dental Clinic Web Application

[![Live Demo](https://img.shields.io/badge/Demo-Live%20Website-brightgreen?style=for-the-badge&logo=netlify)](https://dental-hc.netlify.app/)
[![React Version](https://img.shields.io/badge/React-19.2.7-61DAFB?style=for-the-badge&logo=react)](https://react.dev/)
[![Express Version](https://img.shields.io/badge/Express-5.2-000000?style=for-the-badge&logo=express)](https://expressjs.com/)
[![MongoDB Mongoose](https://img.shields.io/badge/MongoDB-Mongoose-47A248?style=for-the-badge&logo=mongodb)](https://mongoosejs.com/)

A premium, state-of-the-art web application designed for a dental clinic, focusing on luxurious visual aesthetics, fluid page transitions, buttery-smooth animations, and a seamless full-stack booking system.

**🔗 Explore the live deployment here:** [https://dental-hc.netlify.app/](https://dental-hc.netlify.app/)

---

## ✨ Features & Architecture

### 🎨 Visual & Frontend Excellence
*   **Awwwards-Grade Scrolling:** Integrated with **Lenis** momentum scrolling, delivering an ultra-smooth, floaty viewport experience.
*   **GSAP & ScrollTrigger Animations:** Dynamic entry reveals, staggered text masking, and interactive scroll-linked animations powered by the GreenSock library.
*   **Unique UI Elements:** Includes custom masked cards (which shift the background image focal point relative to scroll/element position), magnetic buttons, and a customizable cursor simulation.
*   **Full Responsiveness:** Tailored and polished for desktop, tablet, and mobile displays, featuring an elegant, responsive mobile navigation overlay.

### ⚙️ Production-Ready Backend
*   **Restful API Architecture:** Scalable Node.js & Express server hosting clean API routes.
*   **MongoDB & Mongoose Database:** Robust schemas for managing appointments and contact inquiries with indexes optimized for slot availability checks.
*   **Automated Email Confirmations:** Integrated with **Nodemailer** to dispatch stylized, rich HTML confirmation emails to patients immediately upon booking a slot.
*   **Centralized Error Handling:** Global middleware wrapper catching and formatting all endpoint errors gracefully.

---

## 🛠️ Tech Stack

| Domain | Technologies |
| :--- | :--- |
| **Core Frontend** | React 19, TypeScript, Vite, React Router v7 |
| **Styling** | Tailwind CSS, Autoprefixer, PostCSS |
| **Animations** | GSAP, ScrollTrigger, Lenis Smooth Scroll |
| **Core Backend** | Node.js, Express (v5.2) |
| **Database** | MongoDB, Mongoose |
| **Services** | Nodemailer (SMTP Email Client), CORS, Dotenv |

---

## 📂 Project Structure

```text
├── backend/                  # Node.js + Express Backend Server
│   ├── config/               # Database connection settings
│   │   └── db.js             # Mongoose/MongoDB initialization
│   ├── controllers/          # Route controller functions (appointments, contacts)
│   ├── middleware/           # Custom Express middleware (errorHandler, etc.)
│   ├── models/               # MongoDB Mongoose schemas (Appointment, Contact)
│   ├── routes/               # API route definitions (appointmentRoutes, contactRoutes)
│   ├── services/             # Third-party integrations
│   │   └── emailService.js   # Nodemailer email configuration & HTML templates
│   ├── server.js             # Main server entrypoint
│   └── .env.example          # Sample environment variables
│
├── src/                      # React Frontend Application
│   ├── components/           # Reusable UI components (MagneticButton, CustomCursor, PremiumFooter, etc.)
│   ├── pages/                # Page views (Home, About, Services, Appointment, Contact, Gallery)
│   ├── App.tsx               # Root component with routing and Lenis setup
│   └── main.tsx              # Application entry point
│
├── public/                   # Static assets (images, logos)
├── package.json              # Main project scripts and dependencies
└── README.md                 # Project documentation
```

---

## 🚀 Setup & Installation

Follow these steps to run the complete stack locally.

### Prerequisites
*   [Node.js](https://nodejs.org/) installed (v18 or higher recommended)
*   A running [MongoDB](https://www.mongodb.com/) instance (local or Atlas cloud cluster)

### 1. Clone & Install Dependencies
First, clone the repository and install dependencies in the root directory:
```bash
git clone https://github.com/AmanMishra107/dental-health.git
cd dental-health
npm install
```

Next, navigate into the `backend` folder and install server dependencies:
```bash
cd backend
npm install
cd ..
```

### 2. Environment Configuration
Create a `.env` file in the `/backend` directory. Fill in the following environment variables:
```env
PORT=5000
MONGODB_URI=your_mongodb_connection_string

# Clinic settings
CLINIC_NAME="Dental Health"

# SMTP Email Configuration (Nodemailer)
EMAIL_HOST=smtp.mailtrap.io
EMAIL_PORT=587
EMAIL_USER=your_smtp_username
EMAIL_PASS=your_smtp_password
EMAIL_FROM="Dental Health" <no-reply@dentalhealth.com>
```

### 3. Running the Application (Local Development)

You can launch both the frontend and backend simultaneously or run them separately.

#### Option A: Unified Dev (Vite + Express)
From the root directory, run the unified start command:
```bash
npm run dev:all
```
*Note: This command uses windows shell syntax to kick off both servers concurrently (`start /B node backend/server.js && vite`).*

#### Option B: Standalone Run
If running on a non-Windows OS or in separate terminal windows:
*   **Start the Backend server** (Runs on port `5000`):
    ```bash
    npm run server
    ```
*   **Start the Frontend server** (Runs on port `5173`):
    ```bash
    npm run dev
    ```

---

## 📡 API Endpoints Reference

The backend exposes the following endpoints (default base URL: `http://localhost:5000`):

### 📅 Appointment Manager (`/api/appointments`)
*   `POST /api/appointments` - Creates a new appointment booking. Automatically dispatches confirmation email upon success.
*   `GET /api/appointments` - Lists all booked appointments.
*   `GET /api/appointments/:id` - Fetches details of a specific appointment.
*   `PUT /api/appointments/:id` - Updates appointment details (e.g. status changes).
*   `DELETE /api/appointments/:id` - Deletes a booked appointment.

### ✉️ Contact & Inquiries (`/api/contact`)
*   `POST /api/contact` - Submits a client inquiry/contact form.
*   `GET /api/contact` - Retrieves a list of all inquiry submissions.
*   `GET /api/contact/:id` - Fetches a specific inquiry.
*   `DELETE /api/contact/:id` - Deletes a specific inquiry.

### 🩺 Health & Server Status
*   `GET /api/health` - Simple check verifying database connectivity and server status.

---

## 📦 Production Build & Deployment

### Build the Frontend
To compile a static production build of the Vite React application:
```bash
npm run build
```
The production bundle will be output to the `/dist` directory, ready to be served by static hosts like Netlify, Vercel, or AWS S3.

### Deploy the Backend
Deploy the `backend` Node server to platforms such as Heroku, Render, Railway, or DigitalOcean, making sure to configure the `.env` variables on the host dashboard.
