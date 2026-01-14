# 🎰 POKER VIP: ULTIMATE EDITION 🎰

A premium, real-time multiplayer poker application built with Firebase Realtime Database and Vanilla JavaScript. Features stunning "Deep Poker Green" aesthetics with felt textures, wood rail borders, gold accents, and 3D CSS chip animations.

---

## 🌟 Features

### Core Features
- ✅ **Real-time Multiplayer** - Powered by Firebase Realtime Database
- ✅ **Turn-Based Gameplay** - Automatic turn management with visual indicators
- ✅ **3D CSS Chips** - Beautiful chip animations with realistic stacking
- ✅ **Haptic Feedback** - Vibration support for mobile devices
- ✅ **Sound Effects** - Generated via Web Audio API (AudioContext)
- ✅ **Premium UI/UX** - Felt textures, wood borders, gold accents
- ✅ **Responsive Design** - Landscape for Host, Portrait for Player
- ✅ **Safe Area Support** - Optimized for modern mobile devices

### Advanced Features
- 🎯 **Smart Action Buttons** - Dynamically changes (CHECK/CALL/RAISE)
- 💰 **Pot Management** - Visual chip pile with scatter animations
- 🎲 **Dealer Rotation** - Automatic dealer button management
- 👥 **Player Management** - Seat arrangement, kick players
- 🏆 **Split Pot System** - Multi-winner pot distribution
- 🎪 **Flying Chip Animations** - Smooth transitions to pot
- 🔄 **Turn Awareness** - Full-screen overlay when waiting
- 📱 **Mobile Optimized** - Touch-friendly controls

---

## 📂 Project Structure

```
Poker 2/
│
├── index.html          # Landing page with navigation
├── host.html           # Table display (TV/Tablet)
├── player.html         # Mobile controller
└── README.md           # This file
```

---

## 🚀 Getting Started

### Prerequisites
- A modern web browser (Chrome, Firefox, Safari, Edge)
- Internet connection (for Firebase)
- Mobile device for best player experience

### Installation

1. **Clone or download** this project to your local machine

2. **Open the application**
   - Simply open `index.html` in your browser
   - OR use a local server (recommended):
   ```bash
   # Using Python 3
   python -m http.server 8000
   
   # Using Node.js (http-server)
   npx http-server
   ```

3. **Access the app**
   - Navigate to `http://localhost:8000` in your browser

---

## 🎮 How to Play

### Step 1: Setup the Host

1. Open `host.html` on a TV, tablet, or laptop (landscape orientation recommended)
2. Enter a **Room Code** (e.g., "POKER123")
3. Set a **Password** for security
4. Click **CREATE GAME**

The host screen will display:
- The central pot with visual chips
- Player cards in a grid
- Active turn indicators (pulsing green border)
- Dealer button (rotating "D" token)
- Admin controls at the bottom

### Step 2: Players Join

1. Open `player.html` on a mobile phone (portrait orientation)
2. Enter the same **Room Code**
3. Enter the **Password**
4. Enter your **Player Name**
5. Click **JOIN GAME**

### Step 3: Play Poker!

#### Player Actions (Mobile):
- **Wait for Your Turn** - A dark overlay appears showing who's active
- **Your Turn Notification** - Screen glows green, phone vibrates, sound plays
- **Add Chips** - Tap chips at the bottom (1, 5, 25, 100)
- **Stage Bets** - Chips accumulate in the staging area
- **Smart Action Button**:
  - Shows "CHECK" if you match the highest bet
  - Shows "CALL $X" if you need to match
  - Shows "RAISE TO $X" if you're raising
- **Fold** - Give up the current round
- **Clear Staging** - Reset your staged bet

#### Host Controls:
- **Seat Arrangement** - Use `< >` arrows to reorder players
- **Kick Player** - Click the `✕` button to remove a player
- **Next Round** - Clears pot, rotates dealer, resets bets
- **Split Pot** - Select multiple winners to divide the pot
- **Reset All** - Resets everyone to 1000 chips

---

## 🎨 Design Features

### Visual Aesthetics
- **Deep Poker Green Background** - Gradient felt texture
- **Wood Rail Borders** - Realistic wood grain with shadows
- **Gold Accents** - Premium gold text and borders
- **3D CSS Chips** - Radial gradients, border rings, shadows
- **Animations**:
  - Pulsing borders for active player
  - Rotating dealer button
  - Flying chip transitions
  - Chip drop animations
  - Smooth hover effects

### Color Palette
| Element | Color |
|---------|-------|
| Felt Background | `#1a3a1a` to `#0d1f0d` |
| Wood Border | `#4a2f1a` to `#6b4423` |
| Gold Accent | `#ffd700` |
| Green Chips | `#2d8f2d` |
| Red Chips | `#dc143c` |
| White Chips | `#e0e0e0` |
| Black Chips | `#000` with gold border |

---

## 🔧 Technical Details

### Firebase Configuration
```javascript
const firebaseConfig = {
    apiKey: "AIzaSyApDemI7Jtd76lOo1oPBmHneMb4mHCMxZs",
    authDomain: "poker-night-app-dffc6.firebaseapp.com",
    databaseURL: "https://poker-night-app-dffc6-default-rtdb.asia-southeast1.firebasedatabase.app",
    projectId: "poker-night-app-dffc6",
    storageBucket: "poker-night-app-dffc6.firebasestorage.app",
    messagingSenderId: "304292154404",
    appId: "1:304292154404:web:c1d94e60add9a8f0d75cb1"
};
```

### Database Structure
```
rooms/
  {roomCode}/
    password: string
    pot: number
    dealerIndex: number
    turnIndex: number
    seats: [playerName1, playerName2, ...]
    players/
      {playerName}/
        chips: number
        currentBet: number
        folded: boolean
        joined: timestamp
```

### Key Technologies
- **HTML5** - Semantic structure
- **CSS3** - Advanced animations, gradients, transforms
- **JavaScript ES6** - Modules, async/await, arrow functions
- **Firebase v9** - Modular SDK for Realtime Database
- **Web Audio API** - Sound generation
- **Vibration API** - Haptic feedback

---

## 🎯 Game Logic

### Turn Management
1. Game maintains `turnIndex` pointing to current player
2. Player's card shows pulsing green border when active
3. Mobile players see full-screen overlay when not their turn
4. After action (Bet/Check/Fold), automatically advances to next non-folded player

### Dealer Rotation
- Visual "D" token rotates clockwise each round
- Stored as `dealerIndex` in Firebase
- Next Round button advances by 1 (with wraparound)

### Pot Management
- All bets contribute to central pot
- Visual chips rendered with random scatter
- Split Pot allows multiple winners
- Pot clears on Next Round

### Betting Rules
- **Check**: Pass without betting (only if matching highest bet)
- **Call**: Match the highest current bet
- **Raise**: Bet more than the highest current bet
- **Fold**: Give up and skip remaining turns this round

---

## 📱 Responsive Design

### Host (Landscape)
- Optimized for TV, Tablet, Laptop
- Large central pot display
- Grid layout for players (auto-fit)
- Bottom admin controls bar

### Player (Portrait)
- Mobile-first design
- Safe area insets for notch/home indicator
- Bottom chip dock (always accessible)
- Large touch-friendly buttons
- Vertical scrolling when needed

---

## 🔊 Audio System

### Sound Effects
All sounds generated via `AudioContext`:
- **Turn Notification**: Two-tone beep (800Hz → 1000Hz)
- **Chip Click**: Quick 600Hz pulse
- **Bet Placed**: 700Hz with decay

### Example Code
```javascript
function playSound(frequency, duration) {
    const audioContext = new AudioContext();
    const oscillator = audioContext.createOscillator();
    const gainNode = audioContext.createGain();
    
    oscillator.frequency.value = frequency;
    oscillator.type = 'sine';
    
    gainNode.gain.exponentialRampToValueAtTime(0.01, 
        audioContext.currentTime + duration);
    
    oscillator.connect(gainNode);
    gainNode.connect(audioContext.destination);
    
    oscillator.start();
    oscillator.stop(audioContext.currentTime + duration);
}
```

---

## 🛡️ Security Features

- **Password Protection**: Rooms require password to join
- **Validation**: Checks room existence and password match
- **Kick Detection**: Auto-reload if player node is deleted
- **Input Sanitization**: Trims whitespace, validates presence

---

## 🚨 Known Limitations

1. **No Hand Evaluation** - This is a betting interface only (no card dealing/evaluation)
2. **Trust-Based** - Host manages game state (assumes honest play)
3. **No Persistence** - Game state resets if host disconnects
4. **Browser Compatibility** - Requires modern browser with ES6 module support

---

## 🎨 Customization Guide

### Change Chip Values
Edit the chip dock in `player.html`:
```html
<div class="chip chip-1" onclick="addChip(1)">...</div>
<div class="chip chip-5" onclick="addChip(5)">...</div>
<!-- Add more denominations -->
```

### Modify Color Scheme
Update CSS variables in each file:
```css
/* Felt Green */
background: linear-gradient(135deg, #1a3a1a 0%, #0d1f0d 100%);

/* Gold Accent */
color: #ffd700;
border-color: #d4af37;
```

### Adjust Starting Chips
In both `host.html` and `player.html`:
```javascript
chips: 1000  // Change to your preferred amount
```

---

## 🐛 Troubleshooting

### Players Can't Join
- Verify room code matches exactly (case-sensitive)
- Check password is correct
- Ensure Firebase database is accessible

### Buttons Not Working
- Check browser console for errors
- Verify Firebase configuration is correct
- Ensure you're using a modern browser

### No Sound/Vibration
- Check device volume
- Ensure browser has audio permissions
- Vibration API requires HTTPS (except localhost)

### Turn Not Advancing
- Verify all players have different names
- Check Firebase rules allow read/write
- Refresh all clients if stuck

---

## 📜 License

This project is open source and available for personal and educational use.

---

## 🙏 Credits

- **Design Inspiration**: Classic poker tables and casino aesthetics
- **Firebase**: Google Firebase Realtime Database
- **Icons**: Unicode emojis (♠️♥️♦️♣️)
- **Fonts**: Georgia, Times New Roman (web-safe serif fonts)

---

## 📞 Support

For issues or questions:
1. Check the troubleshooting section above
2. Review Firebase Console for database errors
3. Inspect browser console for JavaScript errors

---

## 🎉 Enjoy Your Premium Poker Night!

Built with ❤️ using Vanilla JavaScript, CSS3, and Firebase.

**No frameworks. No dependencies. Just pure web technology.**

---

### Quick Start Commands

```bash
# Open in default browser (Windows)
start index.html

# Open in default browser (Mac)
open index.html

# Open in default browser (Linux)
xdg-open index.html

# Run local server
python -m http.server 8000
```

---

**🎰 May the chips be ever in your favor! 🎰**
