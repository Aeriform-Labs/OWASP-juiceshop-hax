### Challenge: Provoke an error that is neither very gracefully nor consistently handled
----
### Objective

Provoke an error situation that is not handled gracefully by the server and reveals sensitive information such as stack traces or SQL query strings.

### Steps to Complete the Challenge

### Method 1: Triggering an Error via an Invalid URL

1. **Launch Juice Shop:**
    - Start your OWASP Juice Shop application. Typically, you can access it via `http://localhost:3000`.
2. **Navigate to an Invalid Endpoint:**
    - Open your browser and visit `http://localhost:3000/rest/qwertz`.
    - This endpoint does not exist, which will cause the server to throw an error.
3. **Observe the Error:**
    - The server will return a 500 Internal Server Error.
    - The error page will display a stack trace and other sensitive information which should not be exposed.

### Method 2: Triggering an SQL Error via Login Form

1. **Open the Login Page:**
    - Navigate to the login page of Juice Shop, typically found at `http://localhost:3000/#/login`.
2. **Enter Malicious Input:**
    - In the Email field, enter a single quote (`'`).
    - In the Password field, enter any string (e.g., `password`).
3. **Submit the Form:**
    - Click on the login button.
4. **Observe the Error:**
    - The login attempt will fail, and an error message will appear.
    - Open the browser's Developer Tools (usually by pressing `F12` or right-clicking the page and selecting "Inspect").
    - Go to the Console tab.
    - You will see an error message indicating an SQL error. The message may expose parts of the SQL query being executed, which is a security risk.

### Explanation

### Why These Methods Work

- **Invalid Endpoint:** By navigating to an endpoint that doesn’t exist, you force the server to handle a request it cannot process. Instead of gracefully handling the error, the server exposes sensitive debugging information, which is a security flaw.
- **SQL Error:** Entering a single quote in the login form is a common way to provoke SQL injection vulnerabilities. If the input is not properly sanitized, the backend will attempt to execute a malformed SQL query, leading to an error. This reveals how the application handles unexpected input and exposes internal implementation details.

### Importance of Handling Errors Gracefully

- Applications should handle errors gracefully by displaying generic error messages to the user and logging detailed error information securely on the server side.
- Exposing stack traces and SQL queries can provide attackers with valuable information about the application’s internal workings, making it easier to exploit other vulnerabilities.
