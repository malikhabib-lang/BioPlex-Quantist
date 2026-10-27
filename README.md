# Bio-Plex Manager → Quantist

Converts a Bio-Plex Manager Excel report export (.xlsx) into an xPONENT-format batch CSV that Quantist can open.

- Static single page (`index.html`), no build step, no server code.
- The workbook is read in the browser with SheetJS; nothing is uploaded.
- `tools/bioplex_to_xponent.py` is the same conversion as a command-line script:
  `python tools/bioplex_to_xponent.py export.xlsx`

## Mapping
FI → Median · FI − Bkgd → Net MFI · Bead Count → Count · Obs Conc → Result ·
Exp Conc → expected standard/control concentrations · Dilution → Dilution Factor.
Well types B, S#, C#, X# → Background0, Standard#, Control#, Unknown# (or the well description).

## Notes
Unofficial tool. Total Events = sum of per-region bead counts; control ranges default to ±30 % of expected;
Bio-Plex curve coefficients are not carried over (Quantist refits); wells are numbered column-wise.

## Deploy
Push to GitHub, then in Vercel: Add New → Project → import the repo → Framework preset "Other" → Deploy.
