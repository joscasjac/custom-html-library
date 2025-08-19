# API Reference

Complete reference for all methods and events in the StreamCraft Studios Custom HTML Library.

## IframeClient Constructor

Creates a new iframe client instance for communication with StreamCraft Studios.

```javascript
const client = new IframeClient(iframeId);
```

### Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `iframeId` | string | A unique identifier for your iframe instance |

## Core Methods

### setPayload(payload)

Sends data to StreamCraft Studios to update your graphics.

```javascript
client.setPayload({ text: "Hello World", color: "red" });
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `payload` | object | Data object to send to StreamCraft |

### getPayload()

Requests the current payload data from StreamCraft Studios.

```javascript
client.getPayload();
```

**Returns:** Nothing (data is received via event listener)

### getSubcomposition()

Requests template and composition metadata from StreamCraft.

```javascript
client.getSubcomposition();
```

**Returns:** Nothing (data is received via event listener)

### destroy()

Cleans up event listeners when the iframe is unloaded.

```javascript
client.destroy();
```

**Note:** Always call this in your `unload` event handler.

## Event Listeners

### onInitialData(callback)

Fired when the iframe first loads with initial data.

```javascript
client.onInitialData((data) => {
    console.log('Initial data:', data);
    // data.payload contains the current payload
    // data.metadata contains composition information
});
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `callback` | function | Function called with initial data |

### onItemStateChanged(callback)

Fired when the graphics state changes (preview/live).

```javascript
client.onItemStateChanged((data) => {
    if (data.state === 'live') {
        console.log('Graphics are now live!');
    } else {
        console.log('Graphics are in preview mode');
    }
});
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `callback` | function | Function called with state change data |

**Callback receives:** `{ state: 'live' | 'preview' }`

### onSubcomposition(callback)

Fired when subcomposition data is received.

```javascript
client.onSubcomposition((subcomposition) => {
    console.log('Template name:', subcomposition.name);
    console.log('Template ID:', subcomposition.id);
});
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `callback` | function | Function called with subcomposition data |

## Message Types

The library uses these internal message types for communication:

| Message Type | Direction | Description |
|--------------|-----------|-------------|
| `INITIALIZE` | → | Sent when iframe client starts |
| `SET_PAYLOAD` | → | Send data to StreamCraft |
| `GET_PAYLOAD` | → | Request current data |
| `GET_SUBCOMPOSITION` | → | Request template info |
| `INITIAL_DATA` | ← | Received initial data |
| `ITEM_STATE_CHANGED` | ← | State change notification |

## Complete Example

```javascript
// Initialize client
const client = new IframeClient("my-controller");

// Listen for initial data
client.onInitialData((data) => {
    console.log('Connected to StreamCraft');
    if (data.payload) {
        // Update UI with existing data
        updateUI(data.payload);
    }
});

// Listen for state changes
client.onItemStateChanged((data) => {
    updateLiveIndicator(data.state);
});

// Listen for template info
client.onSubcomposition((template) => {
    displayTemplateInfo(template);
});

// Send updates
function updateGraphics(newData) {
    client.setPayload(newData);
}

// Cleanup
window.addEventListener('unload', () => {
    client.destroy();
});
```
