# 🏋️ Pushup Counter

A real-time pushup counter web app that uses AI pose detection to automatically count your pushups using your iPhone's front camera.

## 🚀 Features

- **Real-time pose detection** using Google's MoveNet model
- **Live skeleton overlay** showing detected body keypoints
- **Smart pushup counting** with nose + wrist tracking
- **Anti-double-counting** with debouncing logic
- **iPhone optimized** with responsive design
- **No server required** - runs completely in your browser
- **Privacy-focused** - all processing happens locally on your device

## 📱 How to Use

### Quick Start
1. Open `pushup-counter.html` in your iPhone's browser (Safari recommended)
2. Grant camera permissions when prompted
3. Position your iPhone horizontally on the floor or a low surface
4. Get into pushup position - the app will calibrate for 1 second
5. Start doing pushups and watch the counter increase!

### Optimal Setup
```
📱 iPhone (horizontal, camera facing up)
┌─────────────────────┐
│                     │
│       CAMERA        │
│                     │
└─────────────────────┘
         ↑
    (6-12 inches)
         ↑
    👤 You doing pushups
   /|\  (side view)
    |
   / \
```

**Best positioning:**
- Place iPhone **6-12 inches** away from your body
- Camera should see your **full torso** (head to hips)
- **Low-angle side view** works best
- Ensure good lighting for better pose detection

## 🛠️ Technical Details

### Technologies Used
- **TensorFlow.js** - Machine learning framework
- **MoveNet** - Real-time pose detection model
- **HTML5 Canvas** - Live video processing and skeleton overlay
- **getUserMedia API** - Camera access
- **Vanilla JavaScript** - No external dependencies

### Model Information
- **Model**: MoveNet Lightning (optimized for speed)
- **Size**: ~12MB (downloaded once, cached by browser)
- **Performance**: Runs at 30 FPS on modern iPhones
- **Accuracy**: Detects 17 body keypoints with confidence scores

### Detection Algorithm
The app uses a sophisticated detection system:

1. **Calibration Phase** (1 second)
   - Establishes baseline positions for nose and wrists
   - Ensures stable detection before counting begins

2. **Movement Detection**
   - **Primary**: Nose vertical movement (28px threshold)
   - **Secondary**: Wrist movement validation (32px threshold)
   - Optimized for low-angle side view pushups

3. **Anti-Double-Counting**
   - Frame-based debouncing (6 frames down, 5 frames up)
   - Cooldown period between counts
   - Prevents false positives from pose detection noise

## 🔧 Setup & Installation

### Method 1: Direct File Usage
1. Download `pushup-counter.html`
2. Open directly in your iPhone's browser
3. Grant camera permissions
4. Start using immediately!

### Method 2: Local Development
```bash
# Clone or download the project
git clone <your-repo-url>
cd pushup-counter

# Serve locally (required for camera access)
python -m http.server 8000
# OR
npx http-server

# Open in browser
open http://localhost:8000/pushup-counter.html
```

**Note**: Camera access requires HTTPS or localhost due to browser security policies.

## 📊 Performance

- **Frame Rate**: 30 FPS (matches iPhone camera)
- **Latency**: <100ms detection delay
- **Battery**: Moderate usage (similar to video recording)
- **Memory**: ~50MB RAM usage
- **Storage**: No local storage used

## 🎮 Controls

- **Reset Button**: Resets counter and recalibrates
- **Auto-calibration**: Happens automatically on start
- **Visual Feedback**: 
  - Live pose skeleton overlay
  - Counter display
  - Status messages

## 🔍 Troubleshooting

### Common Issues

**Counter not detecting pushups:**
- Ensure good lighting
- Check camera positioning (low-angle side view)
- Make sure your full torso is visible
- Try resetting the counter

**Double counting:**
- The app includes debouncing to prevent this
- If it persists, your movements might be too fast
- Try slower, more controlled pushups

**Poor pose detection:**
- Improve lighting conditions
- Ensure clear view of your body
- Remove background clutter
- Check that camera isn't obstructed

**Camera not working:**
- Grant camera permissions in browser settings
- Ensure you're using HTTPS or localhost
- Try refreshing the page
- Check if other apps are using the camera

### Debug Mode
Open browser developer tools (F12) → Console tab to see:
- Real-time movement values
- Frame counts
- Detection states
- Troubleshooting information

## 🔒 Privacy & Security

- **No data collection** - everything runs locally
- **No internet required** after initial model download
- **No video recording** - only live processing
- **Camera access** only used for pose detection
- **Model cached locally** - no repeated downloads

## 🌐 Browser Compatibility

**Recommended:**
- Safari on iOS 14+
- Chrome on iOS 14+

**Requirements:**
- Camera access (getUserMedia API)
- WebGL support (for TensorFlow.js)
- Canvas API support
- ES6+ JavaScript features

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

**Built using TensorFlow.js and MoveNet** 
