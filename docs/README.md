# StreamCraft Studios Custom HTML Library

Welcome to the StreamCraft Studios Custom HTML Library documentation! This library allows you to create custom UI controls for specific layers in your composition, giving you full control over your live broadcast graphics.

## 🚀 Quick Start

1. **Include the library** in your HTML:
```html
<script src="https://joscasjac.github.io/custom-html-library/iframe-client.js"></script>
```

2. **Initialize the client**:
```javascript
const client = new IframeClient("my-controller");
```

3. **Send data** to update your graphics:
```javascript
client.setPayload({ text: "Hello World" });
```

## 📚 What You'll Learn

- [Getting Started](./getting-started.md) - Set up your first custom HTML controller
- [API Reference](./api-reference.md) - Complete method documentation
- [Examples](./examples.md) - Real-world implementation examples
- [Best Practices](./best-practices.md) - Tips for building great controllers

## 🎯 Key Features

- **Real-time Communication** - Bidirectional messaging with StreamCraft
- **Payload Management** - Send and receive data to control graphics
- **State Awareness** - Know when graphics are live or in preview
- **Template Information** - Access composition metadata
- **Easy Integration** - Works with any HTML/CSS/JavaScript framework

## 🔗 Library URL

The library is hosted at: `https://joscasjac.github.io/custom-html-library/iframe-client.js`

---

*Ready to build amazing custom graphics controllers? Let's get started!*
