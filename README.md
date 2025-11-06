Aegis-Sec: A Hybrid Crypto-Steganography Tool
Aegis-Sec is a web-based, dual-layer security tool that combines AES-GCM encryption with LSB steganography.
It securely hides secret files within images, ensuring that even if the steganography is detected, 
the underlying data remains computationally secure and unreadable.

This project was developed as an academic requirement,
demonstrating a practical application of hybrid security models in a modern web architecture.

Table of Contents

About The Project
Technology Stack
System Architecture
Getting Started
Prerequisites
Installation
How to Run
Usage
Acknowledgments

About The Project
Traditional steganography (like LSB) provides "security through obscurity." Its greatest weakness is that if the hidden data is ever detected, it is revealed in its original, readable format.

Aegis-Sec solves this problem by integrating a mandatory cryptographic layer. Before any data is hidden, it is first encrypted using the robust AES-GCM algorithm with a user-provided password. This ensures that the hidden data is just meaningless ciphertext, providing true confidentiality.

Features
Dual-Layer Security: Combines AES-256 (GCM) cryptography with LSB steganography.

Data Integrity: AES-GCM authenticates data, protecting it from tampering. A wrong password will fail verification.

Web-Based Interface: An easy-to-use frontend for hiding and extracting files without needing command-line tools.

API-Driven: A decoupled Python/Flask backend handles all processing, making it scalable and modular.

Technology Stack
Backend
Python 3.10

Flask: For the API server.

Flask-CORS: To handle cross-origin requests from the frontend.

PyCryptodome: For robust AES-GCM encryption and PBKDF2 key derivation.

Pillow (PIL): For all image processing and LSB manipulation.

Frontend
HTML5

CSS3

JavaScript (ES6): For API communication (fetch) and DOM manipulation.

System Architecture
The project uses a decoupled frontend-backend architecture.

Frontend: A static web page (HTML/CSS/JS) that runs in the user's browser.

Backend: A Python Flask server that runs locally and exposes API endpoints (e.g., /api/hide, /api/extract).

Ngrok: Used during development to create a secure public HTTPS tunnel to the local Flask server, allowing the frontend to communicate with it.

(You can insert the flow diagram you created here!)

Getting Started
Follow these instructions to get a local copy up and running for development and testing.

Prerequisites
You must have the following software installed:

Python 3.9+

pip (Python package installer)

Ngrok (for connecting the frontend and backend)

Installation
Clone the repository:

Bash

git clone https://github.com/Eternal-prithivi/Cryptography-and-network-security.git
cd Cryptocgraghy-and-network-security
Set up the Backend (in the backend folder):

Bash

cd backend

# Create a virtual environment
python -m venv venv

# Activate it (Windows)
.\venv\Scripts\activate
# (or macOS/Linux: source venv/bin/activate)

# Install required packages
pip install -r requirements.txt
Set up the Frontend: The frontend in the frontend folder requires no installation, only a simple web server to run it.

How to Run
You will need three separate terminals running at the same time.

1. Terminal 1: Run the Backend
Bash

# Make sure you are in the 'backend' folder
# Make sure your virtual environment is active (venv)
python app.py
This will start the Flask server on http://localhost:5000

2. Terminal 2: Run Ngrok
Bash

# Expose your backend's port 5000
ngrok http 5000
Ngrok will give you a public URL (e.g., https://random-string.ngrok.io). Copy this HTTPS URL.

3. Terminal 3: Run the Frontend
Bash

# Go to the 'frontend' folder
cd ../frontend

# Start a simple Python web server
python -m http.server
# (If port 8000 is taken, use: python -m http.server 8001)
4. Final Step: Configure the Frontend
Open the frontend/app.js file in a text editor.

Paste your Ngrok URL (from Terminal 2) into the API_URL constant at the top of the file:

JavaScript

const API_URL = 'https://your-ngrok-url-goes-here.io';
Save the file.

Open your web browser and go to http://localhost:8000 (or whichever port you used in Terminal 3).

The application is now fully running!

Usage
To Hide a File:
Select the Encrypt & Hide card.

Upload a Cover Image (e.g., .png, .jpg).

Upload the Secret File you want to hide (any file type).

Enter a strong Password.

Click Hide File. A new stego-image.png will be downloaded.

To Extract a File:
Select the Decrypt & Extract card.

Upload the Stego-Image (must be the .png you downloaded).

Enter the same Password you used to hide it.

Click Extract File. Your original secret file will be downloaded.

Acknowledgments
A special thanks to Prof. Jesy Janet Kumari for their guidance and support throughout this project.
