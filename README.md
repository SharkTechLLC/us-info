# us-info

SHARK TECH LLC - Officials data + audio for My Citizenship Prep.

Downloaded on demand by the app — nothing here is bundled into the app.
Currently covers state officials (governor, senators, capital); reserved
for federal/government officials (e.g. president) in the future.

## Layout

One self-contained folder per record — JSON + its audio files live together,
so the app (and your generator) only ever deals with a single location per
state:

```
state_officials/
  al/
    al.json
    governor_en.mp3
    governor_es.mp3
    senators_en.mp3
    senators_es.mp3
    capital_en.mp3
    capital_es.mp3
  ak/
    ak.json
    ... (same 6 audio files)
  ... (50 folders, lowercase 2-letter code)
government_officials/
  (reserved for future use, e.g. president/president.json + audio)
```

## `<code>.json` schema

```json
{
  "code": "AL",
  "data_version": 1,
  "verified_at": "2026-06-19",
  "governor": "Kay Ivey",
  "senators": ["Katie Britt", "Tommy Tuberville"],
  "capital": "Montgomery"
}
```

- `data_version` must increase any time governor/senators/capital change —
  the app compares this against what it has cached locally to decide
  whether to re-download.
- `verified_at` is just a display string (e.g. an ISO date), shown to the
  user as "last verified on...".
- `capital` is optional — the app already bundles a static state→capital
  list, so it's only useful here if you want this repo to be the single
  source of truth. If omitted, the app keeps its bundled value.
- All 6 audio files are required per state folder: `governor_en.mp3`,
  `governor_es.mp3`, `senators_en.mp3`, `senators_es.mp3`, `capital_en.mp3`,
  `capital_es.mp3` — the app's civics questions cover governor, senators,
  *and* capital.

## What's NOT covered here

The U.S. House Representative is **not** part of this repo — it varies by
congressional district within a state (not just by state), so it can't be
modeled as one record per state. The app currently handles it as a
manually-entered field in Settings, with a link out to the official
ziplook.house.gov lookup tool.
