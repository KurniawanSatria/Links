# Saturia. — Link in Bio

> A minimal, animated link-in-bio page with live Spotify activity, Discord server widget, and platform-colored cards.

---

## Preview

- **Desktop** — split layout: profile on the left, links on the right
- **Mobile** — stacked layout: profile on top, links below

---

## Features

- 🎵 **Spotify Now Playing** — live track, album art (vinyl spin), animated waveform bars
- 💬 **Discord Server Widget** — server name, online count, member count, join button
- 🎨 **Platform-colored cards** — each link card glows with its brand color on hover
- ✨ **Full animations** — particle network, rotating profile ring, blob backgrounds, card 3D tilt, shimmer swipe, stagger entrance
- 🖱️ **Custom cursor** — dot + ring follower, scales on hover
- 📱 **Responsive** — adapts to mobile automatically
- 🔖 **Favicon** — profile photo shown in browser tab

---

## Setup

### 1. Clone / Download

Just grab `index.html` — everything is self-contained in a single file.

### 2. Edit your links

Open `index.html` and find the `.link-card` elements. Update the `href` attributes and subtitle text:

```html
<a class="link-card" data-t="instagram" href="https://instagram.com/YOUR_USERNAME" ...>
```

### 3. Spotify Now Playing (Lanyard)

The widget uses [Lanyard](https://lanyard.rest) to read your Spotify activity from your Discord status.

**Steps:**
1. Join the [Lanyard Discord server](https://discord.gg/wy3r4DtXsP) to register your account
2. Make sure **Display current activity** is enabled in Discord settings
3. Open `index.html` and find this line near the bottom:

```js
const LANYARD_USER_ID = null;
```

Replace `null` with your Discord user ID as a string:

```js
const LANYARD_USER_ID = "123456789012345678";
```

> **How to find your Discord user ID:** Settings → Advanced → Enable Developer Mode → right-click your profile → Copy User ID

If `LANYARD_USER_ID` is left as `null`, the widget runs in **demo mode** (cycles through sample tracks every ~11 seconds).

---

### 4. Discord Server Widget

**Steps:**
1. Go to your Discord server → **Server Settings → Widget**
2. Toggle **Enable Server Widget** ON
3. Copy your **Server ID** (right-click server icon → Copy Server ID with Developer Mode on)
4. In `index.html`, find:

```js
const DC_GUILD_ID = null;
const DC_INVITE   = 'https://discord.gg/YOUR_INVITE';
```

Fill them in:

```js
const DC_GUILD_ID = "987654321098765432";
const DC_INVITE   = 'https://discord.gg/yourinvite';
```

If `DC_GUILD_ID` is `null`, the widget shows demo placeholder data.

---

### 5. Profile Photo & Favicon

Replace the image URL in both places:

```html
<!-- profile photo -->
<img src="YOUR_IMAGE_URL" alt="Saturia">

<!-- favicon -->
<link rel="icon" type="image/jpeg" href="YOUR_IMAGE_URL">
<link rel="apple-touch-icon" href="YOUR_IMAGE_URL">
```

---

## File Structure

```
index.html   ← everything (HTML + CSS + JS in one file)
README.md    ← this file
```

---

## Tech Stack

| Thing | Detail |
|---|---|
| Layout | CSS Flexbox, sticky left panel |
| Fonts | Playfair Display + DM Sans (Google Fonts) |
| Icons | Font Awesome 6.4 |
| Particles | Canvas API (vanilla JS) |
| Spotify data | [Lanyard REST API](https://api.lanyard.rest) |
| Discord data | Discord Widget API |
| Animations | CSS keyframes + JS requestAnimationFrame |

---

## Customization Tips

**Change accent colors** — edit the CSS variables at the top of the `<style>` block:
```css
:root {
  --spotify: #1DB954;
  --discord: #5865F2;
  --ig:      #e6683c;
  --tiktok:  #ff0050;
  --globe:   #4A9EFF;
}
```

**Add a new link card** — copy any `.link-card` block and change `data-t`, `href`, icon class, title, and subtitle. Add a matching color rule in CSS:
```css
.link-card[data-t="youtube"] .card-icon { background: rgba(255,0,0,.14); color: #FF0000; }
.link-card[data-t="youtube"] { --pc: #FF0000; --glow: rgba(255,0,0,.15); }
```

---

## License

MIT — use freely, credit appreciated.

---

*Built by Saturia. · 2026*
