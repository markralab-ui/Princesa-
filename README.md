# Princesa-
Raya's first game

**Princess Raya's Park Adventure** — a cute 2D browser game for learning Bulgarian words. A little Bulgarian princess in a folk dress explores a sunny park with her mama. Every treasure she finds shows (and says) its Bulgarian name, and shy pets hiding behind bushes join her when found.

- 281 everyday words in the bank (kitchen, bathroom, bedroom, clothes, school things, toys, food and drink, body parts, transport, around the house, nature, lots of animals and jewellery) and 12 pets, all drawn with code.
- Animals and jewellery are the favourites: at least 7 of the 26 treasures in every adventure come from those two groups.
- Each adventure has 26 treasures and 8 pets. The game remembers (in the browser) which words have been learned and picks the least-seen ones next time, so every adventure teaches new words.
- 📖 opens a dictionary of everything learned so far; 🔊 toggles saying the words aloud (uses the device's Bulgarian voice when one is installed).

- Play version 1: https://markralab-ui.github.io/Princesa-/ (`index.html`)
- Play version 2 (work in progress, iterated separately): https://markralab-ui.github.io/Princesa-/v2/ (`v2/index.html`)
  - Version 2 adds a cottage in the park with a hallway, kitchen, bedroom, bathroom, living room and playroom. Furniture gets a Bulgarian name sticker when the princess walks up to it; loose household objects are collected like treasures and rotate each adventure. Words are allocated by theme: park (nature, play, picnic, jewellery), kitchen, bedroom, bathroom, living room, hallway. Every animal (54 in all) is a pet friend that hides behind a bush and joins the princess; 8 appear per adventure.
- Controls: arrow keys (on-screen arrows on touch devices)

## Planned: native-quality Bulgarian voice

Today the game uses the device's own Bulgarian voice (e.g. Apple's "Daria"), and stays silent when none is installed.
The plan is to record every word once with Microsoft Azure's Bulgarian neural voice **Kalina** (bg-BG-KalinaNeural) and ship the clips in an `audio/` folder, so it sounds the same on every device with nothing to install.

Steps when ready:
1. Azure portal → create a **Speech** resource (region East US, pricing tier **Free F0**). Copy Key 1 and the region.
2. In the Claude cloud environment settings: allow the domain `eastus.tts.speech.microsoft.com` (use the chosen region's name), and add secrets `AZURE_SPEECH_KEY` and `AZURE_SPEECH_REGION`.
3. Start a new session and ask Claude to record the words. The service is only used for that one recording; playing the game never contacts it.
