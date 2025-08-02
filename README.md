# 🚍 City-Link – Real-Time Bus Tracking & Booking Suite

**City-Link** is a scalable full-stack application that enables live city-bus tracking, ETA prediction, schedule management, ticket and parcel booking, all in one seamless experience.

Built to serve 1000+ concurrent real-time users without breaking a sweat, City-Link uses WebSockets for lightning-fast updates and integrates Google Maps for intuitive visual feedback.

---

## ✨ Features

- **📍 Live Tracking** – Real-time moving buses on an interactive map.
- **⏰ ETA Prediction** – Smart arrival time estimation based on traffic.
- **🚌 Shortest Route Matching** – Finds nearest bus to the user.
- **🚫 Dynamic Schedule** – Updates automatically with real-time delays.
- **🚚 Parcel & Ticket Booking** – One-tap bookings from the app.
- **🌐 WebSocket Streaming** – Low-latency location data with auto-reconnect.
- **👷 Driver-Friendly** – Driver shares location once; system takes over.
- **⚖️ Battle-Tested** – Serves 1K+ concurrent users reliably.
- **🧰 Microservice Structure** – Clean split between backend and frontend.

---

## 📂 Folder Structure

```bash
city-link/
├── city-link-backend/        # Node.js + Socket.io backend
│   ├── Main-Tracker/         # Socket helpers & trackers
│   ├── src/                  # Express controllers/services
│   ├── .env.sample.txt
│   └── package.json
└── city-link-frontend/       # React + Vite frontend
    ├── public/
    ├── src/                  # Pages, components & hooks
    ├── index.html
    ├── vite.config.js
    └── package.json
```

---

## 📇 Tech Stack

| Layer        | Technology                                      |
|--------------|-------------------------------------------------|
| Frontend     | React 18, Vite, Socket.io-client, Google Maps   |
| Backend      | Node.js, Express, Socket.io, REST, JWT Auth     |
| Realtime DB  | Redis / in-memory store                         |
| Persistent DB| MongoDB / PostgreSQL (configurable)             |
| Dev Tools    | ESLint, Prettier, Husky, dotenv                 |

---

## ⚙️ Getting Started

### 1. Clone & Install

```bash
git clone https://github.com/<your-org>/city-link.git
cd city-link

# Backend Setup
cd city-link-backend
cp .env.sample.txt .env   # Fill in DB_URI, GOOGLE_API_KEY, JWT_SECRET, etc.
npm install
npm run dev

# In a new terminal: Frontend Setup
cd ../city-link-frontend
npm install
npm run dev   # Defaults to http://localhost:5173
```

### 2. Expose Driver Socket (Optional)

If drivers connect externally, expose the backend socket via [ngrok](https://ngrok.com/):

```bash
ngrok http 4000
```

Update `CLIENT_SOCKET_URL` in `city-link-frontend/.env` with your ngrok URL.

### 3. Seed Demo Data (Optional)

```bash
# Inside backend
npm run seed
```

---

## 🚦 Usage

### 🚗 Driver Emission
From a driver device or Postman:
```
{
  "busId": "BUS-42",
  "coords": {
    "lat": 28.6139,
    "lng": 77.2090
  }
}
```


### 2. “Backend broadcasts…” should be outside the code block
Right now, because the JSON code block wasn’t closed, the following text appears as part of the code.  
Move it outside and make it normal text.



### 3. API Reference table is not in Markdown table format
Currently it’s just text, so it won’t render as a proper table.  
Change to:


### 🔌 API Reference (abridged)

| Method | Endpoint              | Purpose                          |
|--------|----------------------|----------------------------------|
| GET    | /api/buses            | List all active buses            |
| GET    | /api/buses/:id/eta    | ETA of given bus to user point   |
| POST   | /api/bookings         | Create ticket/parcel booking     |
| WS     | busLocation (emit)    | Push live GPS from driver        |



🙏 Acknowledgements
Google Maps JavaScript SDK

Socket.io for realtime goodness

Vite for lightning‑fast React builds

Made with ❤️ by Yash Goyal to make daily commutes smarter.

> © Jan 2025 - Present. All rights reserved.

