---

# 🏫 Campus Booking System (Facility Management)

A fully functional and secure campus facility booking app developed using the **MERN stack**. The Campus Booking System features user authentication, a premium glassmorphism UI, real-time room availability, and a comprehensive admin dashboard—enhancing the way students and faculty reserve campus spaces. The app offers an intuitive interface for seamless browsing, booking, and management.

---

## 🌟 Commands for Running the App

- ⚛️ **npm run build**  
  Used for building the optimized React app for production. 

- ⚛️ **npm start**  
  (Frontend) After navigating into the client directory (`cd client`), run this command to start the React frontend in development mode.

- ⚛️ **nodemon server.js**  
  (Backend) Run this in the root directory to activate the backend server and connect the MongoDB database to the React app.

- 🚀 **node server.js**  
  (Production) Used in deployment environments like Render. Render will run this automatically via the start command.

---

## 🌟 Features

- ⚛️ **Tech Stack:** React.js, MongoDB, Node.js, Express, Pure CSS (Glassmorphism UI)
- 🔐 **Authentication:** Secure login and registration using JSON Web Tokens (JWT) and bcrypt for encrypted password storage. Anyone registering as `admin@admin.com` receives Admin rights automatically.
- 📅 **Smart Booking:** Strict time validations prevent overlapping bookings and ensure end times are after start times
- 🛠️ **Admin Dashboard:** Administrators can effortlessly approve, reject, or manage all pending booking requests
- 🏫 **Room Management:** Admins can dynamically add new rooms or edit existing facility details
- 💬 **My Bookings:** Students and staff can view their past and upcoming bookings, and cancel them if needed
- 🌐 **Cloud Deployed:** Fully hosted with an automated CI/CD pipeline using Vercel (Frontend) and Render (Backend)

---

## 🛠️ Tech Stack

- **Frontend:** React.js, Vanilla CSS
- **Backend:** Node.js, Express.js
- **Database:** MongoDB Atlas
