# LAMUGBA CORE™ 24/7 — Project Documentation

## 1. Project Overview
* **Client:** Lamugba CDO 24/7 (Lifestyle District, Corrales Ext., Cagayan de Oro City)
* **Business Model:** 24/7 Fast-Casual Diner, Tapsilogan & Catering
* **System Name:** **LAMUGBA CORE™ 24/7** (Smart POS & Automated Inventory Defense ERP)
* **GitHub Repository:** [https://github.com/jasonvelasquez1410/lamugba-pos-system](https://github.com/jasonvelasquez1410/lamugba-pos-system)
* **Live Production URL:** [https://lamugba-pos-system.vercel.app](https://lamugba-pos-system.vercel.app)
* **Local Workspace:** `c:\Users\USER\Documents\Programming Folder Rep\LAMUGBA POS INVENTORY SYSTEM`

---

## 2. Core Business Problems Solved
1. **Unreported Stock & Inventory Shrinkage:** High-volume late-night shifts (graveyard) at Lifestyle District suffered from missing proteins and eggs with shifts blaming each other.
   * *Solution:* 3-Minute Shift Handover Audit (Tab 3) with live physical count vs expected stock formula and automatic Peso loss calculation.
2. **"Screen-Only" Billing & Cash Pocketing:** Staff showing bills on screen without a physical paper trail, then clearing orders and verbally ordering food from the kitchen.
   * *Solution:* Enforced printed Billing Statement + automated Kitchen Order Ticket (KOT). Kitchen never prepares food without a system-generated slip.
3. **BIR Tax Compliance & Penalty Prevention:** Custom POS systems without formal BIR Permit to Use (PTU) accreditation cannot legally print "Official Receipts".
   * *Solution:* The POS prints an itemized **Billing Statement / Guest Check** carrying the required BIR disclaimer. Manual BIR Official Receipts remain at the cashier counter.
4. **Portion Creep & Unlinked Depletion:**
   * *Solution:* Recipe Bill of Materials (BOM) engine that automatically subtracts raw marinated beef tapa (100g), farm eggs (pcs), sinangag rice (cups), and sodas in real time upon billing.

---

## 3. Implemented Modules & Features

### Module 1: Fast POS & Billing Terminal
* **Menu Catalog & Pricing:**
  * Silog: Tapsilog (₱180), Chopsilog (₱180), Bangsilog (₱180), Tocilog (₱155), Chicksilog (₱130), Longsilog (₱120).
  * Sizzlers: Pork Sisig (₱187), Chicken Sisig (₱167).
  * Drinks: Coke Regular Can (₱65), Bottled Water (₱30).
  * Add-ons: Garlic Sinangag Rice (₱25), Sunny-Side Egg (₱20).
* **Billing Engine:** Auto-computes 12% EVAT, tender calculations, quick cash chips (`Exact`, `₱200`, `₱500`, `₱1,000`, `GCash QR`).
* **Instant Demo Readiness:** Pre-loads a sample starter dish (Tapsilog) and exact cash on load so the billing button is always clickable.
* **Anti-Theft Manager PIN Override:** Deleting or voiding punched items requires 4-digit Manager PIN (`1234`).
* **Thermal Output Modal:**
  * ESC/POS 80mm Billing Statement slip format with jagged paper cut simulation.
  * Kitchen Order Ticket (KOT) toggle showing table number, timestamp, and preparation remarks.

### Module 2: Recipe BOM & Live Inventory Depletion
* Visual stock gauges with progress bars for critical raw items (Beef Tapa packs, Farm Eggs, Sisig pre-mix).
* Real-time deduction: Punching items subtracts raw inventory balances live.
* Recipe BOM Inspector: Breakdown of food costs and gross profit margin (e.g. Tapsilog: ₱64.20 cost vs ₱180.00 selling price = 64.3% gross profit margin).

### Module 3: 24/7 Shift Handover & Stock Variance Audit
* Multi-shift selector: Day (7 AM–3 PM), Night (3 PM–11 PM), Graveyard (11 PM–7 AM).
* Formula: `[Starting Stock] + [Restocked] - [POS Depleted] - [Logged Spoilage] = Expected Stock`.
* Interactive inputs: Typing physical counts immediately updates discrepancies and displays financial loss in **RED**.
* Dual digital sign-off banner for outgoing cashier and incoming supervisor.

### Module 4: Purchasing & Commissary Prep Batches
* Supplier scale receiving weight verification (PO vs digital scale reading).
* 50kg beef batch marination yield tracker (yielding 492 portions at 98.4% efficiency).

### Module 5: Manager Security Audit Trail
* Chronological immutable event stream recording printed billing slips, blocked unauthorized voids, mid-shift vault drops, and shift openings.

---

## 4. Design & Responsiveness
* **Light SaaS Mode (Default):** Clean slate canvas (`#f8fafc`), crisp white cards (`#ffffff`), warm amber (`#f59e0b`) and flame orange (`#ea580c`) accents.
* **Dark Mode Toggle:** Top-right moon/sun toggle for late-night/dim lighting cashier environments.
* **Mobile & Tablet Responsive:**
  * Breakpoints at 1100px, 1024px, and 900px automatically collapse grids to single-column view.
  * Tested on touch devices: large tap targets, scroll-free header navigation, mobile-safe modal dialogues.

---

## 5. File Inventory
* `index.html` — Complete standalone Single Page Application (HTML, CSS, JS).
* `lamugba-logo.jpg` — Brand mascot emblem.
* `tapsilog.jpg` — Dish photography for Tapsilog.
* `sisig.jpg` — Dish photography for Sizzling Pork Sisig.
* `chicksilog.jpg` — Dish photography for Chicksilog.
* `.gitignore` — Ignore node_modules, .vercel, logs.
* `PROJECT.md` — System documentation and resumption guide.

---

## 6. How to Run & Resume Work After Restart

### Local Development:
* Open `index.html` in any browser, or run via live-server / VS Code Live Server.

### Deploying Updates to Vercel:
Pushing to the GitHub `main` branch automatically triggers Vercel to rebuild and redeploy:
```bash
git add .
git commit -m "feat: your update message"
git push origin main
```

### Next Steps Upon Client Agreement:
1. Connect backend database (Supabase / PostgreSQL) for persistent shift logs and multi-device sync.
2. Configure local ESC/POS thermal printer integration (USB/LAN direct printing).
3. Connect kitchen display or dedicated thermal kitchen printer.
