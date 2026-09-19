# The Collection

A one-visitor museum, seven rooms wide, walked sideways. It opens in the dark:
a bulb drops in on a cord, and nothing is visible until she presses and holds
it long enough for the filament to come up.

## Run it

Double-click `index.html`. That's it — no build step, no `npm install`, no
dependencies. It's one file plus a `photos/` folder.

To put it online, drag the whole folder onto [Netlify Drop](https://app.netlify.com/drop)
or push it to a GitHub repo and turn on Pages. Both are free and take about a minute.

## Make it yours

Open `index.html` and scroll to the block marked:

```
✎  EDIT EVERYTHING HERE — AND ONLY HERE
```

It's the first thing in the `<script>`, about 150 lines. Every line with a `✎`
is placeholder text. Nothing below that block needs touching.

| What | Where in CONFIG |
|---|---|
| Her name, your name, the date | top of the object |
| The code that unlocks the hidden audio track | `secretCode` |
| The opening screen (bulb text) | `door` |
| How you met, and that first photo | `rooms[0].paragraphs`, `rooms[0].photo` |
| The four framed memories + their hidden notes | `rooms[1].exhibits`, `rooms[2].exhibits` |
| Twelve things about her | `rooms[3].items` |
| The hard parts, and what they became | `rooms[4].mends` |
| Songs + the memory attached to each | `rooms[5].tracks` |
| **The letter** | `rooms[6].letter` |

### Songs

Put them in `songs/`: `014.mp3`, `023.mp3`, `051.mp3`, `068.mp3` and `000.mp3`
(the hidden one). Typing a track number and pressing play starts the song and
shows the memory attached to it beside the handset. If you'd rather not host
audio, leave `audio` blank on a track and paste a Spotify embed link into
`embed` instead.

### Photos

Put them in `photos/`: `first-meeting.jpg` for room I, then `014.jpg`,
`023.jpg`, `051.jpg`, `068.jpg` (portrait crops) and `final.jpg` (square — it's
the one under the cloth). A missing photo
shows a designed empty frame rather than breaking, so you can launch before
you've chosen them all.

## Things she has to find

Not all of it is signposted. That's deliberate.

1. **The bulb.** Nothing happens until she presses and holds it. The filament
   warms, the pool of light widens, and at full brightness the room floods and
   the bulb lifts back up out of frame. If she waits about fifteen seconds
   without touching it, a line appears underneath.
2. **Conservator's notes.** Every framed piece has a second, more private
   caption behind a button in its label.
3. **The placard** in Room I that says not to touch it.
4. **All twelve tags** in Room IV — the counter keeps score, and
   turning the last one unlocks an extra line.
5. **The fourth digit** in the audio guide. Three-digit numbers play catalogued
   tracks; the right four digits play one that isn't in the catalogue. Set it to
   your date in `secretCode`.
6. **The ∞** on the plaque in the last room.

## Notes on how it's built

- Palette is four risograph inks — bubblegum pink, sunflower, mint, periwinkle
  — on warm paper, with every outline the same deep plum and every card sitting
  on a hard offset shadow.
- Horizontal scroll-snap for the walk, so swipe, trackpad, mouse wheel, arrow
  keys and the floor-plan menu all move room to room.
- Only `transform` and `opacity` are animated, driven off one throttled scroll
  listener, so the parallax stays cheap on phones.
- `prefers-reduced-motion` turns off the dust, the parallax and the staggered
  letter reveal, and the site still works completely.
- Keyboard: `←` `→` walk, `Home`/`End` jump, `Esc` closes anything open, focus
  is trapped inside dialogs and returned when they close.
- The last room is the one place that scrolls vertically. Horizontal swipes
  still pass through to the gallery.
