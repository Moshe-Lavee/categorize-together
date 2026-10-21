# Categorize Together

A classroom exercise in one HTML file (`index.html`, no build). The class builds a map of a topic from the bottom up:

1. **Stage A** – students list items in each column (e.g. Judaism / Christianity / Islam).
2. **Stage B** – each student proposes general categories (no assignment yet).
3. **Stage C** – students group categories that are really the same. Then the teacher merges them into final categories.
4. **Stage D** – students drag items (their own and classmates') into the categories. The teacher sees live results as stars, a table, or CSV.

The teacher opens a room, reads a short explanation, and sets up: interface language (Hebrew RTL / English LTR), title, the word for the items, 2–7 columns, number of fields, and the instructions for stages A and B. Students join with a 4-digit room code and a name; no accounts.

## Local test (no Firebase)
Add `?local` to the URL (serve the folder with e.g. `python -m http.server`, then open `http://localhost:8000/index.html?local`). Open several tabs of the same browser: one teacher, others students. In local mode the teacher screen has demo-data buttons (`?debug` shows them in Firebase mode too).

## Firebase
The config at the top of `index.html` points to a Realtime Database. Rules needed:
```json
{ "rules": { "rooms": { "$room": { ".read": true, ".write": true } } } }
```
Rooms are plain data under `rooms/<code>`; use "Delete this room's data" after class.

## Notes
- This app does not modify the earlier religions-only app (`religion-categories`); both can share the same Firebase project.
- Not yet built: teacher-side merging of item variants (e.g. Quran / Koran), and the example tour.
