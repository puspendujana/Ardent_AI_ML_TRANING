# 😊 Real-Time Emotion Detection

A lightweight, real-time facial emotion detection system built with **OpenCV** and **Keras** — no DeepFace dependency required. It uses your webcam to detect faces and classify emotions live using a custom-trained CNN model.

---

## 📸 Demo

The system draws a bounding box around each detected face and overlays the predicted emotion label in real time.

---

## 🧠 How It Works

1. **Face Detection** — OpenCV's Haar Cascade classifier (`haarcascade_frontalface_default.xml`) scans each frame for faces.
2. **Preprocessing** — The detected face region is extracted, converted to grayscale, resized to `64×64` pixels, and normalized to `[0, 1]`.
3. **Emotion Classification** — The preprocessed face is fed into a Keras CNN model (`emotion_model.hdf5`) that outputs probabilities across 7 emotion classes.
4. **Display** — The predicted emotion is rendered on screen alongside a green bounding box.

### Detected Emotions

| Label | Emotion |
|-------|---------|
| 😡 | Angry |
| 🤢 | Disgust |
| 😨 | Fear |
| 😄 | Happy |
| 😢 | Sad |
| 😲 | Surprise |
| 😐 | Neutral |

---

## 🗂️ Project Structure

```
├── emotion_detection.py              # Main script
├── haarcascade_frontalface_default.xml  # Haar Cascade face detector
├── emotion_model.hdf5               # Pre-trained Keras emotion model
└── README.md
```

---

## ⚙️ Requirements

- Python 3.7+
- OpenCV
- NumPy
- TensorFlow / Keras

Install dependencies:

```bash
pip install opencv-python numpy tensorflow
```

> **macOS users:** The script uses `cv2.CAP_AVFOUNDATION` for webcam compatibility, which is the correct backend for macOS. No changes needed.

---

## 🚀 Getting Started

1. **Clone the repository**

```bash
git clone https://github.com/your-username/emotion-detection.git
cd emotion-detection
```

2. **Add the model file**

Place your `emotion_model.hdf5` file in the project root. The model should be a CNN trained on a dataset like [FER-2013](https://www.kaggle.com/datasets/msambare/fer2013) expecting `(1, 64, 64, 1)` input tensors.

3. **Run the script**

```bash
python emotion_detection.py
```

4. **Quit** — Press `q` to exit the webcam window.

---

## 🏋️ Training Your Own Model

The script expects a Keras model saved as `.hdf5` with:
- **Input shape:** `(1, 64, 64, 1)` — grayscale, 64×64 pixels
- **Output:** Softmax layer with 7 units (one per emotion class)

A common training dataset for this task is [FER-2013](https://www.kaggle.com/datasets/msambare/fer2013), available on Kaggle.

---

## 🔧 Configuration

| Parameter | Location | Description |
|-----------|----------|-------------|
| `scaleFactor` | `detectMultiScale(gray, 1.3, 5)` | Controls face detection sensitivity |
| `minNeighbors` | `detectMultiScale(gray, 1.3, 5)` | Reduces false positives |
| Input size | `cv2.resize(roi_gray, (64, 64))` | Must match model's expected input |
| Camera index | `cv2.VideoCapture(0, ...)` | Change `0` to use a different camera |

---

## ⚠️ Known Limitations

- Accuracy depends entirely on the quality of the trained model.
- Performance may degrade in low-light conditions or with partial face occlusion.
- The Haar Cascade detector may struggle with non-frontal face angles.

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

---

## 🙏 Acknowledgements

- [OpenCV](https://opencv.org/) for real-time computer vision tools
- [Keras / TensorFlow](https://keras.io/) for deep learning model inference
- [FER-2013 Dataset](https://www.kaggle.com/datasets/msambare/fer2013) for emotion training data
