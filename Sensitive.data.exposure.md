## Sensitive Data Exposure - Confidential Document" challenge in the OWASP Juice Shop.

### Step-by-Step Walkthrough

### Step 1: Understand the Challenge

The challenge is to access a confidential document within the Juice Shop application. This often involves finding and accessing a file or endpoint that contains sensitive information which should not be publicly accessible.

### Step 2: Explore the Application

1. **Browse Different Pages**: Go through various sections of the Juice Shop, including the home page, admin sections, and user profiles.
2. **Inspect Elements**: Use your browser's developer tools to inspect elements and look for hidden or commented-out URLs that might point to sensitive documents.

### Step 3: Use Developer Tools

1. **Open Developer Tools**: Right-click on the page and select "Inspect" or press `F12`.
2. **Check Network Tab**: Monitor network requests to see if any files are being loaded that look like they could contain sensitive data.

### Step 4: Look for Clues in the Application

1. **Look for Suspicious Links or Files**: Sometimes, the Juice Shop has links or files hidden in the source code.
2. **Check Robots.txt**: Navigate to `http://your-juice-shop-url/robots.txt`. This file often contains paths to files or directories that are intended to be hidden from search engines.

### Step 5: Common Paths and Files

OWASP Juice Shop sometimes uses predictable paths for sensitive documents. Here are some paths to try:

1. **Check `/ftp` directory**:
    - Navigate to `http://your-juice-shop-url/ftp`.
    - Look for any files listed in the directory.
2. **Check for `/admin` directory**:
    - Navigate to `http://your-juice-shop-url/admin`.
    - See if there are any accessible files or directories.

### Step 6: Try Specific URL Paths

1. **Accessing the Confidential Document**:
    - Navigate to `http://your-juice-shop-url/ftp/legal.md`.
    - This file often contains a legal document that is part of the sensitive data exposure challenge.
2. **Alternative Path**:
    - Navigate to `http://your-juice-shop-url/ftp/acquisitions.md`.

### Step 7: Verify the Challenge Completion

- Once you access the correct confidential document, the Juice Shop application will typically provide a notification or update the challenge progress indicating that you have completed the challenge.

### Detailed Example

1. **Navigate to the Juice Shop Application**: Open your Juice Shop application in your web browser.
2. **Check `robots.txt`**:
    - Open `http://your-juice-shop-url/robots.txt`.
    - Look for disallowed paths like `/ftp` or `/admin`.
3. **Access Potential Confidential Documents**:
    - Go to `http://your-juice-shop-url/ftp/legal.md`.
    - If that doesn't work, try `http://your-juice-shop-url/ftp/acquisitions.md`.
4. **Verify**:
    - Once you open one of these files, look for the notification from the Juice Shop indicating that the challenge is complete.

### Example URL Paths:

- `http://your-juice-shop-url/ftp/legal.md`
- `http://your-juice-shop-url/ftp/acquisitions.md`

By following these steps, you should be able to locate and access a confidential document, thereby completing the "Sensitive Data Exposure - Confidential Document" challenge in the OWASP Juice Shop. 
