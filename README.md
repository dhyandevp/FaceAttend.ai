# 📸 FaceAttend.ai: Intelligent Attendance System

> A robust, contactless attendance management solution powered by Computer Vision.

## 🌟 Introduction

**FaceAttend.ai** Automates the traditional attendance process using facial recognition technology. Built with **Python** and **OpenCV**, this system offers a seamless experience for registering students, training a biometric model, and tracking attendance in real-time. It eliminates proxy attendance and saves valuable time in educational or corporate environments.

This project uses the **LBPH (Local Binary Patterns Histograms)** algorithm for accurate face recognition and **Haar Cascade Classifiers** for efficient face detection.

## 🚀 Key Features

*   **⚡ Real-Time Tracking:** Instantly detects and recognizes faces from a live webcam feed.
*   **🛡️ Secure & Accurate:** Uses biometric data to ensure the person is actually present.
*   **📊 Automated Logging:** Automatically saves attendance with `Name`, `ID`, `Date`, and `Time` into daily CSV reports.
*   **📧 Email Reporting:** Built-in feature to email the daily attendance log to administrators with a single click.
*   **🖥️ User-Friendly GUI:** A clean dashboard built with Tkinter for easy management of students and logs.
*   **🧠 Local Processing:** All data and recognition happen locally on your machine—no cloud dependency required.

## 🛠️ Technology Stack

*   **Language:** Python 3.9+
*   **GUI Framework:** Tkinter
*   **Computer Vision:** OpenCV (`cv2`)
*   **Algorithms:**
    *   *Detection:* Haar Cascade Classifier
    *   *Recognition:* LBPH (Local Binary Patterns Histograms)
*   **Data Handling:** Pandas, CSV
*   **Image Processing:** Pillow (PIL)
*   **Notifications:** SMTP (Email)

## 🧠 How It Works (Technical Breakdown)

The system operates in three distinct phases:

### 1. Registration & Data Collection
*   **Goal:** Capture the unique facial features of a user.
*   **Process:** The webcam captures **100 grayscale images** of the user's face.
*   **Why:** Capturing multiple angles and lighting conditions creates a robust dataset for the model to learn from.

### 2. Model Training
*   **Goal:** Teach the system to distinguish between different users.
*   **Algorithm:** **LBPH (Local Binary Patterns Histograms)**.
*   **Method:**
    *   The system reads the training images.
    *   It converts each face into a texture map (binary patterns) to be lighting-invariant.
    *   It creates a histogram (mathematical fingerprint) for each user.
    *   This knowledge is saved into a single lightweight file: `TrainingImageLabel/Trainner.yml`.

### 3. Real-Time Recognition
*   **Goal:** Mark attendance dynamically.
*   **Process:**
    1.  **Detection:** Uses **Haar Cascade** to find *where* the face is.
    2.  **Prediction:** The LBPH recognizer compares the live face with the saved histograms.
    3.  **Logging:** If a match is found (Confidence > 50%), the user is marked present in the daily CSV log.

## ⚙️ Setup & Installation

### Prerequisites
*   Python 3.x installed.
*   A working webcam.

### Step 1: Clone the Repository
```bash
git clone https://github.com/yourusername/FaceAttend.ai.git
cd FaceAttend.ai
```

### Step 2: Install Dependencies
Run the following pip command to install the required libraries:
```bash
pip install opencv-contrib-python numpy pandas pillow
```
*(Note check `requirements.txt` if available)*

### Step 3: Configure
Open `config.ini` (or edit `main.py` directly if preferred) to set your preferences:
*   **Email:** Set your sender email and app password for reports.
*   **Camera:** Change `CAMERA_INDEX` if you use an external webcam (default is 0).

## 🕹️ User Guide

1.  **Run the Application:**
    ```bash
    python main.py
    ```
2.  **Register a New User:**
    *   Enter a numeric **ID** and **Name**.
    *   Click **"Take Images"**. Look at the camera until 100 images are captured.
3.  **Train the Model:**
    *   Click **"Train Images"**. Wait for the "Training Complete" message.
4.  **Start Attendance:**
    *   Click **"Take Attendance"**.
    *   The webcam will open. Recognized faces will show their name and confidence score.
    *   Press **`q`** to stop tracking.
5.  **View & Email Logs:**
    *   The main dashboard shows today's log.
    *   Click **"Email Today's Report"** to send it instantly.

## 📂 Project Structure

```
FaceAttend.ai/
│
├── Attendance/              # Stores daily CSV attendance logs
├── StudentDetails/          # Stores the list of registered IDs and Names
├── TrainingImage/           # Raw captured images for training
├── TrainingImageLabel/      # Stores the trained model (Trainner.yml)
├── main.py                  # Main application source code
├── config.ini               # Configuration file (Email, etc.)
├── haarcascade...xml        # Pre-trained face detector model
└── README.md                # Project documentation
```

## 🔮 Future Roadmap
*   [ ] Integration with SQL Database.
*   [ ] Web-based Dashboard (React/Django).
*   [ ] Hardware integration (Arduino) for door access control.

---
*Created for the Computer Science Evaluation Project.*

