# SAM Auto Launcher

**SAM Auto Launcher** is a lightweight Windows desktop application for quickly launching Steam Achievement Manager (SAM) profiles by Steam AppID.

It lets you organize games into custom lists, launch one game manually, launch up to five games at once, and automatically restart them in a controlled cycle.

> **Note:** This application is a launcher for [Steam Achievement Manager (SAM)](https://github.com/gibbed/SteamAchievementManager). It does not include SAM and does not modify game files.

## Features

- Modern dark “terminal-style” interface
- Russian and English interface
- Multiple game lists
- Add games by Steam AppID
- Launch a single game by AppID
- Launch up to 5 games simultaneously
- Automatic restart cycle
- Configurable interval before closing games
- Configurable delay between closing individual games
- Real-time process status
- Settings reset without deleting game lists
- Safe JSON storage for settings and lists

## Requirements

- Windows 10 or later
- Python 3.9+
- Steam Achievement Manager installed
- `ttkbootstrap`

## Installation

1. Install Python from [python.org](https://www.python.org/downloads/).
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Run the application:

```bash
python sam_auto_launcher.py
```

## First Launch

On first launch, the app creates two files:

```text
config.json
lists.json
```

- `config.json` stores application settings.
- `lists.json` stores your game lists.

Set the path to your `SAM.Game.exe` using the **SAM PATH** button.

## Usage

### Launch a game

1. Click a game button in the list.
2. Or enter a Steam AppID in the `AppID` field and press **RUN**.

### Launch several games

Press **LAUNCH ALL**.

The application launches up to **5 games** from the current list.

### Create a game list

1. Press **NEW LIST**.
2. Enter a list name.
3. Press **ADD GAME** to add games.

### Add a game

1. Press **ADD GAME**.
2. Enter the game name.
3. Enter the Steam AppID.

The AppID can be found in the Steam Store page URL:

```text
[https://store.steampowered.com/app/480/](https://store.steampowered.com/app/480/)
                                    ^^^
                                   AppID
```

### Auto cycle

Press **START CYCLE** to enable automatic restarting.

The application will:

1. Launch up to 5 games.
2. Wait for the configured interval.
3. Close games one by one.
4. Wait between each closing action.
5. Restart the games immediately after all have been closed.

If you close a SAM window manually, that game is considered finished and the cycle moves to the next one.

## Settings

Open **SETTINGS** to configure:

| Setting | Description |
|---|---|
| Restart interval | Time before games begin closing |
| Minimum delay | Minimum pause between closing games |
| Maximum delay | Maximum pause between closing games |
| Reset settings | Restores default settings; game lists are not deleted |

## Configuration Files

### config.json

```json
{
  "sam_path": "C:/Path/To/SAM.Game.exe",
  "language": "ru",
  "theme": "darkly",
  "current_list": "default",
  "auto_restart_enabled": false,
  "restart_interval_minutes": 30,
  "close_delay_min_seconds": 10,
  "close_delay_max_seconds": 20
}
```

### lists.json

```json
{
  "default": [
    {
      "name_ru": "Example game",
      "name_en": "Example game",
      "appid": "480",
      "enabled": true
    }
  ]
}
```

## Build a Windows Executable

Install PyInstaller:

```bash
pip install pyinstaller
```

Build a single executable:

```bash
pyinstaller --onefile --noconsole --name "SAM Auto Launcher v2.1" sam_auto_launcher.py
```

Build with a custom icon:

```bash
pyinstaller --onefile --noconsole --icon=icon.ico --name "SAM Auto Launcher v2.1" sam_auto_launcher.py
```

The executable will be created in:

```text
dist/
```

## Project Structure

```text
.
├── sam_auto_launcher.py   # Main application
├── requirements.txt       # Python dependencies
├── README.md              # Documentation
├── LICENSE                # License
└── .gitignore             # Files excluded from Git
```

## Disclaimer

This project is intended for personal use with Steam Achievement Manager.

Using third-party achievement tools may violate Steam’s terms of service or the rules of specific games. Use this software at your own risk.

## License

This project is licensed under the MIT License.
