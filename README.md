# OB Certificate of Appreciation generator (感谢状)

Makes 马来西亚原始佛教会 Certificates of Appreciation that match the original Photoshop template:
the same fonts, sizes, colours, spacing and positions. Works anywhere Python runs: a Claude cloud
session (e.g. from a phone), or a Mac.

## Quick start

```bash
pip install -r requirements.txt
cd Generator
python3 make_certificates.py certificates.xlsx            # every row
python3 make_certificates.py certificates.xlsx --only 3   # just sheet row 3
```

Output goes to `Output/` (not committed): one JPG (2480 x 3508 px, 300 dpi) and one A4 PDF per row,
plus `All certificates (<sheet>).pdf` with every page, for printing.

## Layout of this repo

```
Fonts/       fonts used by the template (private repo, the association's own use only)
Generator/   make_certificates.py, certificates.xlsx (one row per certificate), templates/
SPEC.md      full typography spec, fixed wording, approved examples and gotchas
```

## Spreadsheet columns (sheet `Certificates`)

| column | meaning |
|---|---|
| layout | **B** = date written into the Chinese and English text (Nestlé style). **A** = date on its own line under the signature (Durian style) |
| recipient_line_1 / recipient_line_2 | Recipient; line 2 optional |
| recipient_line_1_pt / recipient_line_2_pt | Optional size in pt. Defaults: 30 pt for one line, 26 pt each for two lines |
| date | e.g. 2026-09-12 |
| event_cn | Chinese event line, e.g. 热心赞助捐血运动 |
| event_en | English line(s) after "In Sincere Appreciation of Your Invaluable". `\|` forces a line break |
| cn_line_1 / en_line_1 | Optional overrides of the fixed first lines |
| file_name | Optional output file name, without extension |

See [SPEC.md](SPEC.md) for everything else.
