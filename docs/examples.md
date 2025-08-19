# Examples

Real-world examples of how to use the StreamCraft Studios Custom HTML Library.

## Repository Examples

### 🕐 Clock Controller

A countdown timer with play/pause controls and live state awareness.

**Features:**
- Play/stop timer controls
- Live state indicator
- Template information display
- Debounced updates for performance

**Repository:** [https://github.com/joscasjac/pagadito-integration-ghl](https://github.com/joscasjac/pagadito-integration-ghl)

**Key Implementation:**
```javascript
// Timer functionality
function startTimer() {
    timerInterval = setInterval(() => {
        currentPayload.mainClock.value += 1000;
        updateTimeDisplay(currentPayload.mainClock.value);
        updateInputFields(currentPayload.mainClock.value);
    }, 1000);
}

// Live state awareness
client.onItemStateChanged((data) => {
    const liveIndicator = document.getElementById("liveIndicator");
    if (data.state === "live") {
        liveIndicator.classList.add("active");
    } else {
        liveIndicator.classList.remove("active");
    }
});
```

### 📝 Lower Third Controller

Simple text input controls for headline and subheadline graphics.

**Features:**
- Real-time text input
- Template metadata display
- Default value handling
- Clean, modern UI

**Repository:** [https://github.com/joscasjac/iframe-example-l3](https://github.com/joscasjac/iframe-example-l3)

**Key Implementation:**
```javascript
// Handle input changes
function handleInputChange(field, value) {
    const payload = {};
    payload[field] = value;
    debouncedUpdate(payload);
}

// Template info display
client.onSubcomposition((subcomposition) => {
    updateTemplateInfo(subcomposition);
    
    // Apply default values if available
    if (subcomposition.defaults && !currentPayload.headline) {
        currentPayload = { ...subcomposition.defaults };
        // Update UI with defaults
    }
});
```

## Common Use Cases

### Text Graphics
- **Headlines & Captions** - Dynamic text updates
- **Tickers & Crawls** - Scrolling text content
- **Social Media Feeds** - Real-time social content

### Timers & Clocks
- **Countdown Timers** - Event countdowns
- **Stopwatches** - Performance timing
- **Live Clocks** - Current time displays

### Scoreboards & Data
- **Sports Scores** - Live game statistics
- **Poll Results** - Interactive voting
- **Weather Updates** - Current conditions

### Custom Forms
- **Polls & Surveys** - Audience interaction
- **Data Entry** - Manual data input
- **Configuration Panels** - Settings controls

## Building Your Own

When creating your own custom HTML controller:

1. **Start Simple** - Begin with basic functionality
2. **Add Features Gradually** - Build complexity step by step
3. **Test in Preview** - Always test before going live
4. **Handle Errors Gracefully** - Provide fallbacks for missing data
5. **Optimize Performance** - Use debouncing and efficient updates

## Getting Help

- Check the [API Reference](./api-reference.md) for method details
- Review the [Best Practices](./best-practices.md) for tips
- Examine the repository examples for implementation patterns
- Use browser developer tools to debug communication issues
