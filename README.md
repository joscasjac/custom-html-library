# StreamCraft Studios Custom HTML Library

A JavaScript library for building custom UI controls in StreamCraft Studios live broadcast graphics.

## Overview

This library enables communication between custom HTML interfaces and StreamCraft Studios through iframe messaging. It allows you to create custom controls for specific layers in your composition instead of using the default overlay editor.

## Features

- **Real-time Communication**: Bidirectional messaging between your custom UI and StreamCraft
- **Payload Management**: Send and receive data to control your graphics
- **State Awareness**: Know when your graphics are live or in preview mode
- **Template Information**: Access metadata about your composition and templates
- **Easy Integration**: Simple API that works with any HTML/CSS/JavaScript framework

## Quick Start

1. Include the library in your HTML:
```html
    <script src="https://joscasjac.github.io/custom-html-library/iframe-client.js"></script>
```

2. Initialize the client:
```javascript
const client = new IframeClient("my-controller");
```

3. Send data to update graphics:
```javascript
client.setPayload({ text: "Hello World" });
```

## Documentation

📖 **Documentation is now built with GitBook for easier maintenance!**

The documentation includes:
- Getting Started guide
- Complete API reference
- Real-world examples
- Best practices and tips

**Setup GitBook:**
1. Follow the [GitBook Setup Guide](./GITBOOK_SETUP.md)
2. Connect your GitHub repository to GitBook
3. Your docs will be automatically generated from markdown files

## Examples

- **[Clock Controller](https://github.com/joscasjac/pagadito-integration-ghl)** - Countdown timer with play/pause controls
- **[Lower Third Controller](https://github.com/joscasjac/iframe-example-l3)** - Text input controls for headlines

## Setup in StreamCraft Studios

1. Import your composition into StreamCraft Studios
2. Go to Settings → Editor Configurator
3. Select the layer you want to modify
4. Change from "Overlay Editor" to "Custom HTML"
5. Enter your HTML URL in the text box that appears

## GitBook Setup

This repository is now configured for GitBook documentation, which is much simpler to maintain than GitHub Pages.

### Quick Setup

1. Follow the [GitBook Setup Guide](./GITBOOK_SETUP.md)
2. Connect your GitHub repository to GitBook
3. Your documentation will be automatically generated from markdown files

### Benefits of GitBook

- ✅ **Simple Markdown** - Write in easy-to-read markdown
- ✅ **Automatic Navigation** - Table of contents from SUMMARY.md
- ✅ **Search Functionality** - Full-text search across all content
- ✅ **Responsive Design** - Works on all devices
- ✅ **Free Hosting** - GitBook.com provides free hosting

## File Structure

```
custom-html-library/
├── book.json              # GitBook configuration
├── SUMMARY.md             # Table of contents
├── README.md              # Introduction page
├── docs/                  # Documentation files
│   ├── getting-started.md
│   ├── api-reference.md
│   ├── examples.md
│   └── best-practices.md
├── iframe-client.js       # Your library file
└── GITBOOK_SETUP.md       # GitBook setup guide
```

## Development

To work on the documentation locally:

1. Clone the repository
2. Open `index.html` in your browser
3. Make changes and refresh to see updates
4. Commit and push changes to trigger GitHub Pages rebuild

## Contributing

Feel free to submit issues, feature requests, or pull requests to improve the documentation or library.

## License

This project is part of StreamCraft Studios. Please refer to your StreamCraft Studios license agreement for usage terms.

## Support

For technical support with StreamCraft Studios, please contact your system administrator or refer to the official StreamCraft Studios documentation.
