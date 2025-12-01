# Hand Gesture Volume Control 🎚️

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.5+-green.svg)](https://opencv.org/)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-Latest-orange.svg)](https://mediapipe.dev/)
[![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey.svg)](https://www.microsoft.com/windows)

A real-time computer vision application that enables hands-free system volume control using intuitive hand gestures. Built with OpenCV, MediaPipe, and PyCAW, this project demonstrates the practical application of hand tracking technology for human-computer interaction.

![Demo](HciVoliom/assets/demo.gif)






## 🌟 Features

- **Real-time Hand Detection**: Leverages MediaPipe's robust hand tracking model for accurate landmark detection
- **Gesture-Based Control**: Adjusts system volume by measuring the distance between thumb and index finger
- **Visual Feedback**: On-screen volume bar and percentage display for intuitive interaction
- **Performance Monitoring**: Live FPS counter to track application performance
- **Smooth Volume Mapping**: Intelligent scaling from gesture distance to volume levels (0-100%)

## 🎯 How It Works

1. **Hand Detection**: MediaPipe Hands identifies and tracks 21 hand landmarks in real-time
2. **Gesture Recognition**: Calculates Euclidean distance between thumb tip (ID 4) and index finger tip (ID 8)
3. **Volume Mapping**: Maps the calculated distance to system volume range using linear interpolation
4. **Audio Control**: PyCAW library interfaces with Windows Core Audio API to adjust volume levels

## 📋 Prerequisites

- **Operating System**: Windows 10/11 (PyCAW is Windows-specific)
- **Python**: 3.8 or higher
- **Webcam**: Functional camera for hand detection

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/youseffahem/hand-gesture-volume-control.git
cd hand-gesture-volume-control
```

### 2. Create Virtual Environment (Recommended)

```bash
python -m venv venv
venv\Scripts\activate  # On Windows
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

## 📦 Dependencies

```
opencv-python>=4.5.0
mediapipe>=0.8.0
comtypes>=1.1.0
pycaw>=20181226
numpy>=1.19.0
```

## 🎮 Usage

### Quick Start

Run the main volume control application:

```bash
python VolumeControl.py
```

### Basic Hand Tracking Demo

To test hand landmark detection without volume control:

```bash
python BasicHandTrackingDemo.py
```

### Controls

- **Pinch Gesture**: Bring thumb and index finger closer to decrease volume
- **Spread Gesture**: Move thumb and index finger apart to increase volume
- **Press 'Q'**: Exit the application

## 📁 Project Structure

```
hand-gesture-volume-control/
│
├── assets/                    # Contains demo.gif 
│   ├── demo.gif
│
├── HandTrackingModule.py      # Reusable hand detector class (MediaPipe wrapper)
├── VolumeControl.py           # Main application with volume control logic
├── BasicHandTrackingDemo.py   # Standalone hand tracking visualization
├── requirements.txt           # Python package dependencies
├── README.md                  # Project documentation
└── .gitignore                 # Git ignore rules

```

## 🔧 Configuration

### Adjust Detection Confidence

Modify parameters in `HandTrackingModule.py`:

```python
detector = handDetector(
    mode=False,
    maxHands=1,
    detectionCon=0.7,  # Detection confidence threshold (0.0 - 1.0)
    trackCon=0.7       # Tracking confidence threshold (0.0 - 1.0)
)
```

### Customize Volume Range

Edit mapping parameters in `VolumeControl.py`:

```python
# Adjust min/max distance thresholds for gesture recognition
minDistance = 50   # Minimum distance (pixels)
maxDistance = 300  # Maximum distance (pixels)
```

## 🛠️ Technical Details

### Hand Tracking Module

The `handDetector` class provides a clean interface for:
- Hand detection and landmark extraction
- Position tracking with pixel coordinates
- Distance calculation between landmarks
- Configurable confidence thresholds

### Volume Control Logic

```python
# Distance to volume mapping
volume = np.interp(distance, [minDist, maxDist], [minVol, maxVol])
volumeBar = np.interp(distance, [minDist, maxDist], [400, 150])
volumePercentage = np.interp(distance, [minDist, maxDist], [0, 100])
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 To-Do

- [ ] Add gesture recognition for play/pause media
- [ ] Implement brightness control with alternative gestures
- [ ] Support for Linux/macOS using alternative audio libraries
- [ ] Add gesture customization through config file
- [ ] Implement hand gesture recording and playback

## 🐛 Known Issues

- Performance may vary based on lighting conditions
- Requires adequate distance from camera (30-100 cm recommended)
- Background complexity can affect detection accuracy

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [MediaPipe](https://mediapipe.dev/) - Google's ML framework for hand tracking
- [PyCAW](https://github.com/AndreMiras/pycaw) - Python Core Audio Windows Library
- [OpenCV](https://opencv.org/) - Computer vision library

## 📧 Contact

**Yousef Fahem**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/yousef-fahem)
[![Email](https://img.shields.io/badge/Email-Contact-red?style=flat&logo=gmail)](mailto:yousef.fahem11@gmail.com)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-Chat-green?style=flat&logo=whatsapp)](https://wa.me/201060996576)

- 📧 Email: yousef.fahem11@gmail.com
- 💼 LinkedIn: [linkedin.com/in/yousef-fahem](https://www.linkedin.com/in/yousef-fahem)
- 📱 WhatsApp: +20 106 099 6576

Project Link: [https://github.com/youseffahem/hand-gesture-volume-control](https://github.com/youseffahem/hand-gesture-volume-control)

---

⭐ **Star this repository if you found it helpful!**
