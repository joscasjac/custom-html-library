# Getting Started

Learn how to set up and use the StreamCraft Studios Custom HTML Library in your live broadcast graphics.

## Setup in StreamCraft Studios

Follow these steps to enable custom HTML controls in your composition:

1. **Import your composition** into StreamCraft Studios
2. **Go to Settings** → Editor Configurator
3. **Select the layer** you want to modify
4. **Change from "Overlay Editor"** to "Custom HTML"
5. **Enter your HTML URL** in the text box that appears

## Basic Implementation

Here's a minimal example to get you started:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Custom Controller</title>
    <script src="https://joscasjac.github.io/custom-html-library/iframe-client.js"></script>
</head>
<body>
    <div id="controls">
        <input type="text" id="textInput" placeholder="Enter text...">
        <button id="updateBtn">Update Graphics</button>
    </div>

    <script>
        // Initialize the client
        const client = new IframeClient("my-controller");
        
        // Handle text input changes
        document.getElementById("textInput").addEventListener("input", (e) => {
            client.setPayload({ text: e.target.value });
        });
        
        // Handle button clicks
        document.getElementById("updateBtn").addEventListener("click", () => {
            const text = document.getElementById("textInput").value;
            client.setPayload({ text, timestamp: Date.now() });
        });
    </script>
</body>
</html>
```

## Important Notes

⚠️ **Your HTML file must be hosted on a web server accessible via HTTPS.** Local files won't work due to browser security restrictions.

## Next Steps

- Learn about the [API Reference](./api-reference.md) to understand all available methods
- Check out [Examples](./examples.md) for real-world implementations
- Read [Best Practices](./best-practices.md) for tips on building great controllers
