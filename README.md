# Princesa-
Raya's first game

**Princess Raya's Park Adventure** — a cute 2D browser game for learning Bulgarian words. A little Bulgarian princess in a folk dress explores a sunny park with her mama. Every treasure she finds shows (and says) its Bulgarian name, and shy pets hiding behind bushes join her when found.

- 281 everyday words in the bank (kitchen, bathroom, bedroom, clothes, school things, toys, food and drink, body parts, transport, around the house, nature, lots of animals and jewellery) and 12 pets, all drawn with code.
- Animals and jewellery are the favourites: at least 7 of the 26 treasures in every adventure come from those two groups.
- Each adventure has 26 treasures and 8 pets. The game remembers (in the browser) which words have been learned and picks the least-seen ones next time, so every adventure teaches new words.
- 📖 opens a dictionary of everything learned so far; 🔊 toggles saying the words aloud (recorded with the Bulgarian voice Kalina; works on every device).

- Play: https://markralab-ui.github.io/Princesa-/ (`index.html`)
- The original, simpler version is kept at https://markralab-ui.github.io/Princesa-/v1/ (`v1/index.html`)
  - The main game adds a cottage in the park with a hallway, kitchen, bedroom, bathroom, living room and playroom. Furniture gets a Bulgarian name sticker when the princess walks up to it; loose household objects are collected like treasures and rotate each adventure. Words are allocated by theme: park (nature, play, picnic, jewellery), kitchen, bedroom, bathroom, living room, hallway. Every animal (88 in all) is a pet friend that hides behind a bush and joins the princess; 11 appear per adventure. An adventure: 14 treasures, 11 pets, 4–7 objects per room and a few fixed things to name (about 40 minutes, usually over a few sittings). Every section covers its word bank in about 8 adventures. Every section rotates by least-seen with a one-adventure cooldown: treasures, pets, room objects, a few fixed things to name, and a set of "visiting" park objects (statue, picnic table, lamppost, well…).
- Controls: arrow keys (on-screen arrows on touch devices)

## Voice: Kalina (Azure neural)

Every spoken word — all 568 words in the bank (including the 76 animal pets), the 12 baby pets, the 6 room names and the "Здравей!" greeting, 587 clips in all — is recorded once with Microsoft Azure's Bulgarian neural voice **Kalina** (bg-BG-KalinaNeural, 10% slower than normal) and shipped as MP3s in `audio/`. The game plays these, so it sounds the same on every device with nothing to install; it never contacts Azure. The device's own Bulgarian voice is only a fallback for any text without a clip.

To re-record (e.g. after adding words): with `AZURE_SPEECH_KEY` and `AZURE_SPEECH_REGION` set and the region's `*.tts.speech.microsoft.com` host allowed, ask Claude to record the new words with Kalina; each clip is named after the word's key (`apple.mp3`, `pet-bunny.mp3`, `room-kitchen.mp3`) and listed in the `CLIPS` table in `index.html`.
