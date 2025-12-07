# DriveHub 🚗

Github repo: https://github.com/Maruf-420-developer/DriveHub
Live Deployment: https://assignment-two-kohl-five.vercel.app/

---

## Project Overview

**DriveHub** is a Vehicle Rental Management System built with Node.js, TypeScript, and PostgreSQL. It provides a complete backend solution to manage vehicles, bookings, and users with role-based authentication.

---

## Features

- **User Management**: Register, login, and manage customer accounts.
- **Vehicle Management**: Add, update, and track vehicle availability.
- **Booking System**: Rent and return vehicles with automatic status updates.
- **Admin Controls**: Role-based access with admin privileges.
- **Automated Tasks**: Node-cron updates vehicle availability based on booking end dates.
- **Error Handling**: Global and 404 error handling middleware.
- **Security**: JWT-based authentication and role-based authorization.

---

## Technology Stack

- **Backend**: Node.js, TypeScript, Express.js
- **Database**: PostgreSQL
- **Authentication**: JWT (JSON Web Tokens)
- **Environment Management**: dotenv
- **Other Tools**: node-cron, bcrypt

---

## Project Structure

  /src
  /config
    db.ts
    index.ts
  /middleware
    auth.ts
    globalError.ts
    notFound.ts
  /modules
    /auth
      auth.controller.ts
      auth.service.ts
      auth.routes.ts
    /User
      user.controller.ts
      user.interface.ts
      user.routes.ts
      user.service.ts
    /Vehicle
      vehicle.controller.ts
      vehicle.interface.ts
      vehicle.routes.ts
      vehicle.service.ts
    /Booking
      booking.controller.ts
      booking.interface.ts
      booking.routes.ts
      booking.service.ts
      booking.utils.ts
  /router
    index.ts
  /types
    express/index.d.ts
  /utils
    buildUpdateFields.ts
    catchAsync.ts
    formatDate.ts
    getDaysBetweenDates.ts
    initAdmin.ts
  app.ts
  server.ts

Environment Variables
Create a .env file in the root:  
            CONNECTION_STRING=postgres://user:password@localhost:5432/yourdb
            PORT=5000
            JWT_SECRET=your_jwt_secret_key


API Endpoints

Auth: 
 - POST /api/v1/auth/signup – Register a new user
 - POST /api/v1/auth/signin – Login and get JWT token

Users: 
  - GET /api/v1/users – Get all users
  - PUT /api/v1/users/:userId – Update user (Admin or Self)
  - DELETE /api/v1/users/:userId – Delete user

Vehicles: 
  - POST /api/v1/vehicles – Create vehicle (Admin only)
  - GET /api/v1/vehicles – Get all vehicles
  - GET /api/v1/vehicles/:vehicleId – Get single vehicle
  - PUT /api/v1/vehicles/:vehicleId – Update vehicle (Admin only)
  - DELETE /api/v1/vehicles/:vehicleId – Delete vehicle (Admin only, not booked)

Bookings: 
  - POST /api/v1/bookings – Create booking (Admin/Customer)
  - GET /api/v1/bookings – Get bookings (Admin: all, Customer: self)
  - PUT /api/v1/bookings/:bookingId – Update booking status

Utilities & Helpers
(for-TryCatch) => catchAsync – Handles async errors in controllers
(Update-Fields) => buildUpdateFields – Dynamically build SQL update queries
(getDiffDays) => getDaysBetweenDates – Calculate number of days between two dates
(Date-format) => formatDateBD – Format date to Bangladesh timezone

initAdmin – Initialize default admin if not exists
