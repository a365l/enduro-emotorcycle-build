# CAD & Drawings

Frame measurements, motor mount details, battery box dimensions, and any custom bracket designs.

## Structure

```
03-cad/
├── frame-measurements/     # Key frame dimensions (dropout spacing, tube sizes, etc.)
├── battery-mount/          # Battery mounting bracket design if custom
├── controller-mount/       # Fardriver mounting bracket (aluminium standoffs)
├── drawings/               # Dimensioned sketches / exported PDFs
└── renders/                # CAD renders if modelled
```

## Naming Convention

`[component]_[revision].[ext]`  
Example: `controller-bracket_r1.step`

## Key Dimensions to Document

| Measurement | Value | Notes |
|-------------|-------|-------|
| Rear axle dropout spacing | [X] mm | Must match QS205 axle width |
| QS205 axle width | [X] mm | |
| Battery compartment dimensions | [X × Y × Z] mm | |
| Controller mounting footprint | [X × Y] mm | Standoff positions |
| Wheelbase | [X] mm | |
| Seat height | [X] mm | |
| Ground clearance | [X] mm | |
