# 🎬 CineMemory

**On This Day in Cinema History** — A daily journey through the seventh art.

![CineMemory Preview](https://img.shields.io/badge/Cinema-History-gold?style=for-the-badge&logo=film)
![HTML](https://img.shields.io/badge/HTML5-Vanilla-orange?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)

CineMemory is a single-page website that displays cinema history events for each day of the year. Discover births of legendary directors and actors, iconic film releases, technological inventions that shaped filmmaking, historic moments, fascinating curiosities, and award ceremonies.

## ✨ Features

- **📅 Daily Cinema History** — Browse events for any day of the year
- **🌍 Bilingual** — Full Italian and English support
- **🏷️ 6 Event Categories:**
  - 🟠 **Birth** — Directors, actors, writers, composers, and other film professionals
  - 🔵 **Release** — Film premieres and theatrical releases
  - 🟣 **Historic Event** — Major moments in the film industry itself
  - 🟢 **Curiosity** — Fun facts and behind-the-scenes stories
  - 🔴 **Invention** — Technological breakthroughs (from thaumatrope to CGI)
  - 🟡 **Award** — Oscars, Palme d'Or, Golden Globes
- **🔍 Search & Filter** — Find specific events, people, or films
- **📖 Expandable Details** — Click any card to read an in-depth version of the event
- **⌨️ Keyboard Navigation** — Use arrow keys to browse days
- **📱 Responsive Design** — Works on all devices
- **🎨 Cinema-inspired Dark Theme** — Elegant gold accents

## 🚀 Live Demo

Simply open `index.html` in any modern browser, or host it on GitHub Pages.

### GitHub Pages Deployment

1. Fork or clone this repository
2. Go to **Settings → Pages**
3. Select **Source: Deploy from a branch**
4. Choose **main** branch and **/ (root)** folder
5. Your site will be live at `https://yourusername.github.io/cinememory/`

## 📁 Project Structure

```
cinememory/
├── index.html          # Complete single-page application
├── data/                # One JSON file per month
│   ├── january.json
│   ├── february.json
│   ├── march.json
│   ├── april.json
│   ├── may.json
│   ├── june.json
│   ├── july.json
│   ├── august.json
│   ├── september.json
│   ├── october.json
│   ├── november.json
│   └── december.json
└── README.md            # This file
```

The app is a single HTML file — no build tools, no dependencies, no frameworks — that fetches the relevant month's JSON file on demand.

**Important:** month files must be named in **English, lowercase**, exactly as listed above. `index.html` requests them at runtime as `data/{month}.json` (e.g. `data/august.json`), so any other name or capitalization will fail to load.

## 🎬 Data Format

Each month file is a JSON object. Keys are `"month-day"` (e.g. `"8-1"` for August 1st), and each value is an array of events for that day:

```json
{
  "8-1": [
    {
      "year": 1899,
      "cat": "birth",
      "it": "Titolo breve in italiano",
      "en": "Short title in English",
      "it_d": "Descrizione breve per la card (100-150 caratteri).",
      "en_d": "Short description for the card (100-150 characters).",
      "it_long": "Descrizione estesa mostrata quando si clicca sulla card: contesto, aneddoti, perché l'evento conta nella storia del cinema.",
      "en_long": "Extended description shown when the card is clicked: context, anecdotes, why the event matters in cinema history."
    }
  ]
}
```

### Field Reference

| Field | Type | Description |
|-------|------|--------------|
| `year` | Number | Year of the event |
| `cat` | String | One of: `birth`, `release`, `historic`, `curiosity`, `invention`, `award` |
| `it` / `en` | String | Short event title, Italian / English |
| `it_d` / `en_d` | String | Short description (~100-150 characters), shown on the card |
| `it_long` / `en_long` | String | Extended description (~400-800 characters), shown in the modal when the card is clicked. Should add real depth — not just a longer rephrasing of `it_d`/`en_d` |

If `it_long`/`en_long` is missing for an older entry, the app automatically falls back to showing `it_d`/`en_d` in the modal, so partially updated months won't break.

## 🎯 Event Categories Guide

| Category | Icon | Color | What to Include |
|----------|------|-------|-----------------|
| `birth` | 👤 | Orange | Directors, actors, writers, composers, cinematographers, costume designers, etc. whose work significantly impacted cinema |
| `release` | 🎬 | Blue | Film premieres, theatrical releases, significant distribution milestones |
| `historic` | ⏰ | Purple | Events belonging to the film industry itself: strikes, studio foundations, festival launches, censorship cases, award ceremonies |
| `curiosity` | ❓ | Green | Fun facts, behind-the-scenes stories, record-breaking moments — always tied directly to filmmaking |
| `invention` | 💡 | Red | Cameras, film stock, sound systems, special effects, projection technology, digital innovations |
| `award` | 🏆 | Gold | Oscars, Cannes, Venice, Berlin, Golden Globes, BAFTAs, major festival wins |

## ✅ Inclusion Criteria (read this before adding events)

An event only belongs in the database if it is **directly** part of cinema history — not merely connectable to it through a chain of reasoning.

**✅ Include:**
- Birth/death of someone who worked **in** film: director, actor, screenwriter, cinematographer, editor, composer, costume designer, producer, influential critic.
- The actual release, premiere, or festival screening date of a film.
- Invention or patent of technology used in filmmaking.
- Industry milestones: studio foundations, strikes, festival or award launches, historic theater openings/closures, censorship cases.
- Award ceremonies, on the exact day they took place.

**❌ Avoid these patterns:**
- "Birth of [non-film person], whose life later inspired the film X" — this is a biographical fact, not a cinema event, unless the film itself was released that day.
- "[Historical event] happened, later depicted in the film X" — same issue; being dramatized years later doesn't make something a cinema-history event.
- Vague claims with no specific name or title, like "figures who influenced [place]'s cinema."
- Filler entries like "Film X is still dominating the box office" on a date that isn't its actual release or a meaningful anniversary.
- Any chain requiring more than one logical step to reach cinema (e.g. a scientist's discovery that enabled a technology later used in film).

**Rule of thumb:** if you find yourself writing "inspired" or "later depicted in" to justify including a non-film event, leave it out.

Quality over quantity: there's no fixed number of events per day. Three well-verified entries are better than twelve where half are filler.

A ready-to-use prompt for generating new month files with an AI assistant, following these exact criteria, is available on request — see the Contributing section below.

## 🌐 Internationalization

The site supports Italian (default) and English. All UI text is stored in the `i18n` object inside `index.html`:

```javascript
const i18n = {
  it: {
    logoSub: 'Accadde oggi nel cinema',
    heroSubtitle: 'Accadde oggi nella storia del cinema',
    // ... more strings
  },
  en: {
    logoSub: 'Today in cinema history',
    heroSubtitle: 'On this day in cinema history',
    // ... more strings
  }
};
```

To add a new UI language, create a new object with all the required keys.

## 🎨 Customization

### Colors

CSS custom properties are defined in `:root`:

```css
:root {
  --gold: #D4A843;        /* Primary accent */
  --bg-dark: #0A0A0F;     /* Background */
  --cat-birth: #E67E22;   /* Birth category */
  --cat-release: #3498DB; /* Release category */
  /* ... etc */
}
```

### Fonts

The site uses Google Fonts:
- **Playfair Display** — Elegant serif for titles
- **Inter** — Clean sans-serif for body text

## 📊 Database Statistics

The database currently covers all 12 months, with multiple verified events per day across all 6 categories, spanning from ancient history to the present.

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Add more events** — Research and add accurate cinema history events, following the [Inclusion Criteria](#-inclusion-criteria-read-this-before-adding-events) above
2. **Fix errors** — Correct any factual or typographical mistakes
3. **Improve translations** — Enhance Italian or English text
4. **Add features** — Suggest or implement new functionality

### Contribution Guidelines

1. Fork the repository
2. Create a feature branch (`git checkout -b add-january-events`)
3. Add your events to the correct `data/{month}.json` file, filling in both the short (`_d`) and extended (`_long`) descriptions
4. Verify dates and facts against reliable sources
5. Test in multiple browsers
6. Submit a pull request

## 📜 License

MIT License — Feel free to use, modify, and distribute.

## 👩‍💻 Author

**Noemi Marcolini**

- 📧 Email: [noemi.marcolini@gmail.com](mailto:noemi.marcolini@gmail.com)
- ☕ Support: [Ko-fi](https://ko-fi.com/noemimarcolini)

---

<p align="center">
  <em>Every day is a day in cinema history.</em>
</p>

<p align="center">
  Made with ❤️ for the seventh art
</p>
