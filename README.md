# Pico Face Tracker

**Real-time camera streaming from Pico 4 Enterprise to PC over WiFi**

A simple Android app that captures camera feed from Pico 4 Enterprise VR headset and streams it wirelessly to any PC on the same network. Perfect for face tracking, computer vision projects, or remote monitoring.

## 🚀 Features

- **Real-time camera streaming** from Pico 4 Enterprise
- **WiFi broadcasting** - no pairing required
- **Cross-platform receiver** - Python script works on any PC
- **Low latency** UDP streaming
- **Simple setup** - just install APK and run Python script
- **Multiple viewers** - several PCs can receive the same stream

## 📱 System Requirements

### Pico 4 Enterprise
- Android API 29+ (Android 10.0+)
- Camera permissions
- WiFi connectivity

### PC Receiver
- Python 3.7+
- OpenCV (`pip install opencv-python`)
- NumPy (`pip install numpy`)
- Same WiFi network as Pico 4

## 🛠️ Installation

### Step 1: Install APK on Pico 4
1. Download the APK from the [Releases](../../releases) section
2. Enable Developer Mode on your Pico 4 Enterprise
3. Sideload the APK using:
   - **ADB**: `adb install app-debug.apk`
   - **SideQuest**: Drag and drop APK file
   - **Direct install**: Download APK on Pico 4 browser and install

### Step 2: Set up Python Receiver on PC
1. Install Python dependencies:
```bash
pip install opencv-python numpy
```

2. Download and run the receiver script:
```bash
python camera_receiver.py
```

## 🎯 Usage

1. **Start the receiver** on your PC:
   ```bash
   python camera_receiver.py
   ```
   
2. **Launch the app** on your Pico 4 Enterprise

3. **Press "Start Camera Stream"** in the app

4. **View the stream** on your PC - it should appear automatically!

Both devices must be connected to the same WiFi network.

## 📡 How It Works

```
Pico 4 Enterprise (Android APK) → WiFi Broadcast → PC (Python Receiver)
```

- **Android app** captures camera frames using Camera2 API
- **UDP broadcasting** sends frames over port 8888
- **Python receiver** listens for broadcasts and displays video
- **No IP configuration needed** - uses network broadcast

## 🔧 Configuration

### Network Settings
- **Default port**: 8888
- **Protocol**: UDP broadcast
- **Format**: Raw camera data / JPEG (auto-detected)

### Camera Settings
- **Resolution**: 640x480 (configurable)
- **Camera**: Front-facing (for face tracking)
- **Format**: YUV420/JPEG

## 📁 Project Structure

```
PicoFaceTracker/
├── app/
│   ├── src/main/
│   │   ├── java/com/yourname/picocamerastreamer/
│   │   │   ├── MainActivity.kt
│   │   │   └── CameraStreamService.kt
│   │   ├── res/layout/
│   │   │   └── activity_main.xml
│   │   └── AndroidManifest.xml
├── camera_receiver.py
└── README.md
```

## 🐛 Troubleshooting

### No video received on PC
- ✅ Check both devices are on same WiFi
- ✅ Verify app has camera permissions
- ✅ Try disabling PC firewall temporarily
- ✅ Check if port 8888 is blocked

### Poor video quality
- 📶 Move closer to WiFi router
- 🔧 Reduce resolution in `CameraStreamService.kt`
- 🚀 Use 5GHz WiFi if available

### App crashes on startup
- 📱 Ensure Android API 29+
- 🔐 Grant camera permissions manually in settings
- 🔄 Reinstall APK

## 🎮 Controls

### Android App
- **Start Camera Stream**: Begin broadcasting
- **Stop Camera Stream**: Stop broadcasting
- **Background service**: Continues streaming when app is minimized

### Python Receiver
- **'q'**: Quit viewer
- **'s'**: Save current frame
- **Ctrl+C**: Stop receiver

## 🔮 Future Enhancements

- [ ] RTMP streaming support
- [ ] Multiple camera selection
- [ ] Video recording on receiver
- [ ] Mobile hotspot support
- [ ] Encryption for secure streaming
- [ ] Web browser receiver (WebRTC)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⚠️ Disclaimer

This project is for educational and development purposes. Ensure you have proper permissions before recording or streaming camera feeds. Respect privacy and follow local regulations regarding camera usage.

## 🙏 Acknowledgments

- Built for Pico 4 Enterprise VR headset
- Uses Android Camera2 API
- OpenCV for Python video processing
- UDP networking for real-time streaming

---

**Made with ❤️ for the VR development community**

*Need help? Open an issue or start a discussion!*