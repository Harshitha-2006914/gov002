# GovBot - Developer Customization Guide

This guide helps developers extend and customize the GovBot chatbot for government helpdesk services.

---

## 📁 Project Structure

```
hfc/
├── index.html              # Main application (HTML + CSS + JavaScript)
├── README.md               # Project documentation
├── ENHANCEMENTS.md         # Feature enhancement details
├── TESTING_CHECKLIST.md    # Comprehensive testing guide
└── DEVELOPER_GUIDE.md      # This file
```

---

## 🏗️ Code Architecture

### Global Variables
```javascript
let currentLanguage = 'en'          // Active language (en/kn)
let chatStarted = false             // Chat session state
let isVoiceRecording = false        // Voice recording state
let currentMenu = null              // Current menu context
```

### Key Functions

#### Language & Init
- `selectLanguage(lang)` - Handle language selection
- `startChat()` - Initialize chat session
- `resetChat()` - Clear chat and return to welcome

#### Message Display
- `addBotMessage(text)` - Show bot message in bubble
- `addUserMessage(text)` - Show user message in bubble
- `showMainMenu()` - Display main menu with 4 buttons

#### Query Handling (NEW)
- `sendMessage()` - Parse user input and route to handlers
- `handleSalaryQuery()` - Salary status response
- `handlePensionQuery()` - Pension status response
- `handleLeaveQuery()` - Leave balance response
- `handleFileQuery()` - File tracking response
- `handleUnknownQuery()` - Fallback response

#### UI Controls
- `toggleAdminDashboard()` - Show/hide admin panel
- `toggleVoiceInput()` - Voice recording simulation
- `handleEscalate()` - Escalation flow
- `openEscalationModal()` / `closeModal()` - Modal control

---

## 🔧 Customization Scenarios

### Scenario 1: Add New Keyword & Response

**Step 1:** Add keywords to detection
```javascript
// In sendMessage() function, add new condition:
} else if (
    lowerText.includes('sick') || 
    lowerText.includes('medical') ||
    lowerText.includes('health')
) {
    handleMedicalQuery();
}
```

**Step 2:** Create handler function
```javascript
function handleMedicalQuery() {
    addBotMessage("Medical leave must be supported by a doctor's certificate.\n\nDo you want to upload documentation?");
    setTimeout(() => showMainMenu(), 1200);
}
```

**Step 3:** Add menu button (optional)
```javascript
// In showMainMenu(), add to options array:
{ key: 'medicalQuery', label: 'Medical Leave 🏥' }

// In handleMenuSelection():
} else if (key === 'medicalQuery') {
    setTimeout(() => {
        handleMedicalQuery();
    }, 600);
}
```

---

### Scenario 2: Create Custom Response Card

```javascript
function handleCustomQuery() {
    const messageDiv = document.createElement('div');
    messageDiv.className = 'message bot';
    
    const bubble = document.createElement('div');
    bubble.className = 'bubble';
    
    // Add custom HTML
    const card = document.createElement('div');
    card.style.background = 'var(--bg-light)';
    card.style.padding = '12px';
    card.style.borderRadius = '8px';
    card.style.marginBottom = '12px';
    card.innerHTML = `
        <strong>Custom Information</strong><br>
        Your custom data here
    `;
    bubble.appendChild(card);
    
    // Add any other content
    const text = document.createElement('div');
    text.textContent = "Additional message";
    bubble.appendChild(text);
    
    messageDiv.appendChild(bubble);
    
    const timestamp = document.createElement('div');
    timestamp.className = 'timestamp';
    timestamp.textContent = new Date().toLocaleTimeString([], { 
        hour: '2-digit', 
        minute: '2-digit' 
    });
    messageDiv.appendChild(timestamp);
    
    messagesContainer.appendChild(messageDiv);
    messagesContainer.scrollTop = messagesContainer.scrollHeight;
}
```

---

### Scenario 3: Add New Language Support

**Step 1:** Add language object to `messages`
```javascript
const messages = {
    en: { /* existing */ },
    kn: { /* existing */ },
    hi: {  // Hindi
        welcome: "नमस्कार 👋 GovBot में आपका स्वागत है!",
        mainMenu: "कृपया चुनें कि आपको क्या चाहिए:",
        salaryStatus: "वेतन स्थिति 💰",
        // ... add all messages
    }
};
```

**Step 2:** Add button to language selection
```javascript
// In HTML, add button to language-selection div:
<button class="lang-btn" onclick="selectLanguage('hi')">हिन्दी</button>
```

---

### Scenario 4: Modify Color Scheme

```javascript
// In CSS :root section, change variables:
:root {
    --primary-blue: #1E40AF;      // Custom primary
    --light-blue: #3B82F6;        // Custom light
    --accent-blue: #2563EB;       // Custom accent
    --success-green: #10B981;     // Custom green
    --warning-orange: #F59E0B;    // Custom orange
    /* ... update other colors */
}
```

---

### Scenario 5: Add Action After Message

```javascript
function handleQueryWithAction() {
    addBotMessage("Your request is being processed...");
    
    setTimeout(() => {
        addBotMessage("✅ Request processed successfully!");
    }, 2000);
    
    setTimeout(() => {
        showMainMenu();
    }, 4000);
}
```

---

### Scenario 6: Create Dynamic Response from Data

```javascript
function handleDynamicQuery(data) {
    const messageDiv = document.createElement('div');
    messageDiv.className = 'message bot';
    
    const bubble = document.createElement('div');
    bubble.className = 'bubble';
    
    // Build from data object
    const content = `
        Status: ${data.status}
        Reference: ${data.refId}
        Updated: ${data.date}
    `;
    
    bubble.textContent = content;
    messageDiv.appendChild(bubble);
    
    const timestamp = document.createElement('div');
    timestamp.className = 'timestamp';
    timestamp.textContent = new Date().toLocaleTimeString([], { 
        hour: '2-digit', 
        minute: '2-digit' 
    });
    messageDiv.appendChild(timestamp);
    
    messagesContainer.appendChild(messageDiv);
    messagesContainer.scrollTop = messagesContainer.scrollHeight;
}

// Usage:
handleDynamicQuery({
    status: 'Approved',
    refId: '789',
    date: '25-Mar-2026'
});
```

---

## 🎨 CSS Customization

### Change Button Styles
```javascript
// Find .action-btn class in CSS
.action-btn {
    padding: 16px 20px;        // Adjust size
    background: var(--primary-blue);  // Change color
    border-radius: 6px;        // Change roundness
    font-weight: 700;          // Change font weight
    font-size: 16px;           // Change text size
}
```

### Modify Animation Speed
```javascript
// In animation definitions:
@keyframes slideIn {
    animation: slideIn 0.3s ease;  // Change 0.3s to faster/slower
}
```

### Adjust Chat Bubble Size
```javascript
.bubble {
    max-width: 80%;        // Change width percentage
    padding: 16px;         // Adjust padding
    border-radius: 16px;   // Adjust roundness
}
```

---

## 🔌 Integration Points

### For Backend Integration

```javascript
// Replace setTimeout simulation with API call:
async function sendMessage() {
    const text = messageInput.value.trim();
    if (!text) return;
    
    messageInput.value = '';
    addUserMessage(text);
    
    try {
        // Call your backend API
        const response = await fetch('/api/query', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({ query: text, userId: userId })
        });
        
        const data = await response.json();
        addBotMessage(data.response);
        
        if (data.showMenu) {
            setTimeout(() => showMainMenu(), 1000);
        }
    } catch (error) {
        addBotMessage("Sorry, I'm having trouble connecting. Please try again.");
    }
}
```

### For Database Integration

```javascript
// Store user interaction
async function logInteraction(userText, botResponse) {
    await fetch('/api/logs', {
        method: 'POST',
        body: JSON.stringify({
            timestamp: new Date(),
            userId: employeeId,
            userInput: userText,
            botResponse: botResponse,
            language: currentLanguage
        })
    });
}
```

---

## 🧪 Testing Improvements

### Add Console Logging
```javascript
function handleSalaryQuery() {
    console.log('[QUERY] User asked about salary');
    console.log('[LANGUAGE]', currentLanguage);
    // ... rest of function
}
```

### Add Error Boundary
```javascript
function safeSendMessage() {
    try {
        sendMessage();
    } catch (error) {
        console.error('Message error:', error);
        addBotMessage("An error occurred. Please try again.");
    }
}
```

---

## 📊 Admin Dashboard Customization

### Add New Stat Card
```javascript
// In HTML, add to dashboard-grid:
<div class="stat-card">
    <div class="stat-icon">💻</div>
    <div class="stat-value">856</div>
    <div class="stat-label">Tickets Resolved</div>
</div>
```

### Add New Alert
```javascript
// In HTML, add to alerts-section:
<div class="alert-item">
    <div class="alert-icon">📢</div>
    <div>
        <strong>New Feature Available</strong><br>
        <small>Document upload feature now live</small>
    </div>
</div>
```

---

## 🚀 Performance Optimization

### Lazy Load Messages
```javascript
// Load messages gradually for large conversations
function addBotMessageOptimized(text) {
    requestAnimationFrame(() => {
        addBotMessage(text);
    });
}
```

### Debounce Input
```javascript
let inputTimeout;
function handleKeyPress(event) {
    if (event.key === 'Enter') {
        clearTimeout(inputTimeout);
        inputTimeout = setTimeout(() => {
            sendMessage();
        }, 100);
    }
}
```

---

## 📱 Mobile Optimization Tips

```css
/* For better mobile experience */
@media (max-width: 480px) {
    .bubble {
        max-width: 85%;     /* Larger on mobile */
        font-size: 15px;    /* Slightly larger text */
    }
    
    .action-btn {
        padding: 14px 16px; /* Bigger touch targets */
        font-size: 14px;
    }
    
    .menu-btn {
        padding: 18px;      /* Easier to tap */
    }
}
```

---

## 🔐 Security Considerations

```javascript
// Sanitize user input
function sanitizeInput(text) {
    const div = document.createElement('div');
    div.textContent = text;  // Use textContent, not innerHTML
    return div.innerHTML;
}

// Use in message display
addUserMessage(sanitizeInput(userInput));
```

---

## 📚 Useful Resources

- **DOM API:** https://developer.mozilla.org/en-US/docs/Web/API/Document
- **CSS3:** https://developer.mozilla.org/en-US/docs/Web/CSS
- **JavaScript Events:** https://developer.mozilla.org/en-US/docs/Web/Events
- **Async/Await:** https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Promises

---

## 🐛 Debugging Tips

### Check State
```javascript
console.log('Current Language:', currentLanguage);
console.log('Chat Started:', chatStarted);
console.log('Current Menu:', currentMenu);
console.log('Voice Recording:', isVoiceRecording);
```

### Monitor DOM
```javascript
console.log('Messages Container:', messagesContainer.children.length);
console.log('Last Message:', messagesContainer.lastChild);
```

### Test Keyword Matching
```javascript
const testText = "Can I check my salary?";
console.log(testText.toLowerCase().includes('salary')); // true
```

---

## 📞 Quick Reference

| Task | Location |
|------|----------|
| Add keyword | `sendMessage()` function |
| Create response | New handler function |
| Change colors | CSS `:root` variables |
| Add button | `showMainMenu()` in HTML |
| Modify UI | CSS classes |
| Change animation | `@keyframes` in CSS |
| Add language | `messages` object |
| Handle error | Try/catch blocks |

---

**Developer Guide Version:** 1.0
**Last Updated:** March 25, 2026
**Maintainer:** GovBot Development Team
