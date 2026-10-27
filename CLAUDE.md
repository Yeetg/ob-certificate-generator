# OB Certificate of Appreciation generator

This repo makes 马来西亚原始佛教会 Certificates of Appreciation (感谢状) that match the original Photoshop template exactly.

## To make certificates
1. `pip install --break-system-packages -q -r requirements.txt`
2. Put the request into `Generator/certificates.xlsx` (sheet `Certificates`, one row per certificate) with openpyxl. The columns are listed in README.md.
3. `cd Generator && python3 make_certificates.py certificates.xlsx --only <row>`. Leave out `--only` to make every row.
4. Report every `note:` (a line was shrunk to fit) and `SKIPPED` message the script prints.
5. Look at the output JPG before delivering. Send the JPG and the A4 PDF from `Output/`, plus the combined PDF for a batch.

## Rules
- Don't redraw or position text by eye. If the generator can't do something, extend `make_certificates.py`.
- Read `SPEC.md` when a request goes beyond the spreadsheet columns: a new layout, new fixed wording, a size question, or a new PSD template.
- Don't commit `Output/`. Commit only lasting changes: script fixes, new layouts, standard rows Yee wants kept.
- Recipient font: **Cinzel Medium** (default). Sizes: 24 pt for one line; 20 pt over 22 pt for two lines (approved for "DOB DESIGN & BUILD / Mr Chia Kwee Yang").
- Previous recipient fonts are kept for reference. Brush Script MT is `Fonts/Brush Script.ttf`; see the font history in SPEC.md. Use one only when Yee asks, via the `recipient_font` column.
