# 🌤️ Weather App

A premium, single-file weather web app built with HTML, CSS, and vanilla JavaScript. Features real-time weather data, a 5-day forecast, dynamic backgrounds, glassmorphism UI, and geolocation support.

---

## ✨ Features

### Core
- 🔍 **Search by city name** — instant lookup with Enter key support
- 🌡️ **Current weather** — temperature, condition, humidity, wind speed, visibility
- 📅 **5-day forecast** — daily high/low with weather icons
- 🕐 **Live date & time** — updates every minute
- 🌍 **Weather icons** — emoji-based icons matched to conditions

### UI / UX
- 🪟 **Glassmorphism design** — frosted glass cards with soft borders
- 🎨 **Dynamic backgrounds** — gradient shifts based on weather (sunny → warm orange, rainy → dark slate, thunder → near-black, etc.)
- 📱 **Fully responsive** — works on mobile and desktop
- ✨ **Smooth animations** — fade-up card transitions, loading spinner

### Bonus
- 📍 **Geolocation** — auto-detect and load weather for your current location
- 🌡️ **°C / °F toggle** — switch units instantly without re-fetching data
- 🕘 **Recent searches** — last 5 cities saved as quick-tap tags (persisted via `localStorage`)
- ⚠️ **Error handling** — friendly messages for invalid cities or denied location access

---

## 🚀 Getting Started

### 1. Get a Free API Key

This app uses the [OpenWeatherMap API](https://openweathermap.org/api).

1. Sign up at [openweathermap.org](https://home.openweathermap.org/users/sign_up)
2. Go to **API Keys** in your dashboard
3. Copy your key (it activates within a few minutes)

### 2. Add Your API Key

Open `weather-app.html` in any text editor and replace the API key near the top of the `<script>` section:

```js
// Replace with your own OpenWeatherMap API key
const API_KEY = 'your_api_key_here';
```

### 3. Open in Browser

No build step, no server, no dependencies.

```bash
# Just open the file directly
open weather-app.html        # macOS
start weather-app.html       # Windows
xdg-open weather-app.html   # Linux
```

Or drag and drop `weather-app.html` into any browser window.

---

## 📁 Project Structure

This is a **single-file application** — everything lives in `weather-app.html`.

```
weather-app.html
├── <style>         → All CSS (glassmorphism, animations, dynamic backgrounds, responsive)
├── <body>          → HTML structure (search, cards, forecast, loader, error banner)
└── <script>        → JavaScript logic
    ├── Configuration     (API key, base URL)
    ├── State             (unit, lastData, recentCities)
    ├── Background logic  (weather ID → gradient class)
    ├── Emoji mapping     (weather ID → icon)
    ├── Temperature utils (Kelvin → °C/°F conversion)
    ├── Unit toggle       (re-render without re-fetching)
    ├── fetchByCity()     (search by name)
    ├── fetchByCoords()   (geolocation)
    ├── renderWeather()   (update all DOM elements)
    ├── Recent cities     (localStorage read/write)
    └── Init              (load Delhi on startup)
```

---

## 🌈 Dynamic Background Reference

| Weather Condition | Background |
|---|---|
| ☀️ Clear / Sunny | Warm orange–yellow gradient |
| ⛅ Partly Cloudy | Soft gray–blue gradient |
| ☁️ Overcast | Muted steel gradient |
| 🌧️ Rain / Drizzle | Dark slate–blue gradient |
| ❄️ Snow | Cool lavender–white gradient |
| ⛈️ Thunderstorm | Deep dark purple gradient |
| 🌙 Night (any) | Near-black navy gradient |

---

## 🌐 API Reference

This app uses two OpenWeatherMap endpoints:

| Endpoint | Purpose |
|---|---|
| `/data/2.5/weather` | Current weather by city or coordinates |
| `/data/2.5/forecast` | 3-hour forecast for 5 days (40 entries) |

**Free tier** supports up to **60 calls/minute** — more than enough for personal use.

---

## 🔧 Customization

### Change the Default City
Edit the last line of the `<script>` block:
```js
fetchByCity('Delhi');  // ← change to your city
```

### Adjust Recent Cities Count
```js
].slice(0, 5);  // ← change 5 to any number
```

### Modify Background Gradients
Each weather class in the CSS can be edited:
```css
body.bg-sunny  { background: linear-gradient(135deg, #f9c74f 0%, #f3722c 100%); }
body.bg-rainy  { background: linear-gradient(135deg, #2d3a4a 0%, #4a6078 100%); }
/* etc. */
```

---

## 🛠️ Tech Stack

| Technology | Usage |
|---|---|
| HTML5 | Structure and semantic markup |
| CSS3 | Glassmorphism, animations, responsive layout, dynamic gradients |
| Vanilla JavaScript (ES6+) | Logic, async/await API calls, DOM manipulation |
| OpenWeatherMap API | Real-time weather and forecast data |
| Geolocation API | Browser-native location detection |
| localStorage | Persisting recent city searches |

---

## 📸 Weather Condition IDs (OpenWeatherMap)

The app maps OWM condition IDs to categories:

| ID Range | Condition | Category |
|---|---|---|
| 200–299 | Thunderstorm | `thunder` |
| 300–399 | Drizzle | `rainy` |
| 500–599 | Rain | `rainy` |
| 600–699 | Snow | `snowy` |
| 700–799 | Atmosphere (fog, mist) | `cloudy` |
| 800 | Clear sky | `sunny` / `night` |
| 801–804 | Clouds | `cloudy` |

---

## ⚠️ Known Limitations

- Requires an internet connection (API calls are made client-side)
- API key is visible in the HTML source — suitable for personal/local use; for production, proxy calls through a backend
- OpenWeatherMap free tier has a rate limit of 60 requests/minute

---

## 📄 License

This project is open source and free to use for personal and educational purposes.

---

> Built with HTML, CSS & JavaScript · Powered by [OpenWeatherMap](https://openweathermap.org)

---

## Link
[Weather App](https://weather-app-project-git.netlify.app/)
