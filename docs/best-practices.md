# Best Practices

Tips and guidelines for building great custom HTML controllers with the StreamCraft Studios library.

## Performance

### Debounce Updates
Use debouncing for input fields to avoid excessive API calls:

```javascript
let updateTimeout = null;

function debouncedUpdate(payload) {
    if (updateTimeout) {
        clearTimeout(updateTimeout);
    }
    updateTimeout = setTimeout(() => {
        client.setPayload(payload);
    }, 100); // Wait 100ms after last keystroke
}
```

### Batch Changes
Group multiple changes into a single payload update when possible:

```javascript
// Good: Single update
client.setPayload({
    headline: "New Headline",
    subheadline: "New Subheadline",
    timestamp: Date.now()
});

// Avoid: Multiple updates
client.setPayload({ headline: "New Headline" });
client.setPayload({ subheadline: "New Subheadline" });
```

### Cleanup Resources
Always clean up when your iframe is unloaded:

```javascript
window.addEventListener('unload', () => {
    if (updateTimeout) {
        clearTimeout(updateTimeout);
    }
    if (timerInterval) {
        clearInterval(timerInterval);
    }
    client.destroy();
});
```

## User Experience

### Live Indicators
Show users when graphics are live vs. preview mode:

```javascript
client.onItemStateChanged((data) => {
    const indicator = document.getElementById('liveIndicator');
    if (data.state === 'live') {
        indicator.classList.add('live');
        indicator.textContent = 'LIVE';
    } else {
        indicator.classList.remove('live');
        indicator.textContent = 'Preview';
    }
});
```

### Input Validation
Validate user input before sending to StreamCraft:

```javascript
function validateAndSend(data) {
    if (data.text && data.text.length > 0) {
        if (data.text.length <= 100) { // Max length check
            client.setPayload(data);
        } else {
            showError('Text too long (max 100 characters)');
        }
    } else {
        showError('Please enter some text');
    }
}
```

### Loading States
Provide feedback during data operations:

```javascript
function updateGraphics(data) {
    const button = document.getElementById('updateBtn');
    button.disabled = true;
    button.textContent = 'Updating...';
    
    client.setPayload(data);
    
    // Re-enable after a short delay
    setTimeout(() => {
        button.disabled = false;
        button.textContent = 'Update Graphics';
    }, 1000);
}
```

### Responsive Design
Ensure your interface works on different screen sizes:

```css
/* Mobile-first approach */
.controls {
    padding: 15px;
    max-width: 100%;
}

@media (min-width: 768px) {
    .controls {
        padding: 30px;
        max-width: 600px;
    }
}
```

## Error Handling

### Fallback Values
Provide default values for missing data:

```javascript
client.onInitialData((data) => {
    const payload = data.payload || {};
    const headline = payload.headline || 'Default Headline';
    const subheadline = payload.subheadline || 'Default Subheadline';
    
    updateUI({ headline, subheadline });
});
```

### Graceful Degradation
Handle cases where StreamCraft data is unavailable:

```javascript
let isConnected = false;

client.onInitialData((data) => {
    isConnected = true;
    updateConnectionStatus('Connected');
});

// Fallback for offline mode
if (!isConnected) {
    updateConnectionStatus('Offline Mode');
    enableOfflineFeatures();
}
```

### User Feedback
Inform users when operations fail:

```javascript
function showError(message) {
    const errorDiv = document.getElementById('errorMessage');
    errorDiv.textContent = message;
    errorDiv.style.display = 'block';
    
    setTimeout(() => {
        errorDiv.style.display = 'none';
    }, 5000);
}
```

## Security

### Data Validation
Always validate and sanitize data received from StreamCraft:

```javascript
function sanitizeInput(input) {
    if (typeof input !== 'string') return '';
    return input.replace(/<script\b[^<]*(?:(?!<\/script>)<[^<]*)*<\/script>/gi, '');
}

client.onInitialData((data) => {
    if (data.payload && data.payload.text) {
        const safeText = sanitizeInput(data.payload.text);
        document.getElementById('textInput').value = safeText;
    }
});
```

### Never Execute Arbitrary Code
Avoid using `eval()` or similar functions with received data:

```javascript
// ❌ Dangerous - Never do this
eval(data.payload.code);

// ✅ Safe - Use proper DOM methods
document.getElementById('content').textContent = data.payload.text;
```

## Testing

### Preview Mode
Always test in preview mode before going live:

```javascript
client.onItemStateChanged((data) => {
    if (data.state === 'preview') {
        console.log('Testing in preview mode');
        // Enable test features
    } else if (data.state === 'live') {
        console.log('Now live - disable test features');
        // Disable test features
    }
});
```

### Browser Compatibility
Test across different browsers and devices:

- Chrome, Firefox, Safari, Edge
- Desktop and mobile devices
- Different screen resolutions

### Performance Monitoring
Monitor your controller's performance:

```javascript
const startTime = performance.now();

client.setPayload(data);

const endTime = performance.now();
console.log(`Payload update took ${endTime - startTime} milliseconds`);
```

## Code Organization

### Modular Structure
Organize your code into logical functions:

```javascript
// UI updates
function updateUI(data) {
    updateHeadline(data.headline);
    updateSubheadline(data.subheadline);
    updateTimestamp(data.timestamp);
}

// Event handlers
function handleInputChange(field, value) {
    const payload = { [field]: value };
    debouncedUpdate(payload);
}

// StreamCraft communication
function initializeStreamCraft() {
    client.onInitialData(handleInitialData);
    client.onItemStateChanged(handleStateChange);
    client.onSubcomposition(handleTemplateInfo);
}
```

### Consistent Naming
Use clear, consistent naming conventions:

```javascript
// Good
const headlineInput = document.getElementById('headline');
const updateButton = document.getElementById('updateBtn');

// Avoid
const input1 = document.getElementById('headline');
const btn = document.getElementById('updateBtn');
```

Following these best practices will help you create robust, user-friendly, and maintainable custom HTML controllers!
