# Music App Development Instructions

## Overview
This document provides a step-by-step guide to building a music player application using React Native. The app will support local music playback, playlist management, and downloading music files to the app's storage.

## Prerequisites
- Node.js installed
- React Native development environment set up
- Basic knowledge of React Native and JavaScript

## Step 1: Project Initialization
1. Choose between **Expo** or **React Native CLI**.
2. Initialize the project:
   - If using Expo: `npx expo init music-app`
   - If using React Native CLI: `npx react-native init MusicApp`
3. Navigate to the project directory: `cd music-app`

## Step 2: Install Required Dependencies
Install the necessary libraries:
- Navigation: `react-navigation`
- Music playback: `react-native-track-player`
- Local file management: `react-native-fs`
- Database storage: `react-native-sqlite-storage`
- State management (optional): Redux or Context API

## Step 3: Set Up Navigation
1. Install React Navigation dependencies.
2. Configure a basic stack navigator.
3. Create screens for:
   - Home (Song list)
   - Player
   - Playlist management

## Step 4: Implement Music Playback
1. Set up `react-native-track-player`.
2. Configure the playback service.
3. Implement play, pause, next, previous controls.
4. Display song metadata (title, artist, album art).

## Step 5: Manage Playlists
### 5.1. Install SQLite Dependency
- Install `react-native-sqlite-storage` to handle local storage:  
  ```bash
  npm install react-native-sqlite-storage
  ```

### 5.2. Set Up Database Connection
- Create a database file and initialize a connection:
  - Open or create a SQLite database.
  - Define a function to establish a database connection.

### 5.3. Create Playlist Table
- Define a schema for storing playlists:
  ```sql
  CREATE TABLE IF NOT EXISTS playlists (
      id INTEGER PRIMARY KEY AUTOINCREMENT,
      name TEXT NOT NULL
  );
  ```

### 5.4. Create Songs Table
- Define a schema for storing songs and their relation to playlists:
  ```sql
  CREATE TABLE IF NOT EXISTS songs (
      id INTEGER PRIMARY KEY AUTOINCREMENT,
      title TEXT NOT NULL,
      artist TEXT,
      filePath TEXT NOT NULL,
      playlist_id INTEGER,
      FOREIGN KEY (playlist_id) REFERENCES playlists(id)
  );
  ```

### 5.5. Implement CRUD Operations
- **Create a playlist:** Insert a new playlist into the database.
- **Retrieve playlists:** Fetch all playlists.
- **Add a song to a playlist:** Insert song metadata with a reference to a playlist.
- **Remove a song from a playlist:** Delete an entry from the `songs` table.
- **Delete a playlist:** Remove a playlist and its associated songs.

### 5.6. Integrate with React Native UI
- Display playlists in the UI.
- Allow users to select and add songs to playlists.
- Implement a button for creating and deleting playlists.

## Step 6: Enable File Downloads
1. Use `react-native-fs` to manage file storage.
2. Implement a function to download MP3 files from a given URL.
3. Save downloaded files in the app’s directory.

## Step 7: Fetch Local Music Files
1. Access device storage to list available MP3 files.
2. Filter and display relevant music files in the app.
3. Allow users to add local songs to playlists.

## Step 8: Background Playback & Media Controls
1. Configure `react-native-track-player` for background audio.
2. Implement lock screen media controls.
3. Handle app lifecycle events for uninterrupted playback.

## Step 9: UI & UX Enhancements
1. Improve UI with React Native components.
2. Add animations for better user experience.
3. Optimize layout for different screen sizes.

## Step 10: Testing & Debugging
1. Test the app on physical Android & iOS devices.
2. Debug common React Native issues.
3. Optimize performance and fix bugs.

## Step 11: Build & Deployment
1. Build APK or IPA for testing.
2. Prepare for Play Store & App Store submission.
3. Follow platform-specific guidelines for publishing.

## Conclusion
This guide outlines the structured steps for building a React Native music player app. Further optimizations can be added based on user requirements.

