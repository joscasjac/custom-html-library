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

## Development vs Production

### Local Development
✅ **Localhost works perfectly** for testing and development  
✅ **No hosting required** during development  
✅ **Use browser developer tools** to debug and test  
✅ **Fast iteration** - just refresh your browser  

### Production (StreamCraft Studios)
⚠️ **Your HTML file needs to be accessible** via a web server  
✅ **Can be localhost** (if StreamCraft can access it)  
✅ **Can be GitHub Pages** (recommended for public use)  
✅ **Can be any web hosting service**  

## Testing Locally

1. **Save your HTML file** with the library included
2. **Open in browser** (localhost works fine)
3. **Test functionality** using browser developer tools
4. **Debug and iterate** quickly
5. **Deploy when ready** to StreamCraft Studios

## Next Steps

- Learn about the [API Reference](./api-reference.md) to understand all available methods
- Check out [Examples](./examples.md) for real-world implementations
- Read [Best Practices](./best-practices.md) for tips on building great controllers
