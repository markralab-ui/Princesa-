# Princesa-
A Bulgarian word game for kids

**Princess Park Adventure** — a cute 2D browser game for learning Bulgarian words. A little Bulgarian princess in a folk dress explores a sunny park with her mama. Every treasure she finds shows (and says) its Bulgarian name, and shy pets hiding behind bushes join her when found.

- 281 everyday words in the bank (kitchen, bathroom, bedroom, clothes, school things, toys, food and drink, body parts, transport, around the house, nature, lots of animals and jewellery) and 12 pets, all drawn with code.
- Animals and jewellery are the favourites: at least 7 of the 26 treasures in every adventure come from those two groups.
- Each adventure has 26 treasures and 8 pets. The game remembers (in the browser) which words have been learned and picks the least-seen ones next time, so every adventure teaches new words.
- 📖 opens a dictionary of everything learned so far; 🔊 toggles saying the words aloud (recorded with the Bulgarian voice Kalina; works on every device).

- Play: https://markralab-ui.github.io/Princesa-/ (`index.html`)
- The original, simpler version is kept at https://markralab-ui.github.io/Princesa-/v1/ (`v1/index.html`)
  - The main game adds a cottage in the park with a hallway, kitchen, bedroom, bathroom, living room and playroom. Furniture gets a Bulgarian name sticker when the princess walks up to it; loose household objects are collected like treasures and rotate each adventure. Words are allocated by theme: park (nature, play, picnic, jewellery), kitchen, bedroom, bathroom, living room, hallway. Every animal (88 in all) is a pet friend that hides behind a bush and joins the princess; 11 appear per adventure. An adventure: 14 treasures, 11 pets, 4–7 objects per room and a few fixed things to name (about 40 minutes, usually over a few sittings). Every section covers its word bank in about 8 adventures. Every section rotates by least-seen with a one-adventure cooldown: treasures, pets, room objects, a few fixed things to name, and a set of "visiting" park objects (statue, picnic table, lamppost, well…).
- Controls: arrow keys (on-screen arrows on touch devices)

## Myth Monster Freeze (`monsters/index.html`)

A second game: https://markralab-ui.github.io/Princesa-/monsters/

- You start in a sunny meadow with six magic portals: Europe, Asia, Africa, North America, South America and Oceania.
- Each continent has 5 monsters from real myths and folklore. Swing the frost sword to freeze one: its name and country pop up (on a card, and as a tag over the ice block) and it drops its treasure to collect. For example the **Kuker** from **Bulgaria** drops **Kuker bells**.
- The 30 monsters and treasures: Kuker (Bulgaria, bells), Troll (Norway, gold), Krampus (Austria, birch twigs), Baba Yaga (Russia, mortar and pestle), Loch Ness Monster (Scotland, scale); Kappa (Japan, cucumber), Tengu (Japan, feather fan), Nian (China, red lantern), Kumiho (Korea, fox bead), Yeti (Nepal, snow crystal); Grootslang (South Africa, diamond), Ammit (Egypt, Feather of Truth), Tokoloshe (South Africa, invisibility pebble), Ninki Nanka (The Gambia, swamp emerald), Mokele-mbembe (Republic of the Congo, molombo fruit); Sasquatch (Canada & USA, pine cone), Jersey Devil (USA, old lantern), Chupacabra (Puerto Rico, prickly pear), Alux (Mexico, golden corn), Ogopogo (Canada, lake pearl); Saci (Brazil, red cap), Curupira (Brazil, golden seed), Pombero (Paraguay, honey pot), Chonchón (Chile, magic feather), Tunche (Peru, silver whistle); Bunyip (Australia, water lily), Yowie (Australia, opal), Drop Bear (Australia, gum leaf), Patupaiarehe (New Zealand, wooden flute), Adaro (Solomon Islands, flying fish).
- Monsters chase you gently; a bump costs a heart. Lose them all and you go home to the meadow, where hearts refill. Frozen monsters thaw after 2 minutes, and stay frozen while you visit other continents. Freeze every monster on a continent and it is cleared: they stay frozen for good (even after a reload) and its portal gets a ⭐.
- **Six rounds, every country:** pick a round on the start screen (🔄 changes round). Round 1 has the 30 monsters above; Round 2 adds 38 more from 36 new countries (Minotaur from Greece, Leprechaun from Ireland, Tikbalang from the Philippines, Papa Bois from Trinidad and Tobago, and more). Rounds 3–6 are planned so that all 195 countries are covered; see [`monsters/ROUNDS.md`](monsters/ROUNDS.md). Clearing all six continents completes a round.
- **World map:** the Treasure Book opens with a world map. Each country lights up in its continent's colour when you freeze its monster, in any round; tap a country to see its monsters. Light up all 195 to freeze the whole world.
- 🎒 opens the Treasure Book (every monster met, where it is from, and how many treasures you have). Progress is saved in the browser. 🔊 toggles sound effects and the spoken "Kuker! From Bulgaria."
- Controls: arrow keys / WASD to move, Space (or click) to swing. On a phone: drag on the left side to move, tap ⚔️ to swing.

## Voice: Kalina (Azure neural)

Every word was checked by a native speaker. 524 words use Kalina (a few with the stress corrected); the 64 she could not say right are recorded by a native Bulgarian speaker instead (cut from voice memos and levelled to the same loudness). Six words that sounded unnatural were replaced: пластир → химикалка, чаша за зъби → чашка, плед → одеялце, ключ за лампата → крушка, масичка за рисуване → бюро, аплик → полилей.

Every spoken word — all 568 words in the bank (including the 76 animal pets), the 12 baby pets, the 6 room names and the "Здравей!" greeting, 587 clips in all — is recorded once with Microsoft Azure's Bulgarian neural voice **Kalina** (bg-BG-KalinaNeural, 10% slower than normal) and shipped as MP3s in `audio/`. The game plays these, so it sounds the same on every device with nothing to install; it never contacts Azure. The device's own Bulgarian voice is only a fallback for any text without a clip.

To re-record (e.g. after adding words): with `AZURE_SPEECH_KEY` and `AZURE_SPEECH_REGION` set and the region's `*.tts.speech.microsoft.com` host allowed, ask Claude to record the new words with Kalina; each clip is named after the word's key (`apple.mp3`, `pet-bunny.mp3`, `room-kitchen.mp3`) and listed in the `CLIPS` table in `index.html`.

### What works for fixing Kalina's stress (learned from the listening check)

- Asking Kalina for the stress does not work reliably: neither an accent mark nor a phonetic (IPA) hint, and not saying the word inside a sentence.
- What works: keep Kalina's own recording and change it. Azure reports when each sound starts, so the stressed syllable (the capital one in the pronunciation guide, e.g. ba-ra-BAN) can be found exactly. That syllable is made about 4 semitones higher, the loudest, and the longest (at least 0.15–0.2 s); syllables after it are shortened and softened.
- Spell Bulgarian "о" as open `ɔ` and "е" as `ɛ` in the phonetic hint, otherwise Kalina says "ou". Use full `a` for "а" so it stays a clear "a".
- Kalina's voice creaks at the end of a word. Raising the pitch there makes it sound raspy, so the last moment (at most 70 ms) is faded out where her voice stops being clear. Never trim more than that, or a whole syllable is lost.
- The tools are Azure Speech (voice, sound timings), Praat via parselmouth (pitch, length, loudness changes) and ffmpeg.

Stress fixes: Kalina sometimes guesses the stress wrong, because Bulgarian spelling doesn't mark it. These words are re-recorded with the stress spelled out in SSML (`<phoneme alphabet="ipa" ph="...">`); keep them when re-recording:
- барабан (`drum.mp3`): `bɐrɐˈban`
- бисквита (`cookie.mp3`): `bisˈkvitɐ`
- боички (`paints.mp3`): `boˈitʃki`
- бонбон (`candy.mp3`): `bonˈbɔn`
- комин (`chimney.mp3`): `koˈmin`
- краставица (`cucumber.mp3`): `ˈkrastɐvitsɐ`
- лале (`tulip.mp3`): `lɐˈlɛ`
- легло (`bed.mp3`): `lɛˈɡlɔ`
- листо (`leaf.mp3`): `lisˈtɔ`
- лъжица (`spoon.mp3`): `lɐˈʒitsɐ`
- мартеница (`martenitsa.mp3`): `ˈmartɛnitsɐ`
- метла (`broom.mp3`): `mɛˈtla`
- огледало (`mirror.mp3`): `oɡlɛˈdalo`
- панделка (`bow.mp3`): `ˈpandɛlkɐ`
- пастели (`crayons.mp3`): `pɐˈstɛli`
- перо (`feather.mp3`): `pɛˈrɔ`
- пижама (`pyjamas.mp3`): `piˈʒamɐ`
- писмо (`letter.mp3`): `pisˈmɔ`
- пола (`skirt.mp3`): `poˈla`
- пчела (`bee.mp3`): `ptʃɛˈla`
- сърце (`heart.mp3`): `sɐrˈtsɛ`
- хвърчило (`kite.mp3`): `xvɐrˈtʃilo`
- яйце (`egg.mp3`): `jajˈtsɛ`

## After the voice recordings are done: remove the Azure key

The key was only needed to record the clips once. Afterwards:
1. claude.ai/code → gear next to the **Princesa** environment → **Environment variables** → delete the `AZURE_SPEECH_KEY=` line (and the region line) → Save changes.
2. Optional: portal.azure.com → your Speech resource → Keys and Endpoint → **Regenerate Key 1**.
The recordings in the game keep working; they are plain audio files.
