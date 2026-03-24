# GovBot Enhancement - Quick Test Checklist ✅

## Before You Test
- Open `index.html` in your browser
- Select Language (English or Kannada)
- Minimize the notification popup if it appears

---

## Test Suite

### ✅ Salary Query Tests
- [ ] Type: `"salary"` → Get salary processed message
- [ ] Type: `"check my pay"` → Get salary processed message
- [ ] Type: `"arrears"` → Get salary processed message
- [ ] Type: `"payment status"` → Get salary processed message
- [ ] Click "Escalate to Department" → See modal with Ticket ID #456
- [ ] Click "Back to Menu" → Return to main menu

### ✅ Pension Query Tests
- [ ] Type: `"pension"` → Get pension under review message
- [ ] Type: `"ops"` → Get pension under review message
- [ ] Type: `"retirement"` → Get pension under review message
- [ ] Verify Reference ID: 789 appears
- [ ] Main menu shows after 1.2 seconds

### ✅ Leave Query Tests
- [ ] Type: `"leave"` → Get leave days remaining message
- [ ] Type: `"vacation"` → Get leave days remaining message
- [ ] Type: `"time off"` → Get leave days remaining message
- [ ] Type: `"absent"` → Get leave days remaining message
- [ ] Verify "10 leave days remaining" appears

### ✅ File Query Tests
- [ ] Type: `"file"` → Get file in Accounts Department message
- [ ] Type: `"track status"` → Get file tracking message
- [ ] Type: `"document"` → Get file status message
- [ ] Verify File ID: 456 appears
- [ ] Verify Status: In Progress appears

### ✅ Navigation Tests
- [ ] Type: `"menu"` → Main menu appears
- [ ] Type: `"home"` → Main menu appears
- [ ] Click "Salary Status 💰" button → Salary response
- [ ] Click "Pension / OPS Query 🧾" button → Pension response
- [ ] Click "Leave Request 📄" button → Leave response
- [ ] Click "File Tracking 📂" button → File response

### ✅ Unknown Input Tests
- [ ] Type: `"what time is it?"` → Get fallback message
- [ ] Type: `"hello"` → Get "didn't understand" message
- [ ] Type: `"random text"` → Main menu appears
- [ ] Verify helpful keywords mentioned in response

### ✅ Mixed Case Tests
- [ ] Type: `"SALARY"` → Works correctly
- [ ] Type: `"SaLaRy"` → Works correctly
- [ ] Type: `"PeNsIoN"` → Works correctly

### ✅ Voice Input Tests
- [ ] Click microphone button 🎤
- [ ] Wait 3 seconds (recording animation)
- [ ] Verify "What is my salary status?" appears
- [ ] Verify salary response shows
- [ ] Main menu appears after

### ✅ Button Click Tests
- [ ] Click any menu button
- [ ] Verify user action appears in chat
- [ ] Verify appropriate response follows
- [ ] Main menu shows after response

### ✅ Chat Bubble & UX Tests
- [ ] All messages have timestamps
- [ ] Bot messages are left-aligned (white)
- [ ] User messages are right-aligned (blue)
- [ ] Messages slide in smoothly
- [ ] Chat auto-scrolls to latest message
- [ ] Scrollbar appears when needed

### ✅ Admin Dashboard Tests
- [ ] Click 📊 button in header
- [ ] Dashboard shows with statistics
- [ ] Shows 247 queries today
- [ ] Shows alerts about salary delays
- [ ] Click 📊 again to return to chat

### ✅ Reset Tests
- [ ] Click 🔄 button in header
- [ ] Confirm dialog appears
- [ ] Returns to language selection screen
- [ ] Previous messages cleared
- [ ] Can start new conversation

### ✅ Escalation Tests
- [ ] Select "Salary Status" or type "salary"
- [ ] Click "Escalate to Department"
- [ ] Modal appears with:
  - ✅ icon
  - "Request Escalated" title
  - Ticket ID: #456
  - "You will be notified shortly" message
- [ ] Click "Okay" button
- [ ] Modal closes and main menu appears
- [ ] Confirmation message shows in chat

### ✅ Notification Tests
- [ ] Wait 5 seconds after opening
- [ ] "Salary credited successfully ✅" appears at top
- [ ] Auto-dismisses after 3 seconds
- [ ] Smooth slide-up animation

### ✅ Response After Menu Tests
- [ ] All button selections → Show appropriate response → Main menu
- [ ] All text inputs → Show appropriate response → Main menu
- [ ] All voice inputs → Show appropriate response → Main menu

---

## Detailed Test Scenarios

### Scenario 1: Complete Salary Flow
1. Open app → Select English
2. Type: "I need my salary"
3. Verify: Salary message + buttons appear
4. Click: "Escalate to Department"
5. Verify: Modal with ticket #456 appears
6. Click: "Okay"
7. Verify: Main menu appears
8. **Result:** ✅ Pass / ❌ Fail

### Scenario 2: Multiple Consecutive Queries
1. Type: "pension" → Pension response shows
2. From menu, type: "leave" → Leave response shows
3. From menu, type: "file" → File response shows
4. From menu, click: "Salary Status" button
5. Type: "back to menu" → Main menu shows
6. **Result:** ✅ Pass / ❌ Fail

### Scenario 3: Mixed Input Methods
1. Click: "Salary Status 💰" button
2. Type: "pension" (switches query type)
3. Click: "Escalate to Department"
4. Confirm escalation
5. Use voice button (🎤)
6. Wait for auto-response
7. **Result:** ✅ Pass / ❌ Fail

### Scenario 4: Error Recovery
1. Type: "xyz random text"
2. Verify: Fallback message
3. Verify: Main menu appears
4. Type: "salary" → Correct response
5. Verify: System recovered properly
6. **Result:** ✅ Pass / ❌ Fail

### Scenario 5: Full Session
1. Welcome screen with language selection
2. Chat through all 4 menu options
3. Try voice input
4. Test admin dashboard
5. Test reset button
6. New session works
7. **Result:** ✅ Pass / ❌ Fail

---

## Quick Command Reference

| Command | Expected Result |
|---------|-----------------|
| `salary` | Salary processed message + buttons |
| `pay` | Salary processed message + buttons |
| `arrears` | Salary processed message + buttons |
| `pension` | Pension under review message |
| `ops` | Pension under review message |
| `retirement` | Pension under review message |
| `leave` | 10 leave days message |
| `vacation` | 10 leave days message |
| `file` | File tracking message |
| `track` | File tracking message |
| `status` | File tracking message |
| `menu` | Main menu appears |
| `randomtext` | Fallback message + menu |

---

## Browser Compatibility ✅
- [ ] Chrome/Chromium
- [ ] Firefox
- [ ] Safari
- [ ] Edge
- [ ] Mobile Chrome
- [ ] Mobile Safari

---

## Performance Checks ✅
- [ ] No console errors
- [ ] Smooth animations (no jank)
- [ ] Response time < 1 second
- [ ] Scrolling is smooth
- [ ] Buttons responsive to clicks
- [ ] No memory leaks (check DevTools)

---

## Notes & Observations
```
_________________________________________________________________

_________________________________________________________________

_________________________________________________________________

_________________________________________________________________
```

---

**Test Status:** [ ] All Pass | [ ] Some Issues | [ ] Major Issues
**Tester Name:** _________________ 
**Test Date:** March 25, 2026
**Signature:** _________________
