# 🎬 WatchParty - Synchronized Cinema

WatchParty is a real-time web application that allows friends to watch YouTube videos, movies, or screen-share streams together in perfect sync, chat live, and react with emojis—no matter where they are.

🌐 **Live Website:** [https://watch-party-topaz-one.vercel.app/](https://watch-party-topaz-one.vercel.app/)

---

## ✨ Features

- **Synced Video Playback:** Play, pause, and seek videos together across all connected devices in real time.
- **Media Hub:** Quick access to load YouTube streams or launch popular streaming platforms (Netflix, JioHotstar, Amazon Prime Video, MX Player) and stream via tab audio sharing.
- **WebRTC Screen & Audio Sharing:** Share your browser tab with live audio streaming so everyone can listen along.
- **Live Room Chat & Presence:** Send real-time text messages and see who is currently online in the room.
- **Interactive Emoji Reactions:** Send floating emoji animations (`❤️`, `🔥`, `😂`, `🎉`) across the screen instantly.
- **Custom Room Codes:** Easily create a private room and invite friends via a shareable link or 6-character code.

---

## 🛠️ How It Works

WatchParty combines **Cloud Firestore (Firebase)** for real-time state synchronization and **WebRTC** for peer-to-peer screen/audio streaming:

1. **Room Creation & Joining:**
   - When you create a room, a unique 6-character code and Firestore document are generated. When friends open your invite link or enter the code, they connect to that same room document.

2. **Real-Time Playback Synchronization:**
   - Every time a user plays, pauses, or seeks the video, the app updates a shared `videoState` object (timestamp, playing status, and last update time) in Firebase.
   - All other connected devices instantly listen to these updates via Firebase snapshots, automatically syncing their player's current time and play/pause state.
   - Built-in debounce locks prevent infinite loops when local controls interact with incoming remote triggers.

3. **Live Chat & Viewer Presence:**
   - Chat messages are stored in a subcollection under each room and updated instantly using real-time listeners.
   - User presence is tracked via periodic heartbeats, dynamically updating the active viewer count and participant list.

4. **Peer-to-Peer (P2P) Stream & Audio Sharing:**
   - When sharing a browser tab using the screen/audio share feature, a WebRTC peer connection is established directly between browsers to stream video and audio feeds seamlessly without heavy server bandwidth.

---

## 🚀 Getting Started Locally

If you want to run or modify the project locally:

1. Clone or download the repository containing `index.html`.
2. Open `index.html` in your favorite code editor (like VS Code).
3. Run it using a local development server (such as the **Live Server** extension in VS Code) to test multiple browser windows side by side.
