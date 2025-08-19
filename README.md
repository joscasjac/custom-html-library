# StreamCraft Studios Custom HTML Library

A JavaScript library for building custom UI controls in StreamCraft Studios live broadcast graphics.

## Overview

This library enables communication between custom HTML interfaces and StreamCraft Studios through iframe messaging. It allows you to create custom controls for specific layers in your composition instead of using the default overlay editor.



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



## Examples

- **[Clock Controller](https://github.com/joscasjac/pagadito-integration-ghl)** - Countdown timer with play/pause controls
- **[Lower Third Controller](https://github.com/joscasjac/iframe-example-l3)** - Text input controls for headlines

## Setup in StreamCraft Studios

1. Import your composition into StreamCraft Studios
2. Go to Settings → Editor Configurator
3. Select the layer you want to modify
4. Change from "Overlay Editor" to "Custom HTML"
5. Enter your HTML URL in the text box that appears





