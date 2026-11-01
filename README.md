# Pink Ride - Women's Carpooling Platform

<p align="center">
  <img src="pink_ride/pink_ride/uploads/logo.png" alt="Pink Ride Logo" width="160" style="border-radius: 50%;">
</p>

<p align="center">
  <strong>A full-stack web application designed for female ride-sharing and passenger capacity management.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/PHP-8.x-777BB4?style=for-the-badge&logo=php&logoColor=white" alt="PHP">
  <img src="https://img.shields.io/badge/MySQL-Database-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL">
  <img src="https://img.shields.io/badge/Bootstrap-5.3-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white" alt="Bootstrap">
  <img src="https://img.shields.io/badge/Security-Sessions%20%26%20Cookies-success?style=for-the-badge" alt="Security">
</p>

---

## Overview

Pink Ride is a web application developed with PHP and MySQL to provide safe, cost-efficient ride-pooling for female commuters and university students. The platform implements role-based access to coordinate driver routes and passenger bookings.

### Core Workflow

- **Drivers:** Create travel itineraries, define pickup/drop-off points, set trip costs, and manage passenger capacity up to a 4-seat maximum per vehicle.
- **Passengers:** Query available listings through filtered route searches, inspect pricing details, and reserve available seats in real time.

---

## Technical Features

### Role-Based Access and Dashboards
- **Driver Management (`driver_dashboard.php`):** Centralized panel for publishing new routes, editing schedules, and monitoring reservations via standard CRUD operations.
- **Asynchronous User Feedback:** Implements SweetAlert2 modal dialogs for operational confirmations and status feedback.

### Security and Data Validation
- **SQL Injection Prevention:** Enforces MySQLi prepared statements (`prepare` and `bind_param`) across all parameter-dependent operations, including `edit_ride.php` and `delete_ride.php`.
- **Session and Ownership Verification:** Restricts record mutations to authorized users by cross-referencing active session identifiers (`$_SESSION['user_id']`) against resource ownership.
- **Credential Hashing:** Secures account credentials using `password_hash()` and validates authentication attempts via `password_verify()`.
- **Input Sanitization and XSS Prevention:** Escapes dynamic string outputs using `htmlspecialchars()` and validates input patterns with regular expressions prior to processing.

### Localization System
- Integrates a lightweight bilingual dictionary router (`lang.php`) supporting dynamic interface translation.
- Persists user language preferences across navigation cycles using structured HTTP cookies and session storage.

---

## Interface Previews

| User Registration & Validation | Database Schema & Records | Dynamic Ride Search & Filters |
| :---: | :---: | :---: |
| <img src="pink_ride/pink_ride/uploads/signup_preview.png" width="260" alt="Sign Up Form"> | <img src="pink_ride/pink_ride/uploads/database_preview.png" width="260" alt="Database View"> | <img src="pink_ride/pink_ride/uploads/search_preview.png" width="260" alt="Ride Booking Filters"> |

---

## Project Structure

```text
pink_ride/
├── lang.php               # Localization router and translation string dictionary
├── db_connect.php         # Database configuration and connection handler
├── index.php              # Landing page and primary search portal
├── about.php              # Application documentation and development credits
├── login.php              # Authentication endpoint with input validation
├── logout.php             # Session termination and cookie cleanup
├── driver_dashboard.php   # Route administration and trip management dashboard
├── edit_ride.php          # Interface for modifying existing trip parameters
├── delete_ride.php        # Transaction handler for trip cancellation
├── book.php               # Seat allocation and capacity decrement routine
└── pink_rides_db.sql      # Database initialization schema and relational tables
