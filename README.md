# GovBot - AI Helpdesk for Government Services

A modern, professional chatbot UI for government employee helpdesk support. Features intelligent keyword detection, clean design principles, and smooth interactions.

**📊 Latest Update:** Keyword detection for natural language input (v2.0)

## 🎨 Features

### Natural Language Processing
The chatbot intelligently detects keywords from user input and responds appropriately:
- **Salary Keywords:** "salary", "pay", "arrears", "payment", "remuneration"
- **Pension Keywords:** "pension", "ops", "retirement"  
- **Leave Keywords:** "leave", "vacation", "time off", "absent"
- **File Keywords:** "file", "status", "track", "document", "request"
- **Navigation Keywords:** "menu", "home"
- **Fallback:** Unknown queries show helpful error with suggestions

### Welcome Screen
- **Animated logo** with bouncing effect
- **Language selection**: English & Kannada
- Clean gradient background with government blue theme
- Smooth transition to main chat interface

### Chat Interface
- **Chat bubbles** with timestamps
- **Bot messages** (left, white background)
- **User messages** (right, blue background)
- **Auto-scrolling** to latest messages
- **Smooth animations** for new messages

### Main Menu
- **Salary Status** 💰 - Check salary processing status
- **Pension / OPS Query** 🧾 - Pension-related inquiries
- **Leave Request** 📄 - Submit leave requests
- **File Tracking** 📂 - Track document status

### Salary Status Flow
When user selects "Salary Status":
- Displays salary information: "Your salary is processed. Expected by 15th. Track ID: 123"
- Shows detailed salary card with:
  - Salary Month: March 2026
  - Status: Processed
  - Amount: ₹45,000
  - Expected Date: 15th March
- Two action buttons:
  - **Escalate to Department** - Forward to Accounts Department
  - **Back to Menu** - Return to main menu

### Escalation Feature
- Clicking "Escalate" opens a confirmation modal
- Shows: "Request has been forwarded to Accounts Department"
- Displays Ticket ID: #456
- Confirmation message: "You will be notified shortly"

### Header Features
- **Status Indicator**: Connected/Online status (green pulsing dot)
- **Profile Badge**: Employee ID (Emp ID: 4521)
- **Admin Dashboard Button** (📊): View admin metrics
- **Reset Chat Button** (🔄): Start new conversation

### Input Area
- **Voice Input Button** (🎤): Simulates voice recording with visual feedback
- **Text Input Field**: Type your query
- **Send Button**: Submit (➤)
- Auto-focus and smooth styling

### Voice Input
- **Recording indicator**: Pulsing orange animation
- **Auto-response**: Simulates understanding "What is my salary status?"
- **3-second recording timeout**

### Admin Dashboard
- **Statistics Cards**:
  - 📞 Queries Today: 247
  - ⏱️ Avg Response: 2.3 min
  - ✅ Resolution Rate: 94%
  - 👥 Active Users: 1,843
- **Active Alerts**:
  - ⚠️ High Salary Delay Complaints (45% increase)
  - 📈 Most Common Issue: Salary Processing Delays
  - ⏰ Escalation Queue Building

### Notifications
- **System notification** appears 5 seconds after page load
- "Salary credited successfully ✅"
- Auto-dismisses with smooth slide-up animation

## 🎯 Design Features

### Color Scheme (Government Blue Theme)
- **Primary Blue**: #003DA5
- **Light Blue**: #0066FF
- **Accent Blue**: #1E88E5
- **Success Green**: #28A745
- **Warning Orange**: #FF8C00
- **White**: #FFFFFF

### Typography & Spacing
- Responsive font sizes
- Clear hierarchy
- Comfortable padding and margins
- Professional sans-serif fonts

### Animations
- Smooth message transitions
- Button hover effects
- Pulse animations for status indicators
- Modal pop-in effects
- Notification slide animations

### Mobile-Friendly
- Max width: 500px (standard mobile size)
- Touch-friendly buttons (44x44px minimum)
- Responsive grid layouts
- Works on all screen sizes

## 🚀 How to Use

1. **Open the file**:
   - Double-click `index.html` or open in a web browser

2. **Select Language**:
   - Choose English or Kannada (ಕನ್ನಡ)

3. **Chat Flow**:
   - Follow the main menu options
   - Select "Salary Status" to see the detailed flow
   - Click "Escalate to Department" to test the escalation modal

4. **Voice Input**:
   - Click the microphone button (🎤)
   - It will simulate 3 seconds of recording
   - Auto-responds after recording completes

5. **Admin Dashboard**:
   - Click the dashboard button (📊) in header
   - View statistics and alerts
   - Click again to return to chat

6. **Reset Chat**:
   - Click the reset button (🔄) to start over
   - Returns to language selection screen

## 📱 Mobile Optimization

- **Viewport**: Optimized for mobile devices
- **Scrolling**: Smooth scrollbar styling
- **Touch-friendly**: Large, easy-to-tap buttons
- **Responsive Grid**: Adapts to screen size

## 🔧 Technical Stack

- **HTML5**: Semantic markup
- **CSS3**: Modern styling with gradients and animations
- **Vanilla JavaScript**: No dependencies required
- **Single File**: All code in one HTML file for easy deployment

## 📋 Browser Support

- Chrome/Chromium
- Firefox
- Safari
- Edge
- Mobile browsers (iOS Safari, Chrome Mobile)

## 🎬 Demo Flows

### Flow 1: Salary Status Query
1. Welcome Screen → Language Selection
2. Main Menu → Select "Salary Status 💰"
3. View Salary Details
4. Click "Escalate to Department"
5. Confirm escalation modal

### Flow 2: Voice Input
1. Click microphone button
2. Watch 3-second recording animation
3. Auto-response processes query
4. Shows salary status

### Flow 3: Admin Dashboard
1. Click 📊 button in header
2. View statistics and alerts
3. Click 📊 again to return to chat

## 🎨 Customization Tips

- **Colors**: Edit CSS `:root` variables to change theme
- **Messages**: Update `messages` object for different languages
- **Delay**: Adjust `setTimeout` values for faster/slower responses
- **Buttons**: Add more menu options in `showMainMenu()` function

## ✨ Future Enhancements

- ML-based intent detection for more complex queries
- Context-aware multi-turn conversations
- Sentiment analysis for customer satisfaction
- User interaction history and analytics
- Custom response templates by department
- Multilingual support expansion
- Integration with government databases
- Real backend API connection
- Voice recognition (Web Speech API)
- Document upload and processing

---

**Version:** 2.0 - Keyword Detection & Natural Language Processing
**Last Updated:** March 25, 2026
