# Laravel User Authentication System

A comprehensive **user authentication system** built with Laravel featuring custom authentication (without external packages), profile management with file uploads, and protected routes using middleware.

---

## Features

### Authentication System
- **User Registration**: Custom registration with name, email, and password validation.
- **User Login**: Secure login using Laravel's built-in `Auth::attempt()`.
- **User Logout**: Session management with `Auth::logout()`.
- **Route Protection**: Auth middleware protecting dashboard and profile routes.

### Profile Management
- **Profile Creation**: 8-field form with text inputs, file upload, and validation.
- **Image Upload**: Profile image handling with file validation (max 2MB, jpg/png).
- **Profile Display**: Individual profile view with uploaded images.
- **Profile List**: Browse all user profiles with thumbnail previews.

### Technical Highlights
- Custom authentication implementation (no Breeze/Jetstream).
- File upload with proper validation and storage.
- CSRF protection on all forms.
- Server-side validation with error handling.
- Bootstrap 5 responsive UI.
- Eloquent ORM with proper relationships.

---

## Requirements

- PHP 8.1 or higher
- Composer
- MySQL or SQLite
- Node.js and npm (for asset compilation)

---

## Installation

### 1. Clone the Repository
git clone <https://github.com/Wrong1234/user-authentication>
cd laravel-user-auth

### 2. Install Dependencies
composer install   
npm install       

### 3. Environment Configuration
cp .env.example .env
php artisan key:generate

### 4. Database Configuration

- Edit .env file:

- DB_CONNECTION=mysql
- DB_HOST=127.0.0.1
- DB_PORT=3306
- DB_DATABASE=rajinsoft
- DB_USERNAME=root
- DB_PASSWORD=

### 5. Database Setup
- php artisan migrate
- php artisan storage:link

### 6. File Permissions
- chmod -R 755 storage
- chmod -R 755 bootstrap/cache

### 7. Asset Compilation
npm run dev       

### 8. Start Development Server
php artisan serve


Visit http://localhost:8000 to access the application.


---
## Database Schema
### Users Table

- id (Primary Key)
- name (String)
- email (String, Unique)
- password (String, Hashed)
- created_at, updated_at (Timestamps)

### Profiles Table

- id (Primary Key)
- user_id (Foreign Key → users.id)
- full_name (String)
- email (String)
- phone (String)
- address (String)
- bio (Text)
- profile_image (String - file path)
- hobbies (String)
- date_of_birth (Date)
- created_at, updated_at (Timestamps)
## Add project images
- ![Dashboard](https://github.com/Wrong1234/user-authentication/blob/fea68e676a69d9587d0e9590fdaa35dfad7020f4/public/images/Laravel%20-%20Google%20Chrome%208_14_2025%2011_41_40%20AM.png) 
- ![Create Profile](https://github.com/Wrong1234/user-authentication/blob/fea68e676a69d9587d0e9590fdaa35dfad7020f4/public/images/Laravel%20-%20Google%20Chrome%208_14_2025%2011_42_14%20AM.png)
- ![All Profiles](https://github.com/Wrong1234/user-authentication/blob/fea68e676a69d9587d0e9590fdaa35dfad7020f4/public/images/Laravel%20-%20Google%20Chrome%208_14_2025%2011_42_25%20AM.png)
- ![Show Profile](https://github.com/Wrong1234/user-authentication/blob/fea68e676a69d9587d0e9590fdaa35dfad7020f4/public/images/Laravel%20-%20Google%20Chrome%208_14_2025%2011_42_37%20AM.png)
- ![User Registration](https://github.com/Wrong1234/user-authentication/blob/fea68e676a69d9587d0e9590fdaa35dfad7020f4/public/images/Laravel%20-%20Google%20Chrome%208_14_2025%2011_43_03%20AM.png)
- ![User Login](https://github.com/Wrong1234/user-authentication/blob/fea68e676a69d9587d0e9590fdaa35dfad7020f4/public/images/Laravel%20-%20Google%20Chrome%208_14_2025%2011_43_12%20AM.png)
## Usage & Testing
---
### Testing Authentication

### Registration

- Navigate to /register
- Fill in: name, email, password, password_confirmation
- Validation ensures unique email and 8+ character password
- Successful registration redirects to login


### Login

- Go to /login
- Enter registered email and password
- Successful login redirects to /dashboard
- Invalid credentials show error message


### Logout

- Click "Logout" from dashboard
- Session cleared, redirected to login page



### Testing Profile System
---
### Create Profile

- Login first (required by auth middleware)
- Navigate to profile creation form
- Fill all 8 required fields:

- Full Name (text)
- Email (email format)
- Phone (text)
- Address (text)
- Bio (textarea)
- Profile Image (jpg/png, max 2MB)
- Hobbies (text)
- Date of Birth (date)


## Submit to store in database


### View Profile

- Access your submitted profile data
- See uploaded image and all form fields
- Images stored in public/storage/profiles/


### Browse Profiles

- View list of all user profiles
- See name, email, phone, and image thumbnails
- Click to view full profile details



### Protected Routes

- /dashboard - Requires authentication
- /profiles/* - All profile routes require authentication
- Unauthenticated access redirects to login
