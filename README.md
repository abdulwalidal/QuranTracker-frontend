# Quran Tracker — Frontend (React + Vite)

This frontend connects to your Spring Boot backend (abdulwalidal/Quran-Tracker).

Quick start
1. Copy files into a new folder (or clone the repository you create from these files).
2. Install dependencies:
   npm install
3. Create .env from .env.example and set VITE_API_BASE accordingly (e.g., http://localhost:8080).
4. Run dev server:
   npm run dev
5. Open the site (Vite will print the URL, typically http://localhost:5173).

Backend endpoints (exact as implemented in the backend repository)
- POST /verse/{userName}
  - Creates a VerseEntry and attaches it to the user identified by userName.
  - Request body JSON: { "surah": "Al-Fatiha", "verseNo": "1", "memorized": true }
  - Success: 200 OK with text "Verse added Successfully"
  - Note: The path uses userName (not ObjectId).

- GET /verse
  - Lists all verse entries.

- DELETE /verse
  - Deletes all verse entries.

- POST /user
  - Creates a user. Body: { "userName": "alice", "password": "secret" }

- GET /user
  - Lists users (id, userName, password, verseEntry[]).

- GET /user/{id}, DELETE /user/{id}, PUT /user/{id}
  - Operate by MongoDB ObjectId.

CORS
If frontend and backend run on different origins during development you may need to enable CORS in the backend. See optional-backend/WebConfig.java included.

Notes
- The frontend sends POST /verse/{userName} with the selected user's userName (this matches the backend).
- When deleting a user the backend expects the ObjectId string at DELETE /user/{id}. If GET /user returns nested ObjectId objects, you may need to adjust backend serialization or extract string id before delete.

If you want me to push this repository for you to GitHub, provide the repo name and whether it should be public or private and I’ll tell you the exact steps you can run locally or use the GitHub web UI/CLI to create & push.