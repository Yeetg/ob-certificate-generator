# Certificate spec

## Typography (taken from the PSDs; document is 300 dpi, so px = pt x 300/72)

| Element | Font (PostScript name) | File in Fonts/ | Size | Colour | Tracking |
|---|---|---|---|---|---|
| Recipient name | **Cinzel Medium** (free Google font, SIL Open Font License; weight 500 instance of the variable font) | Cinzel-Medium.ttf | single line 24 pt; two lines 20 pt over 22 pt (approved for DOB Design & Build) | black #010101 | 50 |
| Chinese description | Aa筆墨春秋超清楷书 (`AaBMCQCQKSNon-CommercialUse`) | BiMoChunQiu-ChaoQingKaiShu-2.ttf | 17 pt | brown #472E18 | 75 |
| English description | Apple Chancery (`Apple-Chancery`) | Apple Chancery.ttf | 16 pt, line spacing 80 px | brown #472E18 | 75 |
| Date under signature (layout A) | SIL Kai (`SIL-Kai-Reg-Jian`), **not available** | digits: FreeSerif.ttf at 54 px; 年 月 日: glyph images in Generator/templates | 13 pt | black | 75 |

- Font names in Photoshop and Font Book are the font's *internal* name, not its file name. That's why "AaBMCQCQKS" is `BiMoChunQiu-...ttf`.
- The Chinese font is licensed **for non-commercial use only**.
- Lines too wide for the gold line under the name (1,149 px; limit 1,100 px) or for the description area (limit 1,420 px) are shrunk automatically, as the PSD did for long company names.

### Recipient font history (kept for reference)
Previous fonts stay in `Fonts/` or on Yee's Mac. Pick one for a single certificate with the `recipient_font` column.

| Period | Font | File | Sizes | Notes |
|---|---|---|---|---|
| Current (from 27 Oct 2026) | Cinzel Medium | `Fonts/Cinzel-Medium.ttf` | 24 pt single; 20 / 22 pt two lines | Chosen by Yee over Cormorant Garamond, Libre Baskerville, GFS Didot and Pinyon Script as the most solemn and formal. Lowercase letters print as small capitals, and all-capital company names look natural. |
| 25 to 27 Oct 2026 | Brush Script MT (`BrushScriptMT`) | `Fonts/Brush Script.ttf` | 30 pt single (Nestlé template; ×1.137 for person names); two lines approved at 20.6 / 26 pt | From the Chuang Chern Yunn / Nestlé PSD. Yee found 30 pt too big for two lines. All-capital names look crowded in this script. |
| Original Durian PSD | 汉仪行楷简 (`HYi1gj`) | not in repo; on Yee's Mac: `OB-Cert/Fonts/HanYiXingKaiJian-1.ttf` | 32 pt English name, 25 pt Chinese name (with stroke) | Used for "Durian Justgo / 陈建勋先生（弘至）". |

## Fixed wording and layouts
- Chinese line 1: 发心护持马来西亚原始佛教会
- English line 1: "In Sincere Appreciation of Your Invaluable" (sits at centre x = 1219 px, as in the original; everything else is centred at 1240 px)
- **Layout B** (date in text):
  - Chinese: line 1 / 于2026年9月12日 / event_cn
  - English: line 1 / event_en / "on 12th September 2026". If the date fits, it is added to the end of the last event_en line, e.g. "Charity Run on 19th October 2025".
  - No date under the signature.
- **Layout A** (date below):
  - Chinese: line 1 / event_cn
  - English: line 1 / event_en
  - Date 2026年9月12日 under "Ven. Bhikkhu Bodhidipa".

## Approved examples (25 Oct 2026)
- DOB DESIGN & BUILD / Mr Chia Kwee Yang, blood donation, 12 Sep 2026 (rows 2 and 3 of certificates.xlsx)
  - Layout A: event_cn 捐血运动
  - Layout B: event_cn 热心赞助捐血运动
  - English event line for both: "Contribution at the Blood Donation Event"
  - Recipient: Cinzel 20 pt / 22 pt (27 Oct 2026). Earlier approved in Brush Script MT at 20.6 pt / 26 pt.

## Templates
`Generator/templates/layout_A_date_below.png` (from the "Durian Carnival" PSD) and `layout_B_date_in_text.png` (from the "Chuang Chern Yunn"/Nestlé PSD) are the original artwork with all variable text removed. To support a new design, analyse its PSD with psd-tools (text layers give font, size, tracking, colour and position), make a new blank template the same way, and add an entry to `LAYOUTS` in make_certificates.py.

## Always
- Look at the result before delivering it.
- Report every `note:` (auto-shrunk line) and `SKIPPED` message the script prints.
- Don't redraw text by eye. For anything the generator can't express, extend the script.
