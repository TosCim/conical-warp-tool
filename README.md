🔗 **Live demo:** https://toscim.github.io/conical-warp-tool/conical-warp-tool.html

# Conical Warp Tool

A free, open-source, browser-based tool for distorting flat artwork to match the conical (frustum) shape of buckets, cups, and other tapered containers. No installation needed — runs entirely in the browser as a single HTML file.

## The Problem

When printing labels for tapered containers (buckets, paint cans, cups), flat rectangular artwork must be distorted into a circular sector (cone frustum development) so that it appears correct once wrapped around the container. Professional solutions like Esko Studio Toolkit or Ai Toolbox for Adobe Illustrator cost hundreds of euros and require specific software. Free alternatives for Affinity Designer or Inkscape users simply did not exist — until now.

## Features

- **Conical warp distortion** — mathematically accurate polar coordinate remapping with bilinear interpolation
- **Preset bucket database** — select from pre-loaded container dimensions, auto-calculates label diameters
- **Flat artwork calculator** — computes the exact flat artwork dimensions (width = π × top diameter) with configurable overlap and bleed margins
- **Adjustable label position** — set label height and offset from bottom, diameters are computed automatically using the linear taper coefficient
- **Multiple export formats:**
  - **PNG** — high resolution raster image of the distorted artwork
  - **PDF** — real-size PDF with embedded raster artwork + vector die-line (cut contour in magenta) + registration marks
  - **SVG die-line** — vector-only cut contour with registration marks, ready for plotter
- **Configurable DPI** — 72, 150, 200, or 300 DPI output
- **Bilingual UI** — Italian / English language toggle
- **100% client-side** — no server, no uploads, no dependencies, works offline
- **Single HTML file** — just download and double-click to open in any browser

## How to Use

1. Download `conical-warp-tool.html`
2. Open it in any modern browser (Chrome, Firefox, Edge, Safari)
3. Select a bucket from the dropdown or enter dimensions manually
4. Adjust label height, offset from bottom, overlap and bleed
5. Load your flat artwork as a high-resolution PNG or JPG
6. Click **Apply Conical Distortion**
7. Download the result as PNG, PDF (with die-line), or SVG die-line

## Artwork Preparation

Export your flat artwork from your vector editor (Affinity Designer, Inkscape, Illustrator, etc.) as a **PNG at 300 DPI** at the real dimensions:

- **Width** = circumference of the top (wider) edge of the label = π × top diameter + overlap
- **Height** = label height + bleed

The tool shows the exact calculated dimensions after you select a bucket and set the label parameters.

## Technical Notes

- The flat artwork is mapped from rectangular coordinates to polar (conical) coordinates using pixel-by-pixel remapping with bilinear interpolation
- The cone frustum development (sector of an annulus) is computed from the container's top diameter, bottom diameter, and label height
- The PDF generator creates a valid PDF 1.4 file with the JPEG image embedded as a DCTDecode XObject, plus vector die-line paths rendered as cubic Bézier curves
- The SVG die-line uses proper circular arc commands at millimeter scale with CutContour layer naming (industry standard for plotter recognition)
- Registration marks are placed near the four corners of the sector for optical sensor alignment

## Workflow for Print Production

1. Design your artwork flat in your vector editor
2. Export as high-res PNG
3. Use this tool to generate the conical preview + PDF with die-line
4. Send the PDF to the print shop for proof printing
5. Send the original flat vector file (PDF/X-4 CMYK) to the bucket manufacturer for production

## Adding Custom Buckets

The bucket database is a simple JavaScript array at the top of the `<script>` section. To add a bucket:

```javascript
{ name: "20lt - Custom", base: 30.0, bocca: 33.5, h: 37.0 },
```

- `name`: display name in dropdown
- `base`: bottom diameter in cm
- `bocca`: top (mouth) diameter in cm
- `h`: total height in cm

## Browser Compatibility

Works in all modern browsers: Chrome, Firefox, Edge, Safari. Requires JavaScript and HTML5 Canvas support.

## License

MIT License — free for personal and commercial use.

## Credits

Built with assistance from Claude (Anthropic). Developed for the paint manufacturing industry (colorificio) where tapered bucket label design is a daily need.

## Contributing

Contributions welcome! If you use different containers or have feature requests, please open an issue or submit a pull request.
