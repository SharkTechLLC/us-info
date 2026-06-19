# us-states-audio

SHARK TECH LLC - State officials data + audio for My Citizenship Prep.

Downloaded on demand by the app when a user sets (or refreshes) their state —
nothing here is bundled into the app.

## Layout

```
data/
  al.json, ak.json, ... (one per state, lowercase 2-letter code)
audio/
  al/governor_en.mp3, governor_es.mp3, senators_en.mp3, senators_es.mp3
  ak/...
```

## `data/<code>.json` schema

```json
{
  "code": "AL",
  "data_version": 1,
  "verified_at": "2026-06-19",
  "capital": "Montgomery",
  "governor": "Kay Ivey",
  "senators": ["Katie Britt", "Tommy Tuberville"]
}
```

- `data_version` must increase any time governor/senators/capital change —
  the app compares this against what it has cached locally to decide
  whether to re-download.
- `verified_at` is just a display string (e.g. an ISO date), shown to the
  user as "last verified on...".
- Audio file names are fixed (`governor_en.mp3`, `governor_es.mp3`,
  `senators_en.mp3`, `senators_es.mp3`) — only the per-state folder changes.
