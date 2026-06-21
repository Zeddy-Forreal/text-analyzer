<div align="center">

<img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" />
<img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" />
<img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" />

# ¶ Emu — Text Analyzer

A pink-on-midnight text analysis tool built with pure HTML, CSS, and JavaScript. Paste any text and instantly get character, word, and space counts, plus a live character density breakdown — no backend, no dependencies.

[Features](#-features) · [Getting Started](#-getting-started) · [File Structure](#-file-structure) · [Customization](#-customization)

</div>

---

## ✨ Features

* 🔤 **Kinetic Headline** — The hero title animates in with a drawing underline, treating the headline itself as a typographic specimen
* 📊 **Instant Text Stats** — Character, word, and space counts update the moment you click analyze
* 📈 **Character Density Chart** — A sorted, gradient-filled bar chart shows exactly how often each letter appears, with staggered entrance animation
* ✂️ **Trim to Size** — Set a character limit and trim your text down to fit, with a live warning indicator if you're over the limit
* 🧹 **One-Click Clear** — Wipe the input, stats, and density chart back to their empty state instantly
* 🌗 **Light / Dark Mode** — Toggle the entire palette via a single button, swapping CSS custom properties on the fly
* 📱 **Fully Responsive** — Stat cards and density bars reflow cleanly down to small mobile screens

---

## 🚀 Getting Started

**1. Clone the repository**

```bash
git clone https://github.com/Zeddy-Forreal/text-analyzer.git
cd text-analyzer
```

**2. Open in browser**

No build step, no installs. Just open `index.html` directly:

```bash
# macOS
open index.html

# Windows
start index.html

# Linux
xdg-open index.html
```

**3. Analyze some text**

Paste or type text into the input box and hit the play button. Set a number in the size field and hit the scissors icon to trim your text down to that length first.

---

## 📁 File Structure

```
text-analyzer/
├── index.html            Markup and structure
├── style/
│   └── main.css            All styling, theming, and chart animations
└── javascript/
    └── main.js              Counting logic, density calculation, and mode toggle
```

---

## ⚙️ How It Works

Word, character, and space counts are derived from a single trimmed copy of the input text:

```javascript
letters = msg.split("");
letts   = letters.filter((l) => l != " ");
spaces  = letters.filter((l) => l == " ");
words   = msg.split(" ").filter((word) => /\p{L}/u.test(word) == true);
```

Character density is built by counting occurrences of each unique lowercase letter, then rendering them as sorted, percentage-width bars:

```javascript
letters_used.forEach((letter) => {
    let total = letts
        .map((l) => l.toLowerCase())
        .filter((l) => l == letter).length;
    add_to_array(letter, total);
});
add_to_page(array_of_bars, total_number); // sorts by total, renders bars
```

Light and dark mode are just two arrays of four colors swapped into CSS custom properties:

```javascript
function change_col(arr){
    document.documentElement.style.setProperty('--bg', arr[0]);
    document.documentElement.style.setProperty('--text', arr[1]);
    document.documentElement.style.setProperty('--dbg', arr[2]);
    document.documentElement.style.setProperty('--col1', arr[3]);
}
```

---

## 🎨 Customization

All colors and fonts are CSS custom properties at the top of `main.css`. Edit these to retheme the whole app:

```css
:root{
  --bg:        #181c30;   /* Page background          */
  --text:      #f4f3fb;   /* Primary text              */
  --dbg:       #262c4a;   /* Card / panel background   */
  --dbg2:      #2f3658;   /* Secondary panel shade      */
  --col1:      #ff5d8f;   /* Primary accent color       */
  --col1-soft: #ff8aab;   /* Gradient / hover accent    */
  --muted:     #8d92b8;   /* Secondary / muted text     */
}
```

The light/dark palettes swapped by the mode toggle live in `main.js` and can be edited directly:

```javascript
let modes = [
    ["#f3f1fa", "#181c30", "#ffffff", "#ff5d8f"],   // light mode
    ["#181c30", "#f4f3fb", "#262c4a", "#ff5d8f"]    // dark mode
]
```

---

<div align="center">

Made with 🖤 by [Zeddy-Forreal](https://github.com/Zeddy-Forreal)

</div>
