# IIT ISM Campus Booking System - Project Flow

## 1. Project Overview
The **IIT ISM Campus Booking System** is a full-stack web application designed to streamline the reservation process for various campus facilities, including classrooms, lecture halls, and the library reading hall. It features a modern, responsive Glassmorphism UI and ensures that room allocation is handled efficiently and transparently.

## 2. Technology Stack
* **Frontend:** React.js, React Router, Lucide Icons, Date-fns, Vanilla CSS (Glassmorphism design)
* **Backend:** Node.js, Express.js
* **Database:** MongoDB (Mongoose Object Data Modeling)
* **Authentication:** JSON Web Tokens (JWT)

## 3. User Roles
The system operates using Role-Based Access Control (RBAC) with two primary roles:
1. **Standard User (Student/Faculty):** Can view available rooms, submit booking requests, modify pending requests, and cancel bookings.
2. **Administrator:** Has elevated privileges to manage the master list of rooms (add/edit/availability), view all user requests, and approve or reject pending bookings.

---

## 4. Detailed Application Flow

### Phase 1: Authentication & Onboarding
1. **Landing Page:** Users arrive at the login screen.
2. **Registration:** New users can sign up by providing their name, email, password, and role (user/admin). The backend encrypts the password and stores the user in MongoDB.
3. **Login:** Users log in with their credentials. The server verifies the credentials and issues a JWT token.
4. **Routing:** Based on the role defined in the token, the React frontend routes the user to the standard `Dashboard` or the `Admin Dashboard`.

### Phase 2: User Booking Flow (Standard User)
1. **Dashboard Overview:** The user sees a quick overview of their upcoming approved bookings and pending requests.
2. **Browsing Rooms (`/rooms`):**
   * The system fetches a list of all campus facilities from the backend.
   * Rooms are displayed as beautiful glass cards showing capacity, floor, type, and real-time availability status.
3. **Submitting a Request:**
   * The user selects a room and opens the booking modal.
   * **Dynamic Time Validation:** The system dynamically adjusts allowed booking times based on the facility. For example, the Library Reading Hall allows 24/7 booking, while standard classrooms are restricted to 5:00 AM – 10:00 PM.
   * **End Time Validation:** The UI enforces that the End Time is strictly chronologically after the Start Time.
   * The user submits the request with a purpose. The backend validates for time conflicts and saves the booking with a `pending` status.

### Phase 3: Booking Management Flow
1. **My Bookings (`/my-bookings`):**
   * The user can view the history and current status (`pending`, `approved`, `rejected`) of all their requests.
2. **Modification:** If a request is still `pending`, the user can click "Modify" to change the date, time, or purpose.
3. **Cancellation:** The user can seamlessly cancel a request using a custom confirmation modal. 

### Phase 4: Administrative Flow (Admin)
1. **Admin Dashboard (`/admin`):**
   * The admin views a high-level statistical overview of all platform activity (Pending, Approved, Rejected counts).
   * **Interactive Filtering:** The admin can click on status cards to instantly filter the list of all global requests.
2. **Approval Process:** 
   * The admin reviews pending requests, checking the user details, time slots, and purpose.
   * The admin can click **Approve** or **Reject**. The backend updates the MongoDB status, and the user's dashboard is updated in real-time.
3. **Room Management (`/admin/rooms`):**
   * The admin can add new facilities to the system (e.g., adding the Library Reading Hall).
   * The admin can toggle a room's global availability (e.g., marking a room unavailable due to maintenance), which instantly disables booking for that room on the user frontend.

---

## 5. Security & Validation Features
* **Frontend Time Logic:** Prevents selection of invalid time blocks (e.g., trying to book from 3:00 PM to 2:00 PM).
* **Backend Conflict Resolution:** Prevents double-booking by checking the database for overlapping time slots for the same room before creating or updating a request.
* **Stateless Authentication:** API routes are protected using JWT bearer tokens.
* **Cache-Busting:** Real-time data sync using `cache: "no-store"` ensures users always see the most up-to-date room availability and booking statuses.
