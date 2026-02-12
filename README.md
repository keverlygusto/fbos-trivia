# Team Trivia App 🎯

A real-time multiplayer trivia game built for virtual team socials. Supports 10-15 players with live leaderboards and synchronized questions.

## Features

- Real-time multiplayer gameplay
- Live leaderboard updates
- Host controls for question flow
- Mobile-friendly responsive design
- Multiple choice questions (A/B/C/D)
- 15 sample questions included

## Quick Setup (15-20 minutes)

### Step 1: Set Up Firebase (10 minutes)

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add project" or "Create a project"
3. Enter a project name (e.g., "team-trivia")
4. Disable Google Analytics (not needed)
5. Click "Create project"

6. Once created, click the **Web icon** (`</>`) to add a web app
7. Give it a nickname (e.g., "Trivia App")
8. Click "Register app"

9. Copy the Firebase configuration object that appears
10. In your `index.html` file, find this section (around line 295):
    ```javascript
    const firebaseConfig = {
        apiKey: "YOUR_API_KEY",
        authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
        databaseURL: "https://YOUR_PROJECT_ID-default-rtdb.firebaseio.com",
        projectId: "YOUR_PROJECT_ID",
        storageBucket: "YOUR_PROJECT_ID.appspot.com",
        messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
        appId: "YOUR_APP_ID"
    };
    ```
11. Replace it with YOUR Firebase configuration

12. **Enable Realtime Database:**
    - In Firebase Console, click "Build" → "Realtime Database"
    - Click "Create Database"
    - Choose a location (doesn't matter which)
    - Start in **test mode** for now (you can secure it later)
    - Click "Enable"

### Step 2: Deploy to GitHub Pages (5 minutes)

1. Create a new GitHub repository (name it whatever you want)
2. In your terminal, navigate to the trivia-app folder:
   ```bash
   cd /Users/kyle.everly/trivia-app
   ```

3. Initialize git and push:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Team trivia app"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
   git push -u origin main
   ```

4. Enable GitHub Pages:
   - Go to your repo on GitHub
   - Settings → Pages
   - Source: Deploy from branch
   - Branch: `main` → `/ (root)` → Save

5. Your app will be live at: `https://YOUR_USERNAME.github.io/YOUR_REPO_NAME/`

### Step 3: Customize Questions (5-10 minutes)

In `index.html`, find the `questions` array (around line 308). Edit it to add your own questions:

```javascript
const questions = [
    {
        question: "Your question here?",
        answers: ["Option A", "Option B", "Option C", "Option D"],
        correct: 1  // Index of correct answer (0=A, 1=B, 2=C, 3=D)
    },
    // Add more questions...
];
```

After editing, commit and push changes:
```bash
git add .
git commit -m "Updated trivia questions"
git push
```

## How to Run Your Trivia Night

### For the Host:

1. Open the app URL
2. Click "Host Game"
3. Enter host code: `host123`
4. Share the app URL with your team
5. Use controls to:
   - "Next →" to advance to next question
   - "Reveal Answer" to show correct answer (locks in scores)
   - "← Previous" to go back if needed

### For Players:

1. Open the app URL on any device
2. Enter your name
3. Click "Join Game"
4. Answer questions as they appear
5. Watch your score on the live leaderboard!

## Tips

- Have all players join BEFORE starting question 1
- Give players 30-60 seconds per question before revealing
- You can navigate back/forward through questions as needed
- Players see results immediately after clicking an answer
- The leaderboard updates in real-time

## Customization

### Change Host Code
In `index.html`, find line 565:
```javascript
if (code !== 'host123') {
```
Change `'host123'` to your desired code.

### Change Colors
Edit the CSS in the `<style>` section (lines 7-280) to customize colors and appearance.

### Add More Questions
Add more objects to the `questions` array following the same format.

## Troubleshooting

**"Players not syncing"**: Make sure Firebase Realtime Database is enabled in test mode

**"Page not loading"**: Check that you replaced ALL Firebase config values (not just some)

**"GitHub Pages not working"**: Wait 2-3 minutes after enabling, then hard refresh (Cmd+Shift+R or Ctrl+Shift+R)

**"Host code not working"**: Default is `host123`, make sure it's entered exactly

## Security Notes

The Firebase database is currently in test mode (open to everyone). For a production app, you'd want to add security rules, but for a one-time team event with 10-15 people, test mode is fine.

After your event, you can:
- Delete the Firebase project
- Make the GitHub repo private
- Or keep it running for future trivia nights!

## License

Free to use and modify for your team events!
