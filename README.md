# pdweb

Browser-based display quality control tools for DICOM-calibrated displays.

---

## TG270-sQC (`sqc.html`)

Quick visual evaluation of display performance per AAPM Report 270.

**Pattern features:**
- 18 grayscale squares (3 rows × 6 columns) covering gray levels 0–255
- Each square contains upper-left (−5 GL) and lower-right (+5 GL) modulation bar patterns
- The first and last squares use reduced contrast (3 GL) in their outer patterns
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
  - Outer columns: 8 GL contrast; inner columns: 2 GL contrast
- High-contrast line pair patterns (2, 4, 6 px) in top/bottom regions
- Full vertical gradient strips, each with a ±3 GL sinusoidal center strip (periods 4π ≈ 12.6 px and 3π ≈ 9.4 px)

**Controls:**
- Click and drag to pan
- Ctrl + scroll wheel to zoom (1×–10×), centered on cursor
- ⟲ button to reset view

---

## TG18-OIQ (`tg18oiq.html`)

Overall image quality evaluation based on AAPM TG18-OIQ (TG18-QC without the Cx patterns), scaled to fit the window.

**Pattern features:**
- 16 gray steps from 8 to 248 in steps of 16, each with ±4 GL low-contrast corner patches
- Black and white cells with centered patches at 13 (5%) and 242 (95%)
- Luminance ramps either side, window response bands and a crosstalk section
- "QUALITY CONTROL" lettering on black, mid-gray and white panels, one contrast per letter (±14 down to ±1 GL)
- Spatial resolution blocks at the center and four corners: high (0/255) and low (128/130) contrast, 1 and 2 px bars in both directions

**Usage:**
- On a DICOM-conformant display, all low-contrast corner patches should be equally visible
- The high-contrast line pairs in the center and corners should appear crisp
- All letters of QUALITY CONTROL should be visible
- The 0/5% and 95/100% patches are not a reliable indicator of display performance

**Controls:**
- Click and drag to pan
- Ctrl + scroll wheel to zoom (1×–10×), centered on cursor
- ⟲ button to reset view

---

## Ambient Light Verification (`ambtest.html`)

Tests whether ambient lighting conditions are appropriate for diagnostic reading.

**How it works:**
- A low-contrast bar pattern object (6 px period, default 3 GL contrast) is randomly placed in the central 80% of the display
- The user tries to locate and click the object
- Success/failure is reported; results can optionally be shared via email

**Controls:**
- Left-click the contrast display to increase contrast; right-click to decrease
- Shift+left-click anywhere: increase contrast
- Shift+right-click anywhere: decrease contrast
- Alt+left-click anywhere: shift base level up
- Alt+right-click anywhere: shift base level down
- Up/Down Arrow: increase/decrease contrast
- Left/Right Arrow: shift base level down/up
- "Move" button to reposition the object

**URL parameters:**
| Parameter | Description | Default |
|---|---|---|
| `?contrast=N` | Initial contrast (0–255) | 3 |
| `?lockcontrast` (or `?lock`) | Prevent contrast changes | — |
| `?email=addr` | Enable email result sharing | — |

---

## Gray Levels (`grays.html`)

Full-screen uniform gray level display for evaluating grayscale response and uniformity.

**Controls:**
- Left-click anywhere / Scroll up / Up Arrow: increase gray level by step size
- Right-click anywhere / Scroll down / Down Arrow: decrease gray level by step size
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
