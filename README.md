# User Authentication System Using Zustand

## Description

This repository implements a mid-level user authentication system for the frontend using Zustand as the state management library and Axios for API interactions. The system includes essential authentication features like signup, login, logout, email verification, password reset, and session management. It also supports error handling and loading states for a smooth user experience. The authentication state is synchronized with the backend through API calls, and cookies are used to manage sessions securely.

---

## Features

- **Signup**: Allows users to register by providing their email, password, and name.
- **Login**: Users can log in with valid credentials to access protected features.
- **Logout**: Logs users out and clears authentication data.
- **Email Verification**: Validates users’ email addresses using a verification code.
- **Check Authentication**: Verifies if the user is already authenticated upon application load.
- **Forgot Password**: Sends a password reset email to the user.
- **Reset Password**: Enables users to reset their password using a token.
- **Error Handling**: Captures errors and displays user-friendly messages.
- **Loading States**: Displays a loading indicator during asynchronous operations.

---

## API Endpoints

- **Base URL**:
  - Development: `http://localhost:5000/api/auth`
  - Production: `/api/auth`

### Endpoints:

- `POST /signup` - Registers a new user.
- `POST /login` - Logs in an existing user.
- `POST /logout` - Logs out the current user.
- `POST /verify-email` - Verifies the user’s email.
- `GET /check-auth` - Checks the user’s authentication status.
- `POST /forgot-password` - Sends a password reset email.
- `POST /reset-password/:token` - Resets the password using a token.

---

## Flow of User Authentication

1. **Signup Flow**:

   - User provides email, password, and name.
   - The system sends these details to the backend API.
   - If successful, the user is logged in and their data is saved in the state.

2. **Login Flow**:

   - User enters email and password.
   - System authenticates the credentials with the backend.
   - On success, user details are saved in the state and the user is marked as authenticated.

3. **Logout Flow**:

   - User clicks the logout button.
   - The frontend sends a logout request to the backend and clears local state.

4. **Email Verification**:

   - User receives a verification code via email.
   - They input the code into the application.
   - The system verifies the code with the backend.

5. **Session Validation (Check Auth)**:

   - On app load, the frontend checks with the backend if the user is authenticated.
   - If authenticated, user details are fetched and stored in the state.

6. **Password Recovery**:

   - **Forgot Password**: User provides email, and the system sends a reset password link.
   - **Reset Password**: User sets a new password using the reset link and token.

---

## State Management (Zustand)

The entire authentication flow is managed through a Zustand store with the following structure:

```javascript
{
  user: null, // Holds user details if authenticated
  isAuthenticated: false, // Tracks if the user is authenticated
  error: null, // Captures error messages
  isLoading: false, // Indicates loading state during API calls
  isCheckingAuth: true, // Verifies if the user is already logged in
  message: null, // Stores success messages
  
  // Functions for authentication actions
  signup,
  login,
  logout,
  verifyEmail,
  checkAuth,
  forgotPassword,
  resetPassword
}
```

---

## Installation and Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/azzayshakya/Frontend_Auth.git
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Configure the API URL:

   - Update `API_URL` in the code to match your backend's URL.

4. Start the development server:

   ```bash
   npm run dev
   ```

5. Access the application at `http://localhost:3000`.

---

## Usage

1. **Signup**: Navigate to the signup page and register a new account.
2. **Login**: Use the login page to authenticate.
3. **Protected Routes**: Ensure authentication to access restricted pages.
4. **Forgot Password**: Recover the account using the forgot password feature.
5. **Check Session**: Refresh the page to test persistent sessions.

---

## Technologies Used

- **Frontend**: React, Zustand
- **HTTP Client**: Axios
- **Backend Integration**: RESTful API

---

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch:
   ```bash
   git checkout -b feature-name
   ```
3. Commit your changes:
   ```bash
   git commit -m "Add feature-name"
   ```
4. Push to your branch:
   ```bash
   git push origin feature-name
   ```
5. Open a pull request.

---

