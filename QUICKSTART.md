# 🚀 Quick Start Guide - ChatGuard

Get up and running with ChatGuard in 10 minutes!

## Prerequisites

- Node.js 16+ ([Download](https://nodejs.org/))
- Python 3.8+ ([Download](https://www.python.org/))
- Git ([Download](https://git-scm.com/))

## Step 1: Clone the Repository

```bash
git clone https://github.com/sharkgitz/chatguard.git
cd chatguard
```

## Step 2: Set Up Backend

```bash
cd server

# Create virtual environment
python -m venv venv

# Activate it
# Windows:
venv\Scripts\Activate
# macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
pip install python-multipart
```

## Step 3: Set Up Frontend

```bash
cd ../client
npm install
```

## Step 4: Configure Firebase (Optional)

If you want to use your own Firebase project:

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create a new project
3. Enable Authentication and Firestore
4. Copy your config
5. Update `client/src/firebase.js` with your credentials

## Step 5: Run the Application

Open **3 terminals** in the project root:

### Terminal 1: Deepfake Detection API
```bash
cd server
venv\Scripts\Activate
uvicorn deepfake_api:app --port 8000 --reload
```

### Terminal 2: Fake News Detection API
```bash
cd server
venv\Scripts\Activate
uvicorn fakenewsaigen_api:app --port 8001 --reload
```

### Terminal 3: Frontend
```bash
cd client
npm run dev
```

## Step 6: Access the App

Open your browser and go to: **http://localhost:5173**

## First Time Setup

1. Click **Register** and create an account
2. **Login** with your credentials
3. Browse **Users** and start chatting
4. Messages are automatically checked for:
   - 🎭 Deepfake images
   - 📰 Fake news
   - 🤖 AI-generated text

## Troubleshooting

**PyTorch installation stuck?**
```bash
pip install torch torchvision --index-url https://download.pytorch.org/whl/cpu
```

**Ports already in use?**
```bash
# Change port in uvicorn command
uvicorn deepfake_api:app --port 9000 --reload
# Update fetch URLs in Home.jsx accordingly
```

**CORS errors?**
- Ensure both backend servers are running
- Check CORS settings in `deepfake_api.py` and `fakenewsaigen_api.py`

**Firebase errors?**
- Check internet connection
- Verify Firebase credentials in `firebase.js`

## Performance Tips

- Use GPU acceleration: Install CUDA for PyTorch
- Clear browser cache if experiencing issues
- Run backends on separate machines for production

## Next Steps

- Check [README.md](README.md) for full documentation
- See [CONTRIBUTING.md](CONTRIBUTING.md) to contribute
- Read the main README for API documentation

---

**Need help?** Open an [issue](https://github.com/sharkgitz/chatguard/issues) on GitHub!
