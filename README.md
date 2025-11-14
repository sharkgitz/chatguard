# 🛡️ ChatGuard - AI-Powered Content Detection

A full-stack real-time chat application with advanced AI-powered content detection to identify deepfakes, fake news, and AI-generated text.

![React](https://img.shields.io/badge/React-19.1-blue?logo=react)
![Python](https://img.shields.io/badge/Python-3.8+-green?logo=python)
![FastAPI](https://img.shields.io/badge/FastAPI-Latest-teal?logo=fastapi)
![Firebase](https://img.shields.io/badge/Firebase-Latest-orange?logo=firebase)
![License](https://img.shields.io/badge/License-MIT-green)

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Running the Application](#-running-the-application)
- [API Documentation](#-api-documentation)
- [Configuration](#-configuration)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)

## ✨ Features

### 💬 Real-Time Chat
- **Instant Messaging**: Live chat between users with real-time synchronization
- **User Discovery**: Browse and connect with other registered users
- **Message History**: Persistent message storage with Firestore
- **Responsive Design**: Mobile-friendly UI built with Tailwind CSS

### 🔍 AI Content Detection
- **Deepfake Detection**: Identifies AI-manipulated images using VGG16 deep learning model
- **Fake News Detection**: Analyzes text messages using BERT classifier
- **AI-Generated Text Detection**: Detects AI-generated content using RoBERTa model
- **Smart Filtering**: Ignores casual messages to reduce false positives

### 🔐 Security
- **Firebase Authentication**: Secure user registration and login
- **CORS Protection**: Configured API access control
- **File Upload Validation**: Analyzes images before sharing

## 🏗️ Tech Stack

### Frontend
| Technology | Purpose |
|-----------|---------|
| **React 19** | UI framework |
| **Vite** | Build tool & dev server |
| **Tailwind CSS** | Styling |
| **Firebase** | Authentication & Realtime Database |
| **React Router** | Client-side routing |
| **React Icons** | Icon components |
| **Transformers.js** | Client-side ML inference |

### Backend
| Technology | Purpose |
|-----------|---------|
| **Python 3.8+** | Server runtime |
| **FastAPI** | REST API framework |
| **PyTorch** | Deep learning framework |
| **Hugging Face Transformers** | NLP models |
| **Pillow** | Image processing |

### Infrastructure
| Service | Purpose |
|---------|---------|
| **Firebase** | Auth & Firestore database |
| **CUDA** | GPU acceleration (optional) |

## 📂 Project Structure

```
chatguard/
├── client/                          # React Frontend
│   ├── src/
│   │   ├── pages/
│   │   │   ├── Home.jsx            # Main chat interface
│   │   │   ├── Login.jsx           # Login page
│   │   │   ├── Register.jsx        # Registration page
│   │   │   └── StartPage.jsx       # Landing page
│   │   ├── App.jsx                 # Root component with routing
│   │   ├── firebase.js             # Firebase configuration
│   │   ├── main.jsx                # Entry point
│   │   └── App.css                 # Styles
│   ├── public/                     # Static assets
│   ├── package.json
│   ├── vite.config.js
│   ├── tailwind.config.js
│   └── README.md
│
├── server/                          # Python Backend
│   ├── deepfake_api.py            # Deepfake detection API
│   ├── fakenewsaigen_api.py       # Fake news & AI text detection
│   ├── vgg16_deepfake.pth         # Pretrained deepfake model
│   ├── requirements.txt           # Python dependencies
│   └── __pycache__/
│
└── README.md                        # This file
```

## 🔧 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v16 or higher) - [Download](https://nodejs.org/)
- **Python** (3.8 or higher) - [Download](https://www.python.org/)
- **Git** - [Download](https://git-scm.com/)
- **pip** (Python package manager - comes with Python)

### Optional
- **CUDA** (for GPU acceleration of PyTorch models)

## 📦 Installation

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/sharkgitz/chatguard.git
cd chatguard
```

### 2️⃣ Backend Setup

Navigate to the server directory and set up the Python environment:

```bash
cd server

# Create a virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\Activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Fix the typo in requirements (if needed)
pip install python-multipart
```

**Important**: Make sure `vgg16_deepfake.pth` exists in the server directory.

### 3️⃣ Frontend Setup

Navigate to the client directory:

```bash
cd ../client

# Install dependencies
npm install
```

## 🚀 Running the Application

### Option 1: Run All Services (Recommended for Development)

Open **three separate terminals** and run:

**Terminal 1 - Deepfake Detection API** (Port 8000)
```bash
cd server
venv\Scripts\Activate  # Windows: or source venv/bin/activate on Mac/Linux
uvicorn deepfake_api:app --port 8000 --reload
```

**Terminal 2 - Fake News & AI Text Detection API** (Port 8001)
```bash
cd server
venv\Scripts\Activate
uvicorn fakenewsaigen_api:app --port 8001 --reload
```

**Terminal 3 - React Frontend** (Port 5173)
```bash
cd client
npm run dev
```

### Option 2: Run with npm Scripts (If configured)

```bash
npm run dev          # Start Vite dev server
npm run build        # Build for production
npm run preview      # Preview production build
npm run lint         # Run ESLint
```

## 🌐 Access the Application

Once all services are running, open your browser and navigate to:

```
http://localhost:5173
```

### Usage Flow

1. **Register** a new account on the `/register` page
2. **Login** with your credentials
3. **View users** on the home page
4. **Start chatting** - Messages are automatically analyzed for:
   - ⚠️ Fake news
   - 🤖 AI-generated text
   - 🎭 Deepfake images
5. **Flags appear** when suspicious content is detected

## 📡 API Documentation

### Deepfake Detection API

**Endpoint:** `POST /detect-deepfake`  
**Port:** 8000

**Request:**
```bash
curl -X POST "http://localhost:8000/detect-deepfake" \
  -F "file=@image.jpg"
```

**Response:**
```json
{
  "isDeepfake": false
}
```

### Fake News & AI Text Detection API

**Endpoint:** `POST /analyze-text`  
**Port:** 8001

**Request:**
```bash
curl -X POST "http://localhost:8001/analyze-text" \
  -H "Content-Type: application/json" \
  -d '{"text": "Your message here"}'
```

**Response:**
```json
{
  "message": "Your message here",
  "fake_news": {
    "label": "FAKE",
    "score": 0.95
  },
  "ai_generated": {
    "label": "AI",
    "score": 0.87
  },
  "flags": ["FAKE_NEWS", "AI_GENERATED"]
}
```

## ⚙️ Configuration

### Firebase Configuration

Edit `client/src/firebase.js` to use your own Firebase project:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_AUTH_DOMAIN",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_STORAGE_BUCKET",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

**Steps to get your Firebase credentials:**
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create a new project
3. Enable Authentication (Email/Password)
4. Enable Firestore Database
5. Copy the config from Project Settings

### API Ports Configuration

To change API ports, modify the `port` parameter in the `uvicorn` commands or update the fetch URLs in `client/src/pages/Home.jsx`:

```javascript
// Change these URLs to match your API ports
const res = await fetch("http://localhost:8001/analyze-text", { ... });
const deepfakeRes = await fetch("http://localhost:8000/detect-deepfake", { ... });
```

## 🐛 Troubleshooting

### Common Issues & Solutions

| Issue | Cause | Solution |
|-------|-------|----------|
| `ModuleNotFoundError: torch` | PyTorch not installed | Run `pip install torch torchvision` |
| `Connection refused on port 8000/8001` | APIs not running | Start both FastAPI servers in separate terminals |
| Firebase auth errors | Missing credentials | Update `firebase.js` with your Firebase config |
| `vgg16_deepfake.pth not found` | Model file missing | Download or place the model in `/server` directory |
| CORS errors in browser console | Backend CORS not configured | Verify CORS middleware in `deepfake_api.py` |
| `npm ERR! ERR!` | Node modules issue | Delete `node_modules` and run `npm install` again |
| Slow image processing | GPU not available | Install CUDA for GPU acceleration |

### Debug Mode

Enable verbose logging in `fakenewsaigen_api.py`:

```python
import logging
logging.basicConfig(level=logging.DEBUG)
```

### Check Service Status

```bash
# Check if ports are in use
netstat -ano | findstr :8000  # Windows
lsof -i :8000                  # macOS/Linux
```

## 🔄 Deployment

### Frontend Deployment (Vercel/Netlify)

```bash
cd client
npm run build
# Deploy the 'dist' folder
```

### Backend Deployment (Heroku/Railway/Render)

```bash
cd server
# Create requirements.txt with pinned versions
pip freeze > requirements.txt

# Deploy with Procfile:
web: uvicorn deepfake_api:app --host 0.0.0.0 --port $PORT
web: uvicorn fakenewsaigen_api:app --host 0.0.0.0 --port $PORT
```

## 📝 Environment Variables

Create a `.env` file in both `client/` and `server/` directories:

**client/.env**
```
VITE_API_BASE_URL=http://localhost:8000
VITE_FAKE_NEWS_API_URL=http://localhost:8001
```

**server/.env**
```
PYTORCH_DEVICE=cuda  # or cpu
MODEL_PATH=./vgg16_deepfake.pth
```

## 🤝 Contributing

Contributions are welcome! Here's how to contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code Style

- **Frontend**: ESLint configured in `.eslintrc`
- **Backend**: Follow PEP 8 standards

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👥 Authors

- **Vaishak** - Developer - [@sharkgitz](https://github.com/sharkgitz)

## 🙏 Acknowledgments

- PyTorch team for the deep learning framework
- Hugging Face for NLP models
- Firebase for backend services
- React and Vite communities

## 📞 Support

For issues, questions, or suggestions:

1. Open an [Issue](https://github.com/sharkgitz/chatguard/issues) on GitHub
2. Check existing issues for similar problems
3. Provide detailed reproduction steps

## 🔐 Security Notice

- Never commit Firebase credentials to public repositories
- Use environment variables for sensitive data
- Keep dependencies updated for security patches
- Review AI model outputs before deployment

---

**Made with ❤️ for safer online communication**

Last Updated: November 14, 2025
