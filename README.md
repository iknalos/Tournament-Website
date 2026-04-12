# 🏸 Boston Friendly Tournament V — Registration App

A full-featured tournament registration web app built for **Boston Friendly Badminton Tournament V**, taking place on **May 1st, 2026** at Boston Badminton, 203 Ayer Rd, Harvard MA.

---

## ✨ Features

### Registration Form
- Full RSVP form — name, email, gender, joining status
- **Time availability picker** — players choose how long they can stay (9 PM → Full tournament)
- **T-shirt ordering** — optional add-on with size selection (XS–XXL)
- **Venmo payment integration** — live total calculator, direct Venmo link
- **Tournament regulations modal** — must be read and agreed to before submitting
- Form validation with inline error messages

### Who's Invited Page
- Three-state invite tracking: 🟢 Joining · 🔴 Can't make it · 🟡 No response
- **Smart name matching** — fuzzy match handles "david liang", "Liang David", "David A Liang" all matching "David Liang"
- Filterable by status — tap any summary pill to filter the list
- Summary counts at the top

### Admin Panel (PIN protected)
- Add/remove invites directly from the Invited page when logged in
- Separate admin panel for bulk invite management
- PIN: set in `src/App.jsx` → `ADMIN_PIN` constant
- Invites persist across sessions via localStorage

### Navigation
- Slide-in sidebar navigation (hamburger menu, top-left)
- Four pages: **Register · Invited · Draws · Winners**
- Draws and Winners pages ready for tournament night updates

### Design
- Full-screen photo backgrounds with scroll-driven crossfade between images
- Dark green premium theme with glassmorphism cards
- Fully mobile-first responsive layout

---

## 🗂 Project Structure

```
bbt5-registration/
├── src/
│   ├── App.jsx          # Main application (all components)
│   └── main.jsx         # React entry point
├── index.html           # HTML shell + global styles + Outfit font
├── package.json         # Dependencies
├── vite.config.js       # Vite build config
└── netlify.toml         # Netlify build settings
```

---

## 🚀 Getting Started

### Prerequisites
- Node.js 18+ installed ([nodejs.org](https://nodejs.org))

### Run locally
```bash
# Install dependencies
npm install

# Start dev server
npm run dev
```

### Build for production
```bash
npm run build
# Output goes to /dist — drag this to Netlify Drop
```

---

## 🌐 Deployment

### Netlify (recommended)

**Option A — GitHub (auto-deploys on every push):**
1. Push this repo to GitHub
2. Connect repo in Netlify → Build Settings:
   - Build command: `npm run build`
   - Publish directory: `dist`

**Option B — Drag and drop:**
1. Run `npm run build`
2. Drag the `dist/` folder to [netlify.com/drop](https://app.netlify.com/drop)

---

## ⚙️ Configuration

All key settings are at the top of `src/App.jsx`:

```js
const STORAGE_KEY = "bbt5-v15-regs";   // localStorage key for registrations
const INVITE_KEY  = "bbt5-v15-invites"; // localStorage key for invite list
const ADMIN_PIN   = "012345";           // Change this to your PIN
const SIZES       = ["XS","S","M","L","XL","XXL"];
```

### Changing the background photos
The `PHOTOS` array holds the two background images as base64 data URIs. To replace them:
1. Prepare your image (recommended: ~700×960px, JPEG quality 72–80)
2. Convert to base64: `base64 -w 0 your-image.jpg`
3. Replace the relevant entry in the `PHOTOS` array

---

## 🗄 Database (coming soon — Supabase)

Currently registrations and invites are stored in **localStorage** — data is per-browser and not shared across devices.

Planned upgrade: **Supabase** integration
- All registrations flow into a central Postgres database
- Real-time invite list synced across all devices
- CSV export from a single organiser dashboard
- Video background served from Supabase Storage

When Supabase is connected, replace the two `localStorage` calls in the `persist` and `persistInvites` functions with Supabase client inserts.

---

## 📋 Tournament Details

| Detail | Info |
|--------|------|
| **Date** | Friday, May 1st, 2026 |
| **Time** | 7:30 PM – 12:00 AM |
| **Venue** | Boston Badminton, 203 Ayer Rd, Harvard MA 01451 |
| **Format** | Shuffle doubles — partners change every round |
| **Scoring** | Best of 3 sets · 11 point format |
| **Events** | Men's Doubles · Women's Doubles · Mixed Doubles |
| **Entry fee** | $25 per player (Venmo @Rahul-Solanki-2) |
| **T-shirt** | $12 optional add-on · order by April 18th |
| **Registration deadline** | April 28th |
| **Draws posted** | April 29th |

---

## 📞 Contact

- **Michael Chet** — +1 954-419-3114
- **Rahul Solanki** — +1 617-955-4893 · Venmo @Rahul-Solanki-2

---

## 🛠 Built With

- [React 18](https://react.dev) + [Vite 5](https://vitejs.dev)
- [Outfit Font](https://fonts.google.com/specimen/Outfit) via jsDelivr
- [Netlify](https://netlify.com) for hosting
- Supabase *(planned)*
