# OWASP-juiceshop-hax


## Welcome to the OWASP Juice Shop Walkthroughs and Tutorials

Dive deep into the world of OWASP Juice Shop with this comprehensive collection of walkthroughs and tutorials. This repository is crafted from years of hands-on experience in tackling web application vulnerabilities and honing the art of cybersecurity. Whether you're sharpening your skills or just starting out, you'll find valuable insights and detailed guidance here.

From classic exploits to the more elusive and lesser-known vulnerabilities, each guide is designed to enhance your understanding and capability. Join me as we explore the intricacies of Juice Shop, revealing the tricks of the trade and the subtle nuances that make a successful security professional.

Stay curious, stay sharp, and most importantly, enjoy the journey through one of the most celebrated and challenging web application security playgrounds.

## DOM XSS
Perform a *DOM* XSS attack with `<iframe src="javascript:alert(`xss`)">`.

### Step 1: Understand the Challenge

The challenge asks you to perform a DOM-based Cross-Site Scripting (XSS) attack using the provided payload:

HTML

```html
<iframe src="javascript:alert(`xss`)">
```

DOM XSS occurs when the client-side JavaScript code modifies the DOM based on user input in an unsafe manner, leading to script execution.

### Step 2: Identify Potential Injection Points

1. **Explore the Application**: Browse through different pages of the OWASP Juice Shop application. Look for places where user input is reflected in the DOM.
2. **Common Targets**: Check search fields, feedback forms, user profile updates, and any other areas where user data might be processed.

### Step 3: Test the Payload

1. **Locate the Vulnerable Input Field**: The exact location can vary based on the version of the Juice Shop. Some common places to try are the search bar, the feedback form, or any parameter in the URL that might be processed by JavaScript.
2. **Inject the Payload**: Paste the provided payload `<iframe src="javascript:alert(`xss`)>` into the identified input field or parameter.

### Step 4: Example Walkthrough (Using Search Bar)

1. **Navigate to the Search Bar**: In the OWASP Juice Shop, there is often a search functionality at the top of the page.
2. **Inject the Payload**: Enter the following in the search bar:
    
    ```html
    <iframe src="javascript:alert(`xss`)">
    ```
    
3. **Submit the Search**: Press enter or click the search button.

### Step 5: Observe the Results

- If the search functionality is vulnerable to DOM XSS, the payload will be executed, and you should see an alert box with the message `xss`.
- If nothing happens, try other input fields or URL parameters.

### Step 6: Verify the Challenge Completion

- The OWASP Juice Shop application will typically give you a notification or update the challenge progress once you successfully perform the DOM XSS attack.

### Troubleshooting Tips

1. **Inspect the Page**: Use the browser's developer tools (right-click on the page and select "Inspect") to see how the DOM is being manipulated by JavaScript.
2. **Test Multiple Inputs**: If one input doesn't work, try others like the feedback form, product reviews, or user settings.
3. **Check URL Parameters**: Sometimes, modifying URL parameters can trigger DOM-based XSS vulnerabilities.

### Example Using URL Parameters

1. **Navigate to a Page with URL Parameters**: For example, the product details page might have a URL like `http://your-juice-shop-url/#/product/1`.
2. **Modify the URL Parameter**: Append the payload to a parameter in the URL, such as:
    
    ```html
    http://your-juice-shop-url/#/product/1?query=<iframe src="javascript:alert(`xss`)">
    ```
    
3. `http://your-juice-shop-url/#/product/1?query=<iframe src="javascript:alert(`xss`)">`
4. **Load the Page**: Hit enter and see if the alert box appears.

By following these steps, you should be able to find a location in the OWASP Juice Shop where the DOM XSS payload is executed, thus completing the challenge. If you still encounter issues, try looking at the application source code or using a web proxy tool to inspect the requests and responses more thoroughly.

### Understanding DOM (Document Object Model)

The Document Object Model (DOM) is a programming interface for web documents. It represents the page so that programs can change the document structure, style, and content. The DOM provides a structured representation of the document as a tree of objects. Each node in this tree represents a part of the document (e.g., an element, attribute, text content).

### Key Points:

1. **Structure**: The DOM represents the HTML structure as a tree of nodes, with the document as the root node and elements like `<div>`, `<p>`, and `<a>` as child nodes.
2. **Interaction**: JavaScript can interact with and modify the DOM to dynamically change the content, style, and structure of a web page.
3. **Dynamic Updates**: Changes made to the DOM can update the user interface without needing to reload the page.

### Understanding XSS (Cross-Site Scripting)

Cross-Site Scripting (XSS) is a type of security vulnerability typically found in web applications. XSS allows attackers to inject malicious scripts into web pages viewed by other users. These scripts can then execute in the context of the victim's browser, potentially leading to data theft, session hijacking, or other malicious activities.

### Types of XSS:

1. **Stored XSS**: Also known as persistent XSS, this type occurs when malicious input is stored on the server (e.g., in a database) and then served to users. For example, if a user posts a comment containing a script, and that script is executed when others view the comment.
2. **Reflected XSS**: This type occurs when the malicious script is reflected off a web server, such as in an error message or search result, and then executed in the context of the victim's browser. It typically requires the user to click on a malicious link.
3. **DOM-based XSS**: Unlike stored and reflected XSS, DOM-based XSS occurs entirely on the client side. It happens when the web application's client-side scripts process data from an untrusted source in an unsafe way, modifying the DOM and executing malicious code.

### Detailed Explanation of Each XSS Type

### Stored XSS

1. **How It Works**:
    - Attacker submits malicious code to a website where the input is stored (e.g., comment section, user profile, message board).
    - The website later displays this input to other users, embedding the malicious script in the web page.
    - When users view the affected page, the script executes in their browsers.
2. **Example**:
    - Attacker submits a comment: `<script>alert('XSS')</script>`
    - The comment is stored in the database.
    - When other users load the page with the comment, the script runs, showing an alert.

### Reflected XSS

1. **How It Works**:
    - Attacker crafts a malicious URL containing a script.
    - Victim clicks the URL.
    - The server processes the input and reflects it back in the response (e.g., in a search result or error message).
    - The script executes in the victim's browser.
2. **Example**:
    - Malicious URL: `http://example.com/search?q=<script>alert('XSS')</script>`
    - The server includes the `q` parameter value in the response page.
    - When the victim visits the URL, the script runs, showing an alert.

### DOM-based XSS

1. **How It Works**:
    - Client-side JavaScript code dynamically updates the DOM based on user input or URL parameters.
    - If the input is not properly sanitized, it can lead to script execution.
2. **Example**:
    - URL: `http://example.com/#<script>alert('XSS')</script>`
    - JavaScript on the page reads the fragment identifier (part after `#`) and writes it to the DOM without sanitization.
    - The script executes, showing an alert.

### Preventing XSS

1. **Sanitize Input**: Always validate and sanitize user inputs both on the client side and server side.
2. **Escape Output**: Properly escape user-supplied data before including it in HTML, JavaScript, or other outputs.
3. **Content Security Policy (CSP)**: Use CSP headers to restrict sources from which scripts can be loaded.
4. **Use Security Libraries**: Utilize libraries and frameworks that automatically handle escaping and sanitization.

By understanding the types of XSS and how they can be exploited, you can better protect your web applications from these vulnerabilities. Implementing robust input validation and output escaping practices are crucial steps in securing applications against XSS attacks.
