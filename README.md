# pacsDisplay Web Tools

Browser-based display quality control tools for DICOM-calibrated displays.

---

## TG270-sQC (`sqc.html`)

Quick visual evaluation of display performance per AAPM Report 270.

**Pattern features:**
- 18 grayscale squares (3 rows × 6 columns) covering gray levels 0–255
- Each square contains upper-left (−5 GL) and lower-right (+5 GL) modulation bar patterns
- Corner squares use reduced contrast (±3 GL)
- Three 256×256 large squares (black, mid-gray, white) for luminance measurement
- Full-width 0–255 gradient bar with line pattern verification strips

**Controls:**
- Click and drag to pan
- Ctrl + scroll wheel to zoom (1×–10×), centered on cursor
- ⟲ button to reset view

---

## TG270-pQC (`pqc.html`)

Comprehensive display evaluation based on the TG18-PQC design, per AAPM Report 270.

**Pattern features:**
- 18 horizontal grayscale bars (0–255 in 15 GL steps)
- Horizontal and vertical modulation patterns at 4 frequencies (18, 12, 6, 4 px)
  - Inner columns: 8 GL contrast; outer columns: 2 GL contrast
- High-contrast line pair patterns (2, 4, 6 px) in top/bottom regions
- Full vertical gradient strips with modulation for uniformity assessment

**Controls:**
- Click and drag to pan
- Ctrl + scroll wheel to zoom (1×–10×), centered on cursor
- ⟲ button to reset view

---

## Ambient Light Verification (`ambtest.html`)

Tests whether ambient lighting conditions are appropriate for diagnostic reading.

**How it works:**
- A low-contrast bar pattern object (6 px period, default 3 GL contrast) is randomly placed on the display
- The user tries to locate and click the object
- Success/failure is reported; results can optionally be shared via email

**Controls:**
- Left-click the contrast display (or Shift+left-click anywhere) to increase contrast
- Right-click (or Shift+right-click) to decrease contrast
- "Move" button to reposition the object

**URL parameters:**
| Parameter | Description | Default |
|---|---|---|
| `?contrast=N` | Initial contrast (0–255) | 3 |
| `?lockcontrast` | Prevent contrast changes | — |
| `?email=addr` | Enable email result sharing | — |

---

## Gray Levels (`grays.html`)

Full-screen uniform gray level display for evaluating grayscale response and uniformity.

**Controls:**
- Left-click anywhere: increase gray level by step size
- Right-click anywhere: decrease gray level by step size
- Click the number input to type a value directly (0–255)
- Dropdown to select step size (1, 5, or 15)
- ⌗ button to toggle a 3×3 grid overlay for uniformity assessment

**URL parameters:**
| Parameter | Description | Default |
|---|---|---|
| `?gray=N` | Initial gray level (0–255) | 120 |
| `?step=N` | Step size (1, 5, or 15) | 15 |
| `?grid=true` | Show grid on load | false |

---

## Uniformity Scan (`scan.html`)

Systematically scans a white box across the entire display surface in serpentine fashion to identify non-uniformities, bad pixels, and mura.

**Controls:**
| Input | Action |
|---|---|
| Scroll down / Right arrow (hold) | Advance box forward |
| Scroll up / Left arrow (hold) | Reverse direction |
| Space | Toggle auto-play forward |
| Shift+Space | Toggle auto-play backward |
| Left-click / Up arrow | Increase gray level |
| Right-click / Down arrow | Decrease gray level |
| Box size input | Set box dimensions (px) |
| Gray dropdown | Select gray level (15, 120, 240) |

**URL parameters:**
| Parameter | Description | Default |
|---|---|---|
| `?size=N` | Initial box size (px) | 300 |
| `?gray=N` | Initial gray level | 120 |
