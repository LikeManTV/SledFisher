# 🎣 SledFisher - A Fishing Bot for Sledding Game
SledFisher is a simple and effective fishing bot created with Python, designed to automate fishing in "Sledding Game". It uses computer vision to detect fish bites by monitoring for motion, rather than specific colors, making it robust and adaptable.

The bot features a user-friendly graphical interface (GUI) for easy setup and real-time status updates.

## ✨ Features
- **Motion Detection:** Uses OpenCV to detect the sudden movement of a fishing bobber, ignoring subtle water animations.
- **Easy Setup UI:** A graphical interface guides you through setting the cast power and selecting the fishing area on your screen. No need to manually edit coordinates in the code.
- **Live Status Overlay:** A small, clean overlay shows the bot's current action (Casting, Watching, etc.).
- **Global Stop Hotkey:** Press the `Esc` key at any time to instantly and safely stop the bot.
- **Automated Installation:** Includes a Windows batch file (`install_requirements.bat`) to automatically check for Python/pip and install all required libraries.
- **Calibration Tool:** Comes with a separate tool (`calibration.bat`) to help you fine-tune motion sensitivity for your specific game and screen resolution.

## ⚙️ How It Works
The bot operates in a simple loop:
1. **Cast:** Simulates a mouse click-and-hold to cast the fishing line.
2. **Set Reference:** Takes a "before" screenshot of the selected fishing area.
3. **Detect Motion:** Rapidly takes new screenshots and compares them to the reference image. It calculates a "motion score" based on the differences.
4. **Catch:** If the motion score spikes above a set threshold (indicating the bobber dipped), it simulates a mouse click to reel in the fish. If no bite occurs within 20 seconds, it automatically recasts.

## 🚀 How to Use SledFisher
Follow these steps to get the fishing bot up and running.

### Step 1: Download the Files
First, download all the files from this GitHub repository. You can do this by clicking the green **"Code"** button and selecting **"Download ZIP"**. Extract the ZIP file to a folder on your computer.

You should have the following key files:
- `fishing_bot.py` (The main bot script)
- `calibration_tool.py` (For fine-tuning sensitivity)
- `install_requirements.bat` (The installer)
- `start_bot.bat` (The launcher)
- `calibration.bat` (The calibration tool)

### Step 2: Install Python & Requirements
Before you can run the bot, you need to install Python and the necessary Python libraries.

#### Part A: Install Python
If you don't already have Python installed, you'll need to get it first.
1. Go to the official Python website: **[python.org/downloads/](https://www.python.org/downloads/)**
2. Download the latest installer for **Python 3**.
3. Run the installer and proceed with the installation.
4. **Important:** On the first screen of the installer, make sure to check the box at the bottom that says **"Add Python to PATH"**. This is crucial for the scripts to work correctly.

#### Part B: Install Bot Libraries
Once Python is installed, you can install the specific libraries for the bot.
1. Navigate to the folder where you extracted the files.
2. **Double-click** the `install_requirements.bat` file.
3. A command prompt window will open. It will automatically check if you have `Python` and `pip` (Python's package installer). If not, it will guide you.
4. Press any key to begin the installation. The script will download and install all the required libraries for you.
5. Once it says **"Installation complete!"**, you can close the window.

### Step 3: In-Game Preparation
1. Start the game and go to any fishing pond on the map.
2. Align yourself with the fishing pond and move your camera up a bit so that you can still cast and see the bobber.
3. Once aligned properly, go into settings and set your **Camera Sensitivity to 0**. This is critical to prevent your view from moving between casts (see screenshot).
4. Equip your fishing rod and press `Tab` to free your mouse cursor.

### Step 4: Run the Bot for the First Time
1. **Double-click** the `start_bot.bat` file to launch the bot.
2. The **Setup UI** will appear.
3. **Set Cast Time:** Enter how long (in seconds) the mouse should be held down to cast. This depends on how far you are from the fishing pond but `0.7` is a good starting point.
4. **Start Selection:** Click the **"Start Region Selection"** button. The UI will then ask you to select the fishing area.
5. **Select Region:**
   - Click once on the **top-left corner** of the area where your bobber will be.
   - Click again on the **bottom-right corner** of that area. Try to keep the box relatively small to improve accuracy.
6. The setup window will disappear, and a small **Status UI** will appear in the top-left corner of your screen. The bot will begin fishing automatically after a 3-second countdown.
7. Press `Tab` again to close the player list before the coutdown ends!

### Stopping the Bot
To stop the bot at any time, simply press the `Esc` key. The script will safely terminate.

## 🔧 Calibrating Motion Sensitivity (Optional)
If the bot is missing bites or reacting to water movement, you need to adjust the `MOTION_THRESHOLD` value inside `fishing_bot.py` file. The calibration tool makes this easy.
1. **Run the Calibration Tool:** Double-click `calibration.bat`.
2. **Select Region:** Use the UI to select your fishing area, just like you did with the main bot.
3. **Analyze the Score:** After a countdown, the **Calibration UI** will appear. Go into your game, cast your line manually, and watch the **"Score"** value in the UI.
   - Note the **highest score** you see from normal water movement (e.g., `45000`).
   - Wait for a fish to bite and note the **spike in the score** (e.g., it jumps to `150000`).
4. **Set Your Threshold:** Choose a number that is safely between the two values. In the example above, `120000` would be a good threshold.
5. **Update the Script:** Open `fishing_bot.py` with a text editor (like Notepad or VSCode), find the `MOTION_THRESHOLD` variable near the top, and change its value to the one you found. Save the file.
Your bot is now perfectly tuned for your game!

## ⚠️ Disclaimer
This script is intended for educational purposes and for use in single-player games where it does not violate any terms of service. Using bots or automation tools in online multiplayer games can result in a ban. Use at your own risk.
