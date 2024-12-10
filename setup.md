# Setting up Spotify to YouTube Music Transfer

## Prerequisites
- Python environment
- Internet connection
- Spotify account
- YouTube Music account

## Installation

1. Install required package:
```bash
pip3 install requirements.txt
```

## Steps to Transfer Music

### 1. Export Spotify Playlists
Run the following command to create `playlists.json`:
```bash
python3 spotify_backup.py playlists.json --dump=liked,playlists --format=json
```

### 2. Authenticate with YouTube Music

1. Run authentication command:
```bash
ytmusicapi browser
```

2. Follow these steps:
    - Open https://music.youtube.com/
    - Navigate to Libraries tab
    - Open Network tab in developer tools
    - Find request containing 'browse?ctoken'
    - Copy all request headers
    - Paste in terminal
    - Press Enter followed by Ctrl + D

This will create `browser.json` file.

### 3. File Path Configuration
If encountering file path errors, use absolute paths for:
- browser.json
- playlists.json

### 4. Transfer Liked Songs
Execute the transfer command:
```bash
python3 -m spotify2ytmusic load_liked
```