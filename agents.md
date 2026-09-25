# 🤖 LAMBO — IDE Agent Instructions

> This file provides instructions for AI coding agents working on the LAMBO project.
> Read this file **before making any code changes**.

---

## Project Identity

**LAMBO** = *Landscape Analytics for Monitoring Botanical Observation*
A student-centered wildling/seedling monitoring web app built for campus forestry programs.

---

## Tech Stack (DO NOT change without explicit approval)

| Layer | Technology | Version |
|-------|-----------|---------|
| Frontend | React + Vite | React 18, Vite 5+ |
| Styling | TailwindCSS | v3 |
| Routing | React Router | v6 |
| Charts | Chart.js + react-chartjs-2 | Latest |
| QR Codes | qrcode.react | Latest |
| Excel Export | xlsx (SheetJS) | Latest |
| HTTP Client | Axios | Latest |
| Backend | Node.js + Express | Node 18+, Express 4 |
| Database | MongoDB + Mongoose | Latest |
| Auth | JWT (jsonwebtoken + bcryptjs) | Latest |
| Images | Cloudinary | v2 |
| Upload | Multer | Latest |
| Validation | express-validator | Latest |

---

## Project Structure Rules

```
LAMBO/
├── client/          ← React + Vite frontend (ALL frontend code goes here)
├── server/          ← Node.js + Express backend (ALL backend code goes here)
├── DESIGN/          ← Design boards (READ-ONLY — never modify these files)
├── plan.md          ← Implementation plan (reference for task breakdown)
├── agents.md        ← This file
├── Idea.md          ← Original feature ideas
└── README.md        ← Project documentation
```

### Critical Rules
1. **NEVER modify files inside `DESIGN/`** — these are read-only reference design boards
2. **Frontend code goes in `client/src/`** — follow the component hierarchy:
   - `components/layout/` — AppShell, Header, BottomNav
   - `components/ui/` — Reusable generic UI primitives (Button, Card, Chip, Input, etc.)
   - `components/tree/` — Tree-specific components (TreeCard, GrowthChart, QRCodeDisplay, etc.)
   - `components/dashboard/` — Dashboard-specific components
   - `pages/` — Page-level components (one per route)
   - `services/` — API call modules (one per resource)
   - `context/` — React context providers
   - `hooks/` — Custom React hooks
   - `utils/` — Pure utility functions
3. **Backend code goes in `server/src/`** — follow the MVC pattern:
   - `models/` — Mongoose schemas
   - `controllers/` — Request handlers
   - `routes/` — Express router definitions
   - `middleware/` — Auth, upload, error handling
   - `config/` — DB connection, Cloudinary setup
   - `utils/` — Helper functions
4. **Never install new packages** without checking if an existing dependency already covers the need
5. **Keep dependencies minimal** — this is a student project, not an enterprise app

---

## Design System — MANDATORY Visual Standards

The app uses a **tactical army-green aesthetic**. Reference: `DESIGN/DESIGN.md`

### Color Palette (use these TailwindCSS custom colors)
```
Surfaces:
  surface-base:    #282E16  (main background)
  surface-deep:    #1D230E  (header/nav)
  surface-card:    #30371A  (card backgrounds)
  surface-raised:  #38411F  (hover/active)
  surface-highest: #485327  (elevated)

Text:
  text-primary:    #F0F3E8  (primary text — cream white)
  text-secondary:  #D8DFC8  (secondary text)
  text-muted:      #AAB596  (muted text)
  text-accent:     #C2CE9F  (labels, metadata)

Accents:
  accent-primary:  #A4B566  (links, active states, icons)
  accent-container:#8B9B4C  (button backgrounds)
  accent-dim:      #6B7D3B  (secondary accent)

Borders:
  border-default:  #525E31
  border-accent:   #5D6A37
  border-subtle:   #454F26

Status:
  status-healthy:  #A4B566  (green)
  status-monitor:  #D99B26  (amber)
  status-danger:   #E57373  (red)
```

### Typography
- **Headings & Body:** `Chivo` (Google Fonts)
- **Labels, Data, Monospace:** `JetBrains Mono` (Google Fonts)
- All labels should use uppercase tracking (letter-spacing: 0.04-0.1em)

### Component Rules
- **Border radius:** Minimal (`0.25rem` default, `0.5rem` for cards)
- **Buttons:** Uppercase monospaced text, sharp corners, accent-container background
- **Cards:** `surface-card` background, `border-default` border, optional 2px top accent bar
- **Chips/Badges:** 24px height, tight padding, status-color-coded with 20% opacity background
- **Inputs:** `surface-deep` background, `border-default` → `accent-primary` on focus
- **No shadows** — use tonal layering and borders for depth (military instrument aesthetic)

### Before Creating Any UI Component
1. Check the relevant design board screenshot in `DESIGN/` folder
2. Match the layout, spacing, and visual hierarchy from the design
3. Use the design tokens above — **do not hardcode hex colors inline** unless they exactly match a token
4. Check `DESIGN/DESIGN.md` for component specifications

---

## Data Models — Key Constraints

### User
- `rollNumber` is the unique identifier for login
- Passwords are **always** bcrypt hashed (never store plaintext)
- JWT token expires in 7 days

### Tree
- `treeId` is auto-generated with format `LMB-XXXX` (e.g., LMB-0001, LMB-0002)
- Every tree **must** have an `owner` (the student who registered it)
- Students can only see/edit their own trees (filter by `owner` in every query)
- `species` uses the standard species list from `utils/constants.js`

### GrowthLog
- `height` is the **only required measurement** — all others are optional
- Every log entry **must** reference a `tree` and `loggedBy` user
- Logs are displayed in reverse chronological order (newest first)
- When a log is created, update the parent tree's `healthStatus`, `currentStage`, and `updatedAt`

---

## API Conventions

### Request/Response Format
- All API responses follow: `{ success: boolean, data: any, message: string }`
- Error responses follow: `{ success: false, message: string, errors: [] }`
- Use HTTP status codes correctly (200, 201, 400, 401, 404, 500)

### Authentication
- JWT is sent as `Authorization: Bearer <token>` header
- The `auth` middleware extracts user ID from JWT and attaches `req.user`
- All tree/log endpoints require authentication

### File Upload
- Use Multer with memory storage (buffer)
- Upload to Cloudinary, store the returned URL
- Max file size: 5MB
- Accepted formats: JPEG, PNG, WebP

---

## v1.0 Feature Scope — What to Build

### ✅ Build These
- Student registration & login (roll number + password + JWT)
- Register trees (species, nickname, location, date, photo) → auto tree ID + QR code
- QR code generation + downloadable PNG
- Growth log entries (height required; diameter, leaves, fruit, stage, health, photo, notes optional)
- Push notifications or reminders
- Dashboard (stats grid, health donut chart, recent activity)
- Tree list (filterable by species/health)
- Tree profile (vitals, photos, growth timeline)
- QR code scanning with camera
- Growth charts (Chart.js line chart — height over time)
- Export to Excel (.xlsx)
- Bottom navigation (Home, Trees, Logs, Register, Scan)
- Offline mode or service workers
- Campus map visualization


### 🚫 DO NOT Build These (v2.0+)
- Teacher/admin roles or role-based access control
- Gamification, badges, or achievements
- Species-specific care guides
- Survival tracker percentages
- Peer sharing or social features
- AR scanning, LiDAR, or any advanced sensor features

---

## Development Workflow

### Running the Project
```bash
# Terminal 1: Backend
cd server
cp .env.example .env  # Fill in MongoDB URI, JWT secret, Cloudinary keys
npm install
npm run dev            # nodemon on port 5000

# Terminal 2: Frontend
cd client
npm install
npm run dev            # Vite on port 5173 (proxied to :5000)
```

### Before Committing Code
1. Ensure `npm run build` passes in `client/`
2. Ensure the server starts without errors
3. Test the primary flows manually:
   - Register → Login → Register Tree → Add Growth Log → View Dashboard
4. Check mobile viewport (375px) — the app is mobile-first

---

## Code Style Guidelines

### JavaScript/React
- Use functional components with hooks (no class components)
- Use `async/await` for all async operations (no raw `.then()` chains)
- Destructure props in function signatures
- Use meaningful component and variable names
- Keep components focused — if a component exceeds ~150 lines, split it
- Use `try/catch` blocks for API calls with proper error feedback

### File Naming
- Components: `PascalCase.jsx` (e.g., `TreeCard.jsx`)
- Hooks: `camelCase.js` with `use` prefix (e.g., `useTrees.js`)
- Services: `camelCase.js` with `Service` suffix (e.g., `treeService.js`)
- Utils: `camelCase.js` (e.g., `formatters.js`)
- Models: `PascalCase.js` (e.g., `Tree.js`)

### Comments & Documentation
- Add JSDoc comments to all service functions
- Add brief comments above complex logic
- Keep existing comments unless directly editing that code

---

## Species List (for presets)

These are the target species for Filipino wildling programs. Use as default options in species selection:

1. Mango (*Mangifera indica*)
2. Guyabano (*Annona muricata*)
3. Jackfruit (*Artocarpus heterophyllus*)
4. Coconut (*Cocos nucifera*)
5. Calamansi (*Citrofortunella microcarpa*)
6. Avocado (*Persea americana*)
7. Papaya (*Carica papaya*)
8. Banana (*Musa acuminata*)
9. Durian (*Durio zibethinus*)
10. Rambutan (*Nephelium lappaceum*)
11. Cacao (*Theobroma cacao*)
12. Coffee (*Coffea arabica*)
13. Narra (*Pterocarpus dalbergioides*)
14. Mahogany (*Swietenia macrophylla*)
15. Ipil-ipil (*Leucaena leucocephala*)

---

## Growth Stages (ordered progression)

```
Seedling → Vegetative → Flowering → Fruit Set → Ripening → Harvest
```

## Health Statuses

```
Healthy | Monitoring | Needs Attention
```

---

## Key Reference Files

| File | Purpose |
|------|---------|
| `plan.md` | Full implementation plan with phases and file breakdown |
| `Idea.md` | Original feature brainstorm (full vision, not just v1) |
| `DESIGN/DESIGN.md` | Complete design system specification |
| `DESIGN/*/screen.png` | Visual design boards for each page |
| `DESIGN/*/code.html` | Reference HTML/Tailwind implementations |
