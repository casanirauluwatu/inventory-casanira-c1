# Casa Nira · Villa C1 — Upgraded Inventory

A single self-contained web page (`index.html`) showing the FF&E upgrade inventory and
custom-branding catalog for **Villa C1 · Stephanus · The Sanctuary** (3BR, 160 sqm).
Built on the shared Casa Nira inventory template.

## Baseline verification
The retained/upgraded rows were checked line-by-line against Annex I ("Spesifikasi Villa
dan Daftar Perabot") of **`C1_Furniture Agreement_Stephanus Adrianus.pdf`**
(CN-C1-FURN-001, signed 25 July 2025).

- **83 / 83 baseline items matched** on quantity and location
- **0 discrepancies** between the agreement's `Ex:` brands and the page's `prevBrand`

C1-specific corrections applied relative to the C2 document:

| Item | C2 | C1 (per agreement) |
|---|---|---|
| AC Inverter 1.5 PK | Master Bedroom ×1 | Dining, All Bedrooms ×4 |
| AC Inverter 1 PK | ×3 | *not in C1 baseline — row removed* |
| Iron | ×3 | ×1 |
| TV Stand | ×3 | ×1 |
| TV Cabinet / Shelving | ×4 | ×3 |
| Wall Shelving (All Bedrooms) | ×3 | ×2 |
| Outdoor Dining Chair | ×4 | ×3 |
| Water Glass | — | renamed **Glassware Set** |
| Pool Towel | — | renamed **Pool Towel Set** |

Total AC units are unchanged (5): C1 splits them as 2 PK ×1 + 1.5 PK ×4.

### Open items to confirm with the team
- Five linen/kitchen rows carried from the shared upgrade programme are **not itemised in
  C1's Annex I**: Spatula & Cooking Spoon Set, Flat Sheet, Duvet Cover, Waterproof
  Mattress Protector, Duvet Insert. They are shown as *As Is*.
- Annex I lists the bathtub and bathroom mirrors under *Master Bedroom* / *All Bedrooms*;
  the page uses *Master Bathroom* / *All Bathrooms* for clarity.
- "The Sanctuary" estate name is inferred from the C-block convention (not stated in the
  agreement).

## Structure
Everything lives in **`index.html`** — HTML, CSS, and JS in one file, no build step and no
dependencies (fonts load from Google Fonts).

- **`ITEMS`** — the inventory (136 rows): `{ cat, name, location, status, qty, prevBrand, newBrand, note? }`
  - `status`: `"Upgrade"` (gold ribbon, prev → new brand), `"New"` (green ribbon), `"As Is"`.
- **`BRANDED`** — shared custom-branding catalog (In-Room Amenities + Signage) with
  material/finish/dimension specs and Google Drive asset links.

Counts: **136 total · 28 upgraded · 41 new · 67 retained**, plus 21 branding assets.

## Run locally
```bash
python3 -m http.server 4173      # then open http://localhost:4173
```

## Deploy
No build step — fully static. Import the repo at vercel.com/new (Framework: **Other**, no
build command), or run `npx vercel --prod`.

## Notes
- The source agreements (furniture + construction PDFs) are git-ignored — not published.
- "Last updated" shows the current month automatically.
