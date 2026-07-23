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
- Printable cut sheet.

Units toggle between inches (with nearest-1/16″ fractions) and millimeters.
All results are centerline dimensions — allow for seams and connectors per shop
practice.
