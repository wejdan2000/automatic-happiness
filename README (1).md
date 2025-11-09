# Location-by-Link - Mobile Prototype (React Native + TypeScript + Google Maps)

What this prototype does
- Mobile app (Expo / React Native, TypeScript) that:
  - Parses Google Maps links or "lat,lng" text pasted by the user.
  - Shows the parsed coordinates on a Google map (react-native-maps with Google provider).
  - Lets user save the location to a backend and returns a numeric ID + shareable deep link.
- Backend (Node + Express, TypeScript) that:
  - Stores locations in SQLite.
  - Provides endpoints:
    - POST /api/locations -> create location, returns id and share_url
    - GET /api/locations/:id -> returns saved location JSON
    - GET /loc/:id -> simple web preview (Google Maps embed)

Requirements
- Expo CLI (or React Native environment)
- Node 18+
- Google Maps API key for iOS/Android & for web embed (instructions below)

Quick start (local)
1. Backend
   - cd server
   - cp .env.example .env and set PORT (optional) and BASE_URL (e.g., http://localhost:4000) and GOOGLE_MAPS_EMBED_KEY
   - npm install
   - npm run build
   - npm start
   - Backend runs on http://localhost:4000 by default.

2. Mobile (Expo)
   - cd mobile
   - cp app.config.example.json app.json and set expo.scheme (e.g. "myapp") and expo.extra.API_BASE_URL to your backend (e.g., http://10.0.2.2:4000 for Android emulator or http://localhost:4000 on iOS/sim)
   - npm install
   - expo start
   - Open in Expo Go or run on simulator (ensure Google Maps API key configured per Expo docs).

Notes
- You must add your Google Maps API key. See mobile/README section for instructions.
- Deep links: saved locations return a deep link like myapp://loc/{id}. Configure your app to handle this scheme in production.

What's next
- Add native share sheet, short links, support for more link formats (what3words, Apple Maps), offline caching, authentication if you want it later.