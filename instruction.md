# Music App Development Instructions (Expo Version)

## Overview
This document provides a step-by-step guide to building a music player application using React Native with **Expo**. The app will support local music playback, playlist management, and downloading music files to the app's storage.

## Prerequisites
- Node.js installed
- Expo development environment set up
- Basic knowledge of React Native and JavaScript

## Step 1: Project Initialization
1. Initialize the project using Expo:
   ```bash
   npx expo init music-app
   ```
2. Navigate to the project directory:
   ```bash
   cd music-app
   ```
3. Start the Expo development server:
   ```bash
   npx expo start
   ```

## Step 2: Install Required Dependencies
Install the necessary libraries:
- Navigation: `react-navigation`
- Music playback: `expo-av`
- Local file management: `expo-file-system`
- Database storage: `expo-sqlite`
- State management (optional): Redux or Context API

```bash
npx expo install react-navigation expo-av expo-file-system expo-sqlite
```

## Step 3: Set Up Navigation
1. Install React Navigation dependencies.
2. Configure a basic stack navigator.
3. Create screens for:
   - Home (Song list)
   - Player
   - Playlist management

## Step 4: Implement Music Playback
1. Set up `expo-av` for audio playback.
2. Implement play, pause, next, previous controls.
3. Display song metadata (title, artist, album art).

## Step 5: Manage Playlists
### 5.1. Install SQLite Dependency
- `expo-sqlite` is already included in Expo projects, install it if not available:
  ```bash
  npx expo install expo-sqlite
  ```

### 5.2. Set Up Database Connection
- Open or create an SQLite database.
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
1. Use `expo-file-system` to manage file storage.
2. Implement a function to download MP3 files from a given URL.
3. Save downloaded files in the app’s directory.

```bash
npx expo install expo-file-system
```

## Step 7: Fetch Local Music Files
1. Access device storage to list available MP3 files.
2. Filter and display relevant music files in the app.
3. Allow users to add local songs to playlists.

## Step 8: UI & UX Enhancements
1. Improve UI with React Native components.
2. Add animations for better user experience.
3. Optimize layout for different screen sizes.

## Step 9: Testing & Debugging
1. Test the app using Expo Go on a physical device.
2. Debug common React Native issues.
3. Optimize performance and fix bugs.

## Step 10: Build & Deployment
1. Build APK or IPA for testing:
   ```bash
   eas build -p android
   ```
   or
   ```bash
   eas build -p ios
   ```
2. Prepare for Play Store & App Store submission.
3. Follow platform-specific guidelines for publishing.

## Conclusion
This guide outlines the structured steps for building a React Native music player app using **Expo**. Further optimizations can be added based on user requirements.

