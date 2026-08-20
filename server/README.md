# Flopfish FC - WebSocket Server

Real-time multiplayer server for Flopfish FC game.

## Setup

```bash
cd server
npm install
npm start
```

Server runs on port `8080` (or `$PORT` env var)

## Deployment

### Local Testing
```bash
npm start
# Connect to: ws://localhost:8080
```

### Render.com
1. Create account at https://render.com
2. New Web Service from GitHub repo
3. Settings:
   - Root Directory: `server`
   - Build: `npm install`
   - Start: `node server.js`
4. Deploy → Get URL: `https://flopfish-server.onrender.com`

### Environment
- Node 18+
- WebSocket support required

## API

### Messages from Client

**Join Room**
```json
{
  "type": "joinRoom",
  "roomCode": "1234",
  "slot": 0,
  "name": "ปลา",
  "team": "red"
}
```

**Player Update** (every frame)
```json
{
  "type": "playerUpdate",
  "roomCode": "1234",
  "slot": 0,
  "pos": [x, y, z],
  "heading": 1.57
}
```

**Goal**
```json
{
  "type": "goal",
  "side": 1
}
```

### Messages from Server

**Game State** (every 33ms)
```json
{
  "type": "gameState",
  "roomCode": "1234",
  "players": {
    "0": { "pos": [x, y, z], "heading": 1.57, "name": "ปลา", "team": "red" },
    "1": { "pos": [x, y, z], "heading": 0, "name": "บอท", "team": "blue" }
  }
}
```

**Goal Event**
```json
{
  "type": "goal",
  "side": 1
}
```

## Files
- `server.js` - Main WebSocket server
- `package.json` - Dependencies
- `.gitignore` - Git ignore rules

## License
MIT
