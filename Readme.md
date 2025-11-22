<img width="2914" height="1486" alt="image" src="https://github.com/user-attachments/assets/4494bd64-0c60-425a-b18c-f95b9d5b9472" />
<img width="2899" height="1493" alt="image" src="https://github.com/user-attachments/assets/bc84ab38-5302-4c4e-8208-1d073b518b45" />

![Poker Table](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)
![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![GitHub stars](https://img.shields.io/github/stars/EMMA019/AI_pokergame?style=social)
![GitHub forks](https://img.shields.io/github/forks/EMMA019/AI_pokergame?style=social)
![GitHub issues](https://img.shields.io/github/issues/EMMA019/AI_pokergame)
![License](https://img.shields.io/github/license/EMMA019/AI_pokergame)

I'll clean up and restructure your Midnight Luxury Poker documentation to make it more organized and professional:

# 🃏 Midnight Luxury Poker

A sophisticated online Texas Hold'em game featuring a challenging AI opponent that delivers a realistic, real-time poker experience.

## 🌟 Project Overview

"Midnight Luxury Poker" is a web application designed for players to enjoy Texas Hold'em against an intelligent AI opponent. Built on a robust Flask backend with real-time communication via Flask-SocketIO, it offers a seamless gaming experience focused on strategic play.

## 🚀 Key Features

- **💻 Full-Stack Architecture** - Flask backend with SQLAlchemy persistence and responsive frontend
- **📡 Real-Time Gameplay** - Instant game state synchronization using Flask-SocketIO
- **🤖 Intelligent AI Opponent** - Sophisticated poker logic for challenging strategic play
- **⚖️ MIT Licensed** - Free for use, modification, and distribution

## 🛠️ Technology Stack

| Category | Component | Version |
|----------|-----------|---------|
| **Web Framework** | Flask | 2.3.3 |
| **Real-Time Communication** | Flask-SocketIO | 5.3.6 |
| **Database ORM** | SQLAlchemy / Flask-SQLAlchemy | 2.0.25 / 3.1.1 |
| **WSGI Server** | gunicorn / eventlet | 21.2.0 / 0.33.3 |
| **Configuration & Tools** | python-dotenv / Werkzeug | 1.0.1 / 2.3.8 |
| **Frontend** | HTML5, CSS3, JavaScript | - |

## ⚙️ Installation & Setup

### Prerequisites
- Python 3.x
- Virtual environment

### Quick Start

1. **Clone the Repository**
   ```bash
   git clone https://github.com/EMMA019/AI_pokergame.git
   cd AI_pokergame
   ```

2. **Backend Setup**
   ```bash
   # Create virtual environment
   python3 -m venv venv
   
   # Activate virtual environment
   # Linux/macOS:
   source venv/bin/activate
   # Windows:
   .\venv\Scripts\activate
   
   # Install dependencies
   pip install -r backend/requirements.txt
   ```

3. **Environment Configuration**
   ```bash
   cp backend/.env.sample backend/.env
   ```
   
   Edit `backend/.env` with your settings:
   ```env
# --- Application Security ---
# Generate a strong secret key: python -c "import secrets; print(secrets.token_hex(32))"
SECRET_KEY=your seacret key here

# --- Debug & Development ---
FLASK_DEBUG=True
FLASK_RUN_HOST=127.0.0.1
FLASK_RUN_PORT=5000

# --- Database Configuration ---
# SQLite (development)
DATABASE_URL=sqlite:///poker.db

# PostgreSQL (production example)
# DATABASE_URL=postgresql://username:password@localhost/poker_db

# --- CORS Settings ---
# For production, specify allowed origins instead of *
# CORS_ALLOWED_ORIGINS=http://localhost:3000,https://yourdomain.com

# --- Game Settings ---
DEFAULT_CHIPS=10000
SMALL_BLIND=50
BIG_BLIND=100

4. **Generate Secret Key**
   ```bash
   python -c "import secrets; print(secrets.token_hex(32))"
   ```

5. **Run the Application**
   ```bash
   cd backend
   python -m flask run
   ```

6. **Access the Game**
   Open your browser and navigate to: `http://127.0.0.1:5000`

## 📁 Project Structure

```
AI_pokergame/
├── backend/                    # Server-side (Flask/Python)
│   ├── app/
│   │   └── poker/             # Core Poker Game Logic
│   │       ├── ai.py          # AI Strategy and Logic
│   │       ├── game.py        # Game State Management
│   │       └── routes.py      # Flask Blueprint/API Endpoints
│   ├── config.py              # Flask Configuration
│   └── requirements.txt       # Python Dependencies
├── frontend/                  # Client-side (Web)
│   ├── index.html            # Main Page Structure
│   ├── script.js             # Client-side Game Logic
│   └── style.css             # Styling
├── .gitignore                # Git Ignore Rules
├── LICENSE                   # MIT License
└── README.md                # Project Documentation
```

## 🎮 Game Configuration

### Default Settings
- **Starting Chips**: 10,000
- **Small Blind**: 50
- **Big Blind**: 100

### Production Deployment
For production environments, consider:
- Using PostgreSQL instead of SQLite
- Setting proper CORS origins
- Disabling debug mode
- Using a proper WSGI server like gunicorn

## 📝 License

This project is released under the MIT License. See the [LICENSE](LICENSE) file for details.

## 🔧 Development

### Backend Architecture
- **Flask** with modular blueprint structure
- **SQLAlchemy** for database operations
- **Flask-SocketIO** for real-time events
- **Configurable** via environment variables

### Frontend Features
- Real-time game state updates
- Responsive design
- Interactive gameplay interface

---

*Enjoy your poker experience with Midnight Luxury Poker! 🃏*
