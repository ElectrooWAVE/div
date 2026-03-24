# ✦ Divya Hidden Message Hunt — Project Rules

> A complete reference guide for building, customizing, and expanding this romantic cosmic website.

---

## 1. Project Overview

A single-page romantic website built for **Divya**. It has three screens:
1. **Title Screen** — introduces the experience
2. **Hunt Screen** — 10 floating objects hiding secret love messages
3. **Finale Screen** — triggered when all 10 messages are found

---

## 2. Tech Stack Rules

| Rule | Detail |
|------|--------|
| Single HTML file | All CSS and JS must be embedded — no external files |
| No frameworks | Vanilla HTML, CSS, and JavaScript only |
| Google Fonts allowed | Import via `<link>` tag in `<head>` |
| No jQuery | Use native `document.getElementById`, `classList`, etc. |
| No build tools | Must run by opening the HTML file directly in a browser |

---

## 3. Font Rules

| Font | Usage |
|------|-------|
| `Cormorant Garamond` | All love messages, the name "Divya", finale text, title heading |
| `Quicksand` | Buttons, hint labels, counters, UI text |

- Always import both fonts from Google Fonts
- Never use system fonts like Arial or sans-serif for love messages
- Message text must always be **italic**

---

## 4. Color Palette Rules

| Name | Hex | Usage |
|------|-----|-------|
| Deep purple | `#1a0533` | Background gradient start |
| Near black | `#000010` | Background gradient end |
| Soft lilac | `#f4c8ff` | Heading color, message text |
| Muted lavender | `rgba(220,190,255,0.85)` | Body/subtitle text |
| Purple accent | `#9b3dff` | Button gradient start |
| Pink accent | `#ff6ab0` | Button gradient end, firework |
| Gold | `#ffe066` | Progress stars when lit, firework |
| Blue | `#80d4ff` | Firework particle |
| Orange | `#ff9b3d` | Firework particle |
| Purple firework | `#c87aff` | Firework particle |

- **Never use white text directly** — always use the lilac/lavender shades above
- **Never use a solid background** — always use the radial gradient
- **Dark overlay for message reveal:** `rgba(5,0,20,0.88)`

---

## 5. Animation Rules

| Element | Animation |
|---------|-----------|
| Title heading | Slow glow pulse — text-shadow cycles every 3s |
| Floating objects | `translateY(0px)` → `translateY(-12px)` → back, looping |
| Float timing | Each object has a staggered `animation-delay` (e.g. -0.5s, -1s, -1.5s...) |
| Hover on object | Scale to `1.25x`, glow intensifies |
| Message overlay | `fade-in` opacity 0 → 1, duration 0.3s |
| Fireworks | Burst outward using CSS custom properties `--dx` and `--dy`, fade out |
| Finale name | Same glow-pulse as title heading |

- **Never animate all objects in sync** — stagger delays are required
- **Never use JavaScript for float animation** — use CSS `@keyframes` only
- Fireworks must be **injected dynamically** via JavaScript, not pre-placed in HTML

---

## 6. Object Rules

Each of the 10 hunt objects must follow these rules:

- Size: **56px × 56px** circle
- Background: `rgba(255,255,255,0.06)`
- Border: `1.5px solid rgba(200,150,255,0.25)`
- Filter: `drop-shadow(0 0 8px rgba(200,100,255,0.6))`
- Once clicked: add class `found` → opacity `0.3`, `pointer-events: none`, animation stops
- Objects must be placed with `position: absolute` inside a `position: relative` container
- Positions must be spread naturally across the screen (corners, center, sides, not clustered)

### The 10 Objects & Messages

| # | Emoji | Hidden Message |
|---|-------|----------------|
| 1 | ⭐ | "I love you so much, my princess. You shine brighter than every star in this sky." |
| 2 | 🌙 | "Even on my darkest nights, you are the moon that lights up everything for me." |
| 3 | 🌸 | "I love you so much, Madam Ji — and I will always listen to you, I promise. 💜" |
| 4 | 💌 | "If I could write you a letter every day for the rest of my life, it still wouldn't be enough to say how much I love you." |
| 5 | 🦋 | "You gave me butterflies the moment I met you, and they never went away." |
| 6 | ✨ | "I am so glad the universe decided to put us in the same world. Meeting you changed everything." |
| 7 | 🔮 | "I love you so much, Madam Ji — wherever you lead, I'll follow with my whole heart." |
| 8 | 🌺 | "You make every ordinary day feel like something magical, my princess. I love you so much." |
| 9 | 💫 | "I love you so much — more than I know how to say, more than any words I could find." |
| 10 | 🪐 | "You are my favourite place in the entire universe. I am so, so glad I met you, Divya." |

---

## 7. Progress Indicator Rules

- **10 small circles** shown at the top center of the hunt screen
- Default state: `rgba(255,255,255,0.12)` fill, faint purple border
- Lit state: golden radial gradient + `box-shadow: 0 0 10px #ffe066`
- Circles light up **in order** as messages are found (left to right)
- A counter `"0 / 10 found"` must also update in the top right corner

---

## 8. Message Reveal Rules

When an object is clicked:
1. Show full-screen dark overlay
2. Display the object's emoji (large, ~42px) at the top of the card
3. Show the message text in **Cormorant Garamond italic**, color `#f4c8ff`
4. Show a `carry on ✦` button to close the overlay
5. Mark the object as `found` (opacity + no pointer events)
6. Update the progress indicator and counter
7. After closing, **if all 10 are found**, trigger the finale after a 300ms delay

---

## 9. Finale Rules

- Replace the hunt screen content with the finale
- Show `✦ Divya ✦` in large glowing Cormorant Garamond with pulsing animation
- Show the final message: *"You are the most special thing in my universe. I love you so much, my princess. Every star up there knows — I am so glad I met you. 💜"*
- Inject **30 firework particles** dynamically using JavaScript
- Each firework: random position, random direction (`--dx`, `--dy`), random color from palette, staggered delay
- Fireworks use a `burst` keyframe: scale from 1 → 0, translate outward, fade out

---

## 10. Customization Rules

To safely customize this project, only change these things:

| What to change | Where |
|----------------|-------|
| Her name | Replace all instances of `"Divya"` in text content |
| Messages | Edit the `messages` array in the JavaScript section |
| Emojis | Edit the `emoji` field in the `messages` array |
| Number of objects | Update both the `messages` array AND the `positions` array AND the `#progress-bar` HTML |
| Colors | Only modify values in the color palette table above |
| Font sizes | Only change heading and body sizes — never go below 14px for messages |

**Never change:**
- The float animation logic
- The `found` class behavior
- The `--dx` / `--dy` firework system
- The screen switching logic (`display: none / block / flex`)

---

## 11. Accessibility & UX Rules

- Hint label must always be visible at the bottom: `✦ tap the glowing objects to find hidden messages ✦`
- Objects must never overlap each other
- The overlay close button must always be reachable (centered, not hidden)
- Min container height: **600px**
- All text must be readable against dark background — never go below `rgba(200,170,255,0.6)` for secondary text

---

*Built with love. For Divya. 💜*