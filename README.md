<img width="1920" height="1080" alt="Screenshot (19)" src="https://github.com/user-attachments/assets/ca1b3244-63f6-4c27-8599-530e9006e10f" />
# 🌿 Plant Disease Detector

An AI-powered Android application built with **Flutter, TensorFlow Lite, and MobileNetV2** to identify plant diseases from leaf images. Users can select an image from their gallery or capture one using their camera and receive a predicted disease class with a confidence score.

## ✨ Features

* 📷 **Camera Integration** — Capture plant leaf images directly.
* 🖼️ **Gallery Support** — Select existing images from your device.
* 🤖 **AI-Powered Classification** — Predicts plant diseases using a trained MobileNetV2 model.
* ⚡ **On-Device Inference** — Runs predictions locally using TensorFlow Lite.
* 📊 **Confidence Score** — Displays the model's highest predicted probability.
* 🌱 **15 Classification Classes** — Supports pepper, potato, and tomato health conditions and diseases.
* 📱 **Flutter UI** — A mobile interface built with Flutter and Dart.

## 🛠️ Tech Stack

| Technology         | Purpose                           |
| ------------------ | --------------------------------- |
| Flutter            | Cross-platform mobile UI          |
| Dart               | Application programming language  |
| TensorFlow / Keras | Model training and development    |
| MobileNetV2        | Image classification architecture |
| TensorFlow Lite    | On-device model inference         |
| `tflite_flutter`   | Run the TFLite model in Flutter   |
| `image_picker`     | Capture or select images          |
| `image`            | Image decoding and resizing       |
| PlantVillage       | Plant leaf image dataset          |

## 🧠 Model Information

* **Architecture:** MobileNetV2 with transfer learning and fine-tuning
* **Input shape:** `224 × 224 × 3`
* **Output classes:** 15
* **Input format:** RGB image pixels represented as float32 values
* **Deployment format:** TensorFlow Lite (`.tflite`)
* **Inference:** On-device

The model predicts a probability for each supported class. The application selects the class with the highest predicted probability and maps its output index to the corresponding disease name using `class_names.json`.

> The displayed confidence is the model's predicted probability, not a guarantee that the diagnosis is correct.

<img width="720" height="1600" alt="WhatsApp Image 2026-10-09 at 6 54 19 AM" src="https://github.com/user-attachments/assets/71e50319-f52a-40af-8457-682e5cab7b12" />
<img width="1024" height="873" alt="late_blight_tomato_leaf3x1200-1024x873" src="https://github.com/user-attachments/assets/b5191f41-8b4d-4268-a550-34892cfe4371" />
<img width="1920" height="1080" alt="Screenshot (20)" src="https://github.com/user-attachments/assets/760f2167-c343-47cb-9dde-7ad5b35c6110" />
## 🌿 Supported Classes

### Pepper

* Bacterial spot
* Healthy

### Potato

* Early blight
* Late blight
* Healthy

### Tomato

* Bacterial spot
* Early blight
* Late blight
* Leaf Mold
* Septoria leaf spot
* Spider mites
* Target Spot
* Tomato Yellow Leaf Curl Virus
* Tomato mosaic virus
* Healthy

## 📂 Project Structure

```text
plant-disease-detector/
├── android/
├── assets/
│   └── model/
│       ├── PlantVillage_MobileNetV2_final.tflite
│       └── class_names.json
├── lib/
│   └── main.dart
├── test/
├── pubspec.yaml
├── pubspec.lock
├── analysis_options.yaml
├── .gitignore
└── README.md
```

## 🚀 Getting Started

### Prerequisites

Install the following:

* [Flutter SDK](https://docs.flutter.dev/get-started/install)
* [Android Studio](https://developer.android.com/studio) or an Android device configured for Flutter development
* Git

Check your setup:

```bash
flutter doctor
```

### 1. Clone the repository

```bash
git clone https://github.com/Husnain03066365225/plant-disease-detector.git
cd plant-disease-detector
```


### 2. Install dependencies

```bash
flutter pub get
```

### 3. Verify the model assets

Ensure these files exist:

```text
assets/model/PlantVillage_MobileNetV2_final.tflite
assets/model/class_names.json
```

The asset paths must also be registered in `pubspec.yaml`.

### 4. Connect an Android device

Enable Developer Options and USB debugging on your phone, connect it to your computer, and check:

```bash
flutter devices
```

### 5. Run the application

```bash
flutter run
```
<img width="1920" height="1080" alt="Screenshot (18)" src="https://github.com/user-attachments/assets/0e92971a-3774-4a28-9dd3-d68f63452122" />

## 🔬 How It Works

1. The user captures a leaf image or selects one from the gallery.
2. The application decodes the selected image.
3. The image is resized to `224 × 224` pixels.
4. RGB pixel values are prepared in the input tensor format expected by the model.
5. The TensorFlow Lite interpreter runs inference on the image.
6. The model returns probabilities for 15 classes.
7. The application selects the class with the highest probability.
8. The class index is mapped to a readable disease name, and the prediction with its confidence score is displayed.

### Preprocessing Note

The deployed model includes its MobileNetV2 preprocessing layer. The Flutter application therefore supplies RGB pixel values in the expected `0–255` range and does not apply a second normalization or preprocessing step.

## 📈 Model Evaluation

The project was evaluated using a separate test split in the model development workflow.

* **Previously recorded test accuracy:** 93.36%
* **Previously recorded test loss:** 0.1919

These are the recorded results from the Keras model evaluation. Re-run evaluation against the saved model and test dataset if you need to reproduce them. The Flutter app's displayed confidence is not the same as test accuracy.

## 🔐 Privacy and Connectivity

Image classification is performed locally on the device using the bundled TensorFlow Lite model. The prediction workflow does not require sending leaf images to a remote inference server.

## ⚠️ Limitations

* Predictions are limited to the 15 classes supported by the trained model.
* Results can be affected by lighting, image quality, backgrounds, and leaves that differ from the training data.
* A high confidence score does not guarantee a correct diagnosis.
* The application is an educational decision-support project, not a substitute for professional agricultural advice.

## 🔮 Future Improvements

* Display the top three predicted classes.
* Add treatment and prevention recommendations for each disease.
* Improve image quality checks and handling of unsupported plant species.
* Add prediction history and image storage.
* Optimize inference speed and app size.
* Test on a wider range of real-world field images.

## 👨‍💻 Author

**YOUR NAME**

* GitHub: https://github.com/Husnain03066365225

---

*Built with Flutter, TensorFlow Lite, and MobileNetV2.* 🌱
