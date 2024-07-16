### SQL Injection OWASP Juice Shop Walkthrough
----
### Step 1: Understand the Challenge

The goal is to bypass the login authentication and gain access to the administrator's account using an SQL injection attack.

### Step 2: Navigate to the Login Page

1. **Open the Juice Shop Application**: Start your Juice Shop application in your web browser.
2. **Find the Login Page**: Navigate to the login page by clicking on the "Login" button in the navigation bar.

### Step 3: Understand SQL Injection Basics

SQL Injection (SQLi) involves inserting or "injecting" SQL queries into input fields to manipulate the database. For a login form, you want to craft an input that will bypass the password check and grant access.

### Step 4: Craft the SQL Injection Payload

1. **Typical SQL Injection Payloads**: For login forms, common payloads include:
    - `admin' OR 1=1--`
    - `admin' --`
    - `admin' OR '1'='1`
2. **Explanation**: These payloads work by injecting a condition that is always true (e.g., `1=1`), effectively bypassing the password check.

### Step 5: Perform the Injection

1. **Enter the Payload in the Email Field**:
    - In the email field, enter: `admin' OR 1=1--`
2. **Password Field**: The password can be anything because the payload should bypass the password check.
3. **Submit the Form**: Click the "Log in" button.

### Step 6: Verify the Injection Worked

- If successful, you will be logged in as the administrator. The application should provide access to the admin interface, and you might see a notification confirming the challenge completion.

### Detailed Walkthrough with Screenshots

1. **Navigate to the Login Page**:
    - Open `http://your-juice-shop-url`.
    - Click on "Login" in the navigation bar.
2. **Enter the SQL Injection Payload**:
    - **Email Field**: Type `admin' OR 1=1--`
    - **Password Field**: Type any password, for example, `password123`.
3. **Submit the Form**:
    - Click the "Log in" button.
4. **Result**:
    - If the payload is successful, you should be logged in as the administrator.
    - The Juice Shop application will typically show a notification indicating that you have completed the "Login Admin" challenge.

### Troubleshooting Tips

- **Check for Errors**: If you are not logged in, check for any error messages. Sometimes the application may sanitize inputs or show specific error messages that can provide clues.
- **Try Different Payloads**: If the first payload doesn't work, try variations like:
    - `admin' --`
    - `admin' OR '1'='1`
- **Inspect Network Requests**: Use developer tools (F12) to inspect network requests and see how the input is being processed.

### Example with Developer Tools

1. **Open Developer Tools**:
    - Right-click on the page and select "Inspect" or press F12.
    - Go to the "Network" tab to monitor requests.
2. **Submit the Login Form**:
    - Enter `admin' OR 1=1--` in the email field and any password.
    - Click "Log in".
    - Check the network request to see if the payload was sent correctly.

By following these steps, you should be able to log in as the administrator using SQL injection and complete the "Injection - Login Admin" challenge in the OWASP Juice Shop.
