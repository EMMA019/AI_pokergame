```markdown
# 🎴 Midnight Luxury Poker

A sophisticated, real-time Texas Hold'em poker game built with Flask-SocketIO backend and modern frontend. Features AI opponents with multiple difficulty levels and a luxurious casino-themed interface.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fba578c0-212f-4d10-8fd7-6b2b677c2550" />

![Poker Table](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)
![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Flask](https://img.shields.io/badge/Flask-2.3.3-green)
![SocketIO](https://img.shields.io/badge/SocketIO-5.3.6-orange)

## ✨ Features

### 🎮 Gameplay
- **Real-time Texas Hold'em** with full poker rules
- **Multiplayer support** - Play with friends or AI opponents
- **Smart AI opponents** with three difficulty levels (Easy, Normal, Hard)
- **Complete hand evaluation** and pot management
- **Side pot handling** for all-in scenarios
- **Responsive design** that works on desktop and mobile

### 🎨 User Experience
- **Luxury casino theme** with midnight black and gold accents
- **Smooth animations** for card dealing, chip movements, and pot distribution
- **Intuitive betting interface** with slider and preset bet buttons
- **Real-time game state updates** with Socket.IO
- **Winner announcements** with hand information

### 🛠 Technical
- **Modular architecture** with separated game logic and UI
- **Thread-safe game engine** with proper locking
- **Database integration** for player persistence
- **Comprehensive error handling** and logging
- **Easy deployment** with production-ready configuration

## 🚀 Quick Start

### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)
- Modern web browser with JavaScript enabled

### Installation

1. **Run the automated setup**
   ```bash
   python start_server.py
   ```
   This will:
   - Check your Python environment
   - Install required dependencies
   - Create configuration files
   - Start the development server

2. **Manual setup (alternative)**
   ```bash
   # Install dependencies
   pip install -r requirements.txt
   
   # Start the server
   python run.py
   ```

3. **Access the game**
   Open your browser and navigate to:
   ```
   http://127.0.0.1:5000
   ```

## 🎯 How to Play

### Getting Started
1. Enter your player name in the lobby
2. Add AI opponents using the difficulty buttons
3. Click "Start Game" to begin
4. The game automatically handles dealing and betting rounds

### Game Flow
1. **Blinds**: Small and big blinds are posted automatically
2. **Pre-flop**: Receive your hole cards and begin betting
3. **Flop**: Three community cards are revealed
4. **Turn**: Fourth community card revealed
5. **River**: Final community card revealed
6. **Showdown**: Remaining players reveal hands, best hand wins

### Betting Actions
- **Fold**: Discard your hand and sit out the current round
- **Check**: Stay in the game without betting (when no bet to call)
- **Call**: Match the current bet amount
- **Raise**: Increase the current bet (must meet minimum raise requirements)
- **All-in**: Bet all your remaining chips

## 🏗 Project Structure

```
poker/
├── 📁 backend/              # backend assets
│   ├── 📄 run.py                # Main server entry point
│   ├── 📄 start_server.py       # Automated setup script
│   ├── 📄 config.py             # Application configuration
│   ├── 📄 requirements.txt      # Python dependencies
│   └── 📄 .env.example          # Environment variables template
│   └── 📁 app/                    # Backend application
│       ├── __init__.py           # Flask app factory
│       ├── extensions.py         # Database and SocketIO initialization
│       └── 📁 poker/             # Poker game logic
│           ├── __init__.py       # Blueprint registration
│           ├── models.py         # Database models (User)
│           ├── game.py          # Core game logic (Game, Player, Deck classes)
│           ├── ai.py            # AI strategies (Easy, Normal, Hard)
│           ├── events.py        # SocketIO event handlers
│           ├── routes.py        # HTTP API endpoints
│           └── exceptions.py    # Custom game exceptions
├── 📁 frontend/              # Frontend assets
│   ├── index.html           # Main HTML file
│   ├── style.css            Luxury casino styling
│   └── script.js            # Client-side game logic

```

## 🔧 Configuration

### Environment Variables
Create a `.env` file from `.env.example`:

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

```

### Game Settings
Modify `config.py` to adjust:
- `DEFAULT_CHIPS`: Starting chip count (default: 10000)
- `SMALL_BLIND` / `BIG_BLIND`: Blind amounts
- `MAX_PLAYERS_PER_GAME`: Maximum players per table

## 🎮 AI Difficulty Levels

### 🤖 Easy AI
- Makes random decisions with basic strategy
- Good for beginners learning the game
- Occasionally makes questionable plays

### 🤖 Normal AI  
- Uses hand strength evaluation
- Considers position and pot odds
- Balanced aggression and caution

### 🤖 Hard AI
- Advanced hand reading and range analysis
- Position-aware betting strategies
- Pot odds and implied odds calculations
- Capable of bluffing and semi-bluffing

## 🔌 API Documentation

### Socket.IO Events

#### Client → Server
- `join_game`: Join a game room
  ```json
  { "username": "string", "room_id": "string" }
  ```
- `start_game`: Start a new hand
- `player_action`: Submit player action
  ```json
  { "action": "fold|check|call|bet|raise", "amount": number }
  ```

#### Server → Client
- `game_state_update`: Real-time game state
- `game_over`: Round completion with winners
- `error`: Error notifications

### HTTP API Endpoints
- `POST /api/user`: Create new user
- `GET /api/user/<username>`: Get user information  
- `POST /api/reset_user`: Reset user chips
- `GET /api/games`: List active games
- `GET /api/game/<room_id>`: Get specific game state

## 🚀 Deployment

### Production Deployment
1. Set `FLASK_DEBUG=False` in `.env`
2. Generate a strong `SECRET_KEY`
3. Configure production database (PostgreSQL recommended)
4. Set proper CORS origins
5. Use gunicorn for production server:
   ```bash
   gunicorn -k eventlet -w 1 run:app
   ```

### Docker (Optional)
```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "run.py"]
```

## 🐛 Troubleshooting

### Common Issues

**Server won't start:**
- Check Python version (requires 3.8+)
- Verify all dependencies are installed
- Check port 5000 is available

**Connection errors:**
- Ensure server is running
- Check browser console for WebSocket errors
- Verify CORS settings if accessing from different domain

**Game logic issues:**
- Check server logs for error messages
- Verify database file permissions
- Reset game state if needed

### Logs
- Server logs: `poker_server.log`
- Real-time logs: Browser developer console

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines
- Follow PEP 8 for Python code
- Use meaningful commit messages
- Add tests for new features
- Update documentation accordingly

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Poker hand evaluation logic inspired by open-source poker libraries
- UI design inspired by luxury casino aesthetics
- Socket.IO for real-time communication capabilities
- Flask community for excellent web framework documentation

---

**Enjoy your game of Midnight Luxury Poker!** 🎰♠️♥️♣️♦️

For questions or support, please check the issues section or contribute to the documentation.
```

This README provides:

1. **Comprehensive overview** of the project and its features
2. **Easy setup instructions** using your automated scripts
3. **Detailed technical documentation** of the architecture
4. **Game rules and AI descriptions** for users
5. **API documentation** for developers
6. **Deployment guides** for production
7. **Troubleshooting section** for common issues


The structure follows best practices for open-source projects and should help both users and developers understand and work with your codebase effectively.
