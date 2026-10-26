# Slow Word

**AppADay Day 172** | Category S, Spirituality | Claude API: No

Live: https://augustineiacopelli.github.io/appaday-172-slow-word/
Portfolio: https://augustineiacopelli.github.io/appaday/

Slow Word is a quiet lectio divina companion for the daily Mass readings. It loads the Gospel of the day, then guides you through the four classic movements of lectio divina with a gentle timer, generated chimes, and a screen that stays awake. When the prayer time ends, you save the word or phrase that stayed with you, and a journal keeps those words with a streak of days prayed.

## Today

The Today screen shows the liturgical day, its season, and its color, with a chip for each reading of the day: First Reading, Psalm, Second Reading on Sundays and feasts, and Gospel. The Gospel opens by default, and Settings can change that. Arrows step up to seven days back or ahead, so you can pray tomorrow's Gospel the night before or Sunday's on Saturday. A Short verse chip offers a verse chosen for the date from the offline set, and Another verse draws a different one.

Citations come from the free Catholic Readings API (cpbjr.github.io/catholic-readings-api), the same source used by Day 128 Sermon Note Catcher, and the text comes from bible-api.com. The Douay-Rheims is the default translation, with the World English Bible as an alternative. Psalms always load in the World English Bible so the numbering matches the lectionary. Where a lectionary citation gives a long and short form, the short form is used, which suits slow reading. The Mass in the United States proclaims the NABRE, which cannot be redistributed, so every reading also links to the official USCCB page for anyone who prefers to pray from it.

Each day's citations and each passage are cached on the device, so a day already opened works offline and loads instantly.

## Fallbacks

If the passage text cannot be loaded, the app shows the citation, a link to the USCCB readings, a Try again button, and a box to paste the passage and pray with it. If the readings service cannot be reached at all, the app opens a verse for the day from a built in set of 50 short passages chosen for lectio divina (Psalms, the Prophets, the Gospels, and the Letters), taken from the public domain World English Bible. The divine name is rendered as the LORD, following Catholic liturgical practice, and a few verses are lightly trimmed to stand on their own.

## The four movements

Lectio (Read), Meditatio (Reflect), Oratio (Respond), and Contemplatio (Rest) each have their own prompt and countdown ring. The default is 3, 5, 4, and 3 minutes, and Settings offers Short 10, Standard 15, and Long 30 presets plus one minute steps from 1 to 30 for each movement. During reading and reflection the passage is on screen, and tapping any word holds it in gold; tap again to let it go. Response shows only the held phrase, and Rest dims everything but the timer.

The countdown is computed from a stored end time rather than counted ticks, so it stays accurate if the phone sleeps or the tab is backgrounded. A session survives a reload for three hours and resumes where it left off, skipping ahead past any movement that ended while the page was closed. Pause, Next, and End are always available, and the space bar and right arrow work on a keyboard. If Move on automatically is turned off in Settings, a movement chimes once when its time is up and waits for Next.

Chimes are synthesized with the Web Audio API as a small singing bowl tone (no audio files): one stroke to begin, a brighter stroke between movements, and three strokes at the end, with adjustable volume and a test button. Android phones can also vibrate. On iPhone, the ring switch must be off silent for chimes to sound. The screen stays on while praying. The app uses the Screen Wake Lock API where it works, and on iPhone and iPad it also plays a tiny silent looping video, the same technique NoSleep.js uses, because Wake Lock is missing or unreliable in home screen apps before iOS 18.4. Both are released when the prayer time ends and restarted when you return to the app; a note under the controls says whether the screen is being kept awake. When no word is held, Reflect invites you to tap the word that keeps returning, Respond invites you to speak to God in your own words, and Rest shows only the timer.

## Saving the word

After Rest, the save screen fills the field with the phrase you held, and you can tap more words in the passage below or type your own (up to 80 characters), plus an optional line to carry into the day (up to 500 characters). Save without a word still counts the day.

## Journal

The Journal tab shows the current streak, best streak, total sessions, and total minutes, a seven day row with a candle dot for each day prayed, and every saved word with its date, reading, minutes, and note. The streak counts consecutive days ending today, or ending yesterday if today has not been prayed yet. Entries can be deleted after an in-app confirmation.

## Data

Everything is stored in your browser under `appaday172_slowword` (settings and journal), `appaday172_cache` (up to 40 cached days and passages), and `appaday172_session` (the prayer time in progress). Nothing leaves your device except the requests for the day's readings. Settings has Download backup and Restore backup for a JSON file that merges entries without duplicating them, and Erase all data, which asks first.

## Build

A single self-contained `index.html` with inline CSS and JavaScript, no build step, and no Claude API. EB Garamond loads from Google Fonts. Saved to a phone home screen, it launches full screen with its own icon, and the shared save.js offers to save it on a phone.
