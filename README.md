# FBOS Trivia Challenge 🎯

A real-time multiplayer trivia game built for virtual team socials with modern UI/UX design, Kahoot-style time-based scoring, and Firebase backend.

## 🎮 Live Demo

**Game URL:** https://keverlygusto.github.io/fbos-trivia/

## ✨ Features

### Core Gameplay
- **Real-time multiplayer** - Supports 10-15+ players simultaneously
- **Kahoot-style scoring** - Faster answers earn more points (500-1000 points per question)
- **30 trivia questions** across 4 categories:
  - 🥇 Winter Olympics (10 questions)
  - 🌍 Geography (10 questions)
  - 🍕 Food (5 questions)
  - 💻 Tech, AI & Silicon Valley (5 questions)
- **20-second timer** per question with visual countdown
- **Live leaderboard** updates in real-time

### Game Flow
1. **Lobby** - Players join and wait for host to start
2. **Playing** - 30 questions with timer and instant scoring
3. **Final Results** - Victory podium with animated medals for top 3

### Host Controls
- Start/restart game
- Navigate between questions
- Reveal answers
- Remove players from game
- View live leaderboard

### Modern Design
- **Premium UI/UX** - Glassmorphism, smooth animations, modern typography
- **Gusto branding** - Custom orange/coral color scheme
- **Fully responsive** - Works on desktop, tablet, and mobile
- **Professional feel** - Innovative tech company aesthetic

## 🚀 Quick Setup (15-20 minutes)

### Step 1: Firebase Setup (10 minutes)

1. **Create Firebase Project**
   - Go to https://console.firebase.google.com/
   - Click "Add project" or "Create a project"
   - Project name: `fbos-trivia` (or your choice)
   - Disable Google Analytics (not needed)
   - Click "Create project"

2. **Add Web App**
   - Click the Web icon (`</>`)
   - App nickname: `Trivia App`
   - Don't check Firebase Hosting
   - Click "Register app"

3. **Copy Firebase Config**
   - Copy the `firebaseConfig` object shown
   - In `index.html`, replace lines 946-953 with your config:
   ```javascript
   const firebaseConfig = {
       apiKey: "YOUR_API_KEY",
       authDomain: "YOUR_PROJECT.firebaseapp.com",
       databaseURL: "https://YOUR_PROJECT-default-rtdb.firebaseio.com",
       projectId: "YOUR_PROJECT",
       storageBucket: "YOUR_PROJECT.firebasestorage.app",
       messagingSenderId: "YOUR_SENDER_ID",
       appId: "YOUR_APP_ID"
   };
   ```

4. **Enable Realtime Database**
   - In Firebase Console, click "Build" → "Realtime Database"
   - Click "Create Database"
   - Choose a location (any)
   - Start in **test mode** (for quick setup)
   - Click "Enable"

5. **Set Database Rules**
   - Click the "Rules" tab
   - Replace with:
   ```json
   {
     "rules": {
       ".read": true,
       ".write": true
     }
   }
   ```
   - Click "Publish"

### Step 2: Deploy to GitHub Pages (5-10 minutes)

1. **Create GitHub Repository**
   - Go to https://github.com/new
   - Repository name: `fbos-trivia` (or your choice)
   - Make it **Public** (required for free GitHub Pages)
   - Don't add README, .gitignore, or license
   - Click "Create repository"

2. **Push Code** (if not already done)
   ```bash
   cd /Users/kyle.everly/trivia-app
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin git@github.com:YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```

3. **Enable GitHub Pages**
   - Go to repository Settings → Pages
   - Source: "Deploy from a branch"
   - Branch: `main` → `/ (root)` → Save
   - Wait 1-2 minutes for deployment

4. **Get Your URL**
   - Your app will be live at: `https://YOUR_USERNAME.github.io/YOUR_REPO/`

## 🎮 How to Play

### For Players:
1. Open the game URL
2. Enter your name
3. Click "Join Game"
4. Wait in lobby for host to start
5. Answer questions as fast as possible!
6. See your score on the live leaderboard

### For Host:
1. Open the game URL
2. Click "Host Game"
3. Enter host code: `host123`
4. Click "Start Hosting"
5. Wait for players to join
6. Click "Start Game" to begin
7. Use controls:
   - **Next →** - Advance to next question (or show final results after Q30)
   - **← Previous** - Go back to previous question
   - **Reveal Answer** - Show correct answer (locks in player scores)
   - **Restart Game** - Reset all scores and return to lobby

## ⚙️ Configuration

### Change Host Password

In `index.html`, find line ~1197:
```javascript
if (code !== 'host123') {
```
Change `'host123'` to your desired password.

### Customize Questions

In `index.html`, find the `questions` array (around line 965). Format:
```javascript
{
    question: "Your question here?",
    answers: ["Option A", "Option B", "Option C", "Option D"],
    correct: 1  // Index of correct answer (0=A, 1=B, 2=C, 3=D)
}
```

### Adjust Timer

In `index.html`, line 962:
```javascript
const QUESTION_TIME_LIMIT = 20; // seconds
```

### Change Scoring

In `index.html`, line 963:
```javascript
const MAX_POINTS = 1000; // Maximum points for instant answer
```

Points decrease over time: 1000 points (instant) → 500 points (at time limit)

## 🎨 Design System

### Colors
- **Primary:** `#F45D48` (Gusto Orange)
- **Primary Dark:** `#E94B35`
- **Success:** `#10b981` (Green)
- **Error:** `#ef4444` (Red)
- **Warning:** `#f59e0b` (Amber)
- **Neutral:** `#f3f4f6`, `#e5e7eb`, `#d1d5db`

### Typography
- **Font:** Inter (Google Fonts)
- **Weights:** 400 (Regular), 500 (Medium), 600 (Semibold), 700 (Bold), 800 (Extrabold)

### Effects
- Glassmorphism cards with `backdrop-filter: blur(20px)`
- Multi-layer shadows for depth
- Smooth cubic-bezier transitions
- Gradient backgrounds and buttons
- Animated micro-interactions

## 📁 Project Structure

```
trivia-app/
├── index.html          # Complete single-file application
├── README.md          # This file
└── .git/              # Git version control
```

## 🔧 Technical Stack

- **Frontend:** Vanilla JavaScript, HTML5, CSS3
- **Backend:** Firebase Realtime Database
- **Hosting:** GitHub Pages
- **Fonts:** Google Fonts (Inter)
- **Architecture:** Single-page application (SPA)

## 📊 Firebase Data Structure

```javascript
{
  "gameState": {
    "status": "lobby" | "playing" | "finished",
    "currentQuestion": 0,
    "showAnswer": false,
    "totalQuestions": 30
  },
  "players": {
    "player_1234567890": {
      "name": "Kyle",
      "score": 7500,
      "joinedAt": 1234567890
    }
  }
}
```

## 🚨 Troubleshooting

### Players not syncing
- Verify Firebase Realtime Database is enabled
- Check database rules allow read/write
- Confirm correct `databaseURL` in config

### GitHub Pages not loading
- Wait 2-3 minutes after enabling Pages
- Hard refresh browser (Cmd/Ctrl + Shift + R)
- Check repository is Public
- Verify Pages is enabled for `main` branch

### Timer not working
- Check browser console for JavaScript errors
- Ensure Firebase config is correct
- Try clearing browser cache

### Host code not working
- Default code is `host123`
- Check if you changed it in the code
- Case-sensitive - must match exactly

## 🔐 Security Notes

**Current Setup:**
- Firebase database is in test mode (open read/write)
- Fine for private team events with 10-15 people
- Host code provides basic access control

**For Production:**
- Add Firebase security rules
- Implement proper authentication
- Use environment variables for config
- Make repository private if needed

## 🎯 Future Enhancements

Ideas for expansion:
- User authentication
- Question categories selection
- Custom question upload
- Team vs Team mode
- Question difficulty levels
- Sound effects and music
- Multiple game sessions
- Admin dashboard
- Question bank management
- Export results to CSV

## 📝 License

Free to use and modify for team events and internal use.

## 🙋 Support

For issues or questions:
1. Check the Troubleshooting section
2. Review Firebase Console for errors
3. Check browser console for JavaScript errors
4. Verify all setup steps were completed

## 🎉 Credits

Built with Claude Code for FBOS team social events.

Design inspired by modern SaaS applications and innovative tech companies.

---

**Enjoy your trivia night! 🎊**
