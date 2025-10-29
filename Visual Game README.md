# 🎮 VisualGame - Interactive Computer Vision Games

A collection of interactive games and visual applications powered by Pygame and OpenCV, featuring hand tracking, real-time image processing, and gesture-based controls. Experience gaming through computer vision!

## 📖 Overview

VisualGame combines the power of Pygame for game development with OpenCV for computer vision to create unique interactive experiences. Using your webcam and hand tracking, you can play games without touching a keyboard or mouse - just use your hands!

This project demonstrates the integration of computer vision libraries with game development frameworks, showcasing real-time hand detection, image processing filters, and interactive GUI design.

## ✨ Features

### 🎯 Interactive Games
- **Balloon Pop Game** - Pop balloons using hand gestures detected by your webcam
- **Hand Tracking** - Real-time hand detection and finger tracking using cvzone
- **Score System** - Time-based challenges with increasing difficulty
- **Gesture Controls** - Touch-free gaming using computer vision

### 🎨 Visual Applications
- **GUI Filter Panel** - Beautiful custom GUI with toggle switches and sliders
- **Image Transformations** - Real-time image processing effects
- **OpenCV Integration** - Seamless webcam feed integration with Pygame
- **Custom Graphics** - Handcrafted UI elements with shadows and rounded corners

### 🖼️ Image Processing
- **Gray Scale Conversion** - Convert images to grayscale
- **Edge Detection** - Detect edges in real-time video
- **Contour Finding** - Identify object contours
- **Blur Effects** - Apply various blur filters
- **Live Preview** - See effects in real-time

## 🏗️ Architecture

```
┌──────────────┐
│   Webcam     │
└──────┬───────┘
       │
       ▼
┌──────────────────┐
│  OpenCV          │
│  - Capture       │
│  - Processing    │
│  - Hand Detect   │
└──────┬───────────┘
       │
       ▼
┌──────────────────┐
│  cvzone          │
│  Hand Tracking   │
└──────┬───────────┘
       │
       ▼
┌──────────────────┐
│  Pygame          │
│  - Rendering     │
│  - Game Logic    │
│  - UI Elements   │
└──────────────────┘
```

## 🛠️ Technology Stack

| Component | Technology |
|-----------|------------|
| **Game Engine** | Pygame |
| **Computer Vision** | OpenCV (cv2) |
| **Hand Tracking** | cvzone |
| **Image Processing** | NumPy |
| **Language** | Python 3.x |
| **Graphics** | Custom PNG assets |

## 🚀 Getting Started

### Prerequisites
- Python 3.7 or higher
- Webcam (built-in or external)
- Good lighting for hand tracking
- pip (Python package manager)

### Installation

**1. Clone the repository**
```bash
git clone https://github.com/KhonS7/VisualGame.git
cd VisualGame
```

**2. Install dependencies**
```bash
pip install pygame
pip install opencv-python
pip install cvzone
pip install numpy
```

Or use requirements.txt:
```bash
pip install -r requirements.txt
```

**3. Run a game or application**
```bash
# Play the Balloon Pop game
python BalloonPop.py

# Launch the GUI filter panel
python projectGui.py

# Test OpenCV webcam integration
python OpencvIntegrations.py
```

## 🎮 Games & Applications

### 🎈 Balloon Pop Game (`BalloonPop.py`)

Pop balloons using your index finger before they reach the top!

**How to Play:**
1. Run the game
2. Allow webcam access
3. Raise your hand and point your index finger
4. Touch balloons with your finger to pop them
5. Score increases as you pop balloons
6. Game lasts 30 seconds - beat your high score!

**Features:**
- ✅ Hand tracking with cvzone
- ✅ Real-time collision detection
- ✅ Increasing difficulty (balloons get faster)
- ✅ Score tracking
- ✅ Time limit challenge

**Controls:**
- 👆 Index finger - Pop balloons
- ❌ No keyboard needed!

---

### 🎨 Filter GUI (`projectGui.py`)

Beautiful custom GUI for applying image filters with toggles and sliders.

**Features:**
- ✅ Custom-designed interface with rounded corners
- ✅ Toggle switches for filters (Gray Scale, Edges, Contours, Blur)
- ✅ Interactive sliders for parameter adjustment
- ✅ Multiple preview windows
- ✅ Custom color scheme and icons

---

### 📷 OpenCV Integration (`OpencvIntegrations.py`)

Template for integrating OpenCV webcam feed with Pygame.

**Use Cases:**
- Real-time video processing
- Filter applications
- Computer vision prototypes
- AR applications

---

### 📦 Additional Modules

- **AddImage.py** - Add images to Pygame window
- **AddRect.py** - Draw rectangles with custom properties
- **AddText.py** - Render text with custom fonts
- **DrawShapes.py** - Draw various shapes
- **ImageTransformations.py** - Apply image transformations
- **Template.py** - Base template for new Pygame projects

## 📦 Project Structure

```
VisualGame/
│
├── 🎈 BalloonPop.py              # Main balloon popping game
├── 🎨 projectGui.py              # GUI filter panel application
├── 📷 OpencvIntegrations.py      # Webcam integration template
│
├── 📐 DrawShapes.py              # Shape drawing utilities
├── 🖼️ AddImage.py                # Image handling
├── 🔲 AddRect.py                 # Rectangle drawing
├── ✏️ AddText.py                 # Text rendering
├── 🔄 ImageTransformations.py    # Image processing effects
├── 📄 Template.py                # Project template
│
├── 📁 Resources/                 # Assets folder (not included)
│   ├── BalloonRed.png           # Balloon sprite
│   ├── Project - GUI/           # GUI assets
│   │   ├── background.png
│   │   ├── design.png
│   │   ├── icon1-5.png
│   │   ├── shadow.png
│   │   └── toggle*.png
│   └── Marcellus-Regular.ttf    # Custom font
│
├── 📄 requirements.txt           # Python dependencies
└── 📄 README.md                  # You are here!
```

## 🎯 Key Technical Achievements

✅ **Real-Time Hand Tracking** - Accurate finger detection using cvzone  
✅ **Game-CV Integration** - Seamless blend of Pygame and OpenCV  
✅ **Collision Detection** - Precise hit detection between hand and game objects  
✅ **Custom UI Design** - Professional-looking GUI with custom graphics  
✅ **Performance Optimization** - 30 FPS with webcam processing  
✅ **Modular Code** - Reusable components for quick prototyping  

## 💡 Usage Examples

### Creating a New Game

```python
import pygame
import cv2
from cvzone.HandTrackingModule import HandDetector

# Initialize
pygame.init()
window = pygame.display.set_mode((1280, 720))
cap = cv2.VideoCapture(0)
detector = HandDetector(detectionCon=0.8, maxHands=1)

while True:
    success, img = cap.read()
    hands, img = detector.findHands(img, flipType=False)
    
    if hands:
        hand = hands[0]
        x, y = hand['lmList'][8]  # Index finger tip
        # Your game logic here
    
    pygame.display.update()
```

### Adding Custom Filters

```python
import cv2
import numpy as np

# Apply gray scale
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Detect edges
edges = cv2.Canny(gray, 50, 150)

# Find contours
contours, _ = cv2.findContours(edges, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
```

## 🎨 Customization

### Change Game Difficulty
```python
# In BalloonPop.py
speed = 15        # Initial balloon speed
totalTime = 30    # Game duration in seconds
score += 10       # Points per balloon
```

### Adjust Hand Detection Sensitivity
```python
# Adjust detection confidence
detector = HandDetector(detectionCon=0.8, maxHands=1)
# Lower value = more sensitive (0.5 - 1.0)
```

### Modify Colors
```python
# In projectGui.py
c = {
    "lightGreen": (189, 209, 197),
    "lightOrange": (238, 204, 140),
    # Add your custom colors
}
```

## 📚 What You'll Learn

✅ Game development with Pygame  
✅ Computer vision with OpenCV  
✅ Hand tracking and gesture recognition  
✅ Real-time image processing  
✅ Collision detection algorithms  
✅ GUI design and custom graphics  
✅ Event-driven programming  
✅ Frame rate management and optimization  
✅ Integration of multiple libraries  

## 🐛 Troubleshooting

### Webcam Not Working
```bash
# Check if webcam is detected
ls /dev/video*  # Linux/Mac
# or check Device Manager on Windows
```

### Low Frame Rate
- Close other applications using the webcam
- Reduce video resolution in code
- Ensure good lighting (reduces processing time)

### Hand Not Detected
- Improve lighting conditions
- Keep hand in frame
- Lower `detectionCon` value
- Ensure clear background

### Import Errors
```bash
# Reinstall dependencies
pip uninstall opencv-python
pip install opencv-python
pip install cvzone
```

## 🎯 Future Enhancements

- [ ] **Multiple Hand Support** - Track both hands simultaneously
- [ ] **More Games** - Add new gesture-based games
- [ ] **High Score System** - Save and display best scores
- [ ] **Sound Effects** - Add audio feedback
- [ ] **Difficulty Levels** - Easy, Medium, Hard modes
- [ ] **Gesture Library** - Create custom gesture recognizer
- [ ] **Multiplayer Mode** - Two-player games
- [ ] **AR Elements** - Augmented reality features
- [ ] **Mobile Support** - Port to mobile platforms
- [ ] **Record Gameplay** - Save video replays

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/NewGame`)
3. **Commit** your changes (`git commit -m 'Add awesome new game'`)
4. **Push** to the branch (`git push origin feature/NewGame`)
5. **Open** a Pull Request

### Contribution Ideas
- 🎮 Create new games
- 🎨 Design better graphics
- 🐛 Fix bugs
- 📝 Improve documentation
- ⚡ Optimize performance
- 🌐 Add internationalization

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Khon S.**

- GitHub: [@KhonS7](https://github.com/KhonS7)
- LinkedIn: [Khon S.](https://linkedin.com/in/khon-s)
- Email: js14841@nyu.edu

## 🙏 Acknowledgments

- **Pygame Community** - For excellent game development tools
- **OpenCV Team** - For powerful computer vision library
- **cvzone** - For simplified hand tracking
- **NumPy** - For efficient array operations
- **All Contributors** - Thank you for your support!

## Support
- 📖 **Pygame Docs:** [pygame.org](https://www.pygame.org/docs/)
- 📖 **OpenCV Docs:** [docs.opencv.org](https://docs.opencv.org/)

---

⭐ **If you find this project helpful, please give it a star!**

🎮 **Happy Gaming!**

---

⚡ **Interested in my work? Check out my other projects:**
- [AI Code Agent](https://github.com/KhonS7/ai-code-agent) - LLM-powered autonomous coding assistant
- [Stepwise.us](https://github.com/KhonS7/Stepwise.us) - Django blog platform

**Built with ❤️ using Pygame & OpenCV**
