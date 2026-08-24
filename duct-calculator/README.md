# Sheet Metal Duct Calculator

A self-contained, single-file web app for sheet metal / spiral duct field work.
Open `index.html` in any browser (works offline, phone-friendly, printable).

## Tools

### Rolling Offset
Enter the rise (vertical offset), roll (horizontal offset), and fitting angle
(90°, 60°, 45°, 30°, 22½°, 15°, or custom). Calculates:

- **True offset** — `√(rise² + roll²)`
- **Travel** — center-to-center length of the diagonal piece: `offset ÷ sin(angle)`
- **Run** — distance used along the main line: `offset ÷ tan(angle)`
- **Roll rotation** — how far to rotate the fittings off plumb: `atan(roll ÷ rise)`
- **Cut length** of the travel piece when a fitting take-out is entered

Set roll to 0 for a flat (single-plane) offset. Includes end-view and side-view
diagrams of the offset triangle.

### Miter Cut Layout
Generates a wrap-around cut layout for cutting round pipe at any angle:

- Enter the total fitting/elbow angle (the pipe is cut at half that angle, then
  one piece is rotated 180° and rejoined), or enter a direct cut angle off square.
- Produces an ordinate table: distance around the pipe from the throat and the
  rise above a squared reference line at each mark
  (`rise = R × tan(cut) × (1 − cos θ)`), plus a drawing of the unrolled cut line.
- Optional **throat length** input: set the exact throat (short-side) length and
  the table adds an "up from pipe end" column (`throat + rise`) so every mark is
  measured from the squared end of the pipe; also reports the resulting heel
  length (`throat + D × tan(cut)`).
- Printable cut sheet.

### Fitting Take-Out
Calculates a fitting's take-out from its actual geometry — enter the fitting
angle, pipe diameter, and either the **throat radius** or the **centerline
radius** (CLR = throat radius + D ÷ 2), plus an optional straight collar length:

- **Take-out** — end of fitting to centerline intersection:
  `CLR × tan(angle ÷ 2) + collar`
- Throat / centerline / heel radii and arc lengths through the fitting
- One-tap button copies the take-out into the Rolling Offset tab so the
  travel piece cut length uses real fitting dimensions
- Dimensioned elbow diagram

### Airflow & Gauges
Reference data for the size you're running:

- **Velocity** from diameter + CFM (`V = CFM ÷ area`, shown in FPM and m/s),
  velocity pressure (`VP = (V ÷ 4005)²`), and straight-duct friction per 100 ft
  (standard galvanized duct equation `0.109136 × CFM^1.9 ÷ D^5.02`)
- **Fitting pressure loss** — approximate loss coefficients (C) for pressed,
  5-gore, 3-gore, and mitered elbows at any standard angle, times VP
- **CFM capacity** of the pipe at 1000 / 1500 / 2000 FPM, labeled with the
  current diameter, plus a built-in capacity chart for all standard spiral
  sizes (3–60″) at 1000–3000 FPM with the entered size highlighted — the
  whole tab re-keys automatically whenever the diameter changes in any tab
- **Typical spiral pipe gauge schedule** (galvanized, SMACNA-style) with the
  current diameter highlighted, plus rule-of-thumb velocity ranges

Reference values are typical — always verify against the current SMACNA HVAC
Duct Construction Standards and project specs.

### SMACNA reference
Field-reference summaries from the SMACNA HVAC Duct Construction Standards
world: what SMACNA is and which manuals apply, the pressure class → seal class
table, leakage classes by seal class for round vs rectangular duct, and round
duct rules of thumb (fitting gauges, hanger spacing, joint sealing, elbow
construction by size). Summaries only — the current manual and project spec
always govern.

### 3D views
Every tab includes an interactive CAD-style 3D model rendered with a built-in
software renderer (no libraries, works offline): the full rolling-offset
assembly showing how the fittings roll, the miter-cut pipe piece with the cut
face highlighted, and the elbow built from the entered radius and collars.
Drag to rotate, pinch or scroll to zoom.

Units toggle between inches (with nearest-1/16″ fractions) and millimeters.
All results are centerline dimensions — allow for seams and connectors per shop
practice.
