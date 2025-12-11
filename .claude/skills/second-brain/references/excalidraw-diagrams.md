# Excalidraw Diagrams in Obsidian

> Complete guide for creating and editing Excalidraw diagrams programmatically

---

## Overview

Excalidraw is a virtual whiteboard tool that integrates with Obsidian via the [obsidian-excalidraw-plugin](https://github.com/zsviczian/obsidian-excalidraw-plugin). Claude can create diagrams by generating the appropriate file format.

---

## File Format

### File Extension

Use `.excalidraw.md` - this is the preferred format that combines markdown with Excalidraw drawing data.

### Complete File Structure

```markdown
---
excalidraw-plugin: parsed
tags:
  - excalidraw
  - {{topic-tag}}
excalidraw-default-mode: view
---

# {{Diagram Title}}

Optional markdown content here. Anything between frontmatter and `# Excalidraw Data` is preserved and visible in reading mode.

# Excalidraw Data

## Text Elements
{{text element content here, one per line with ID}}

## Drawing
```json
{
  "type": "excalidraw",
  "version": 2,
  "source": "https://excalidraw.com",
  "elements": [],
  "appState": {
    "gridSize": null,
    "viewBackgroundColor": "#ffffff"
  },
  "files": {}
}
`` `
```

**Note:** The JSON in `## Drawing` can be compressed (LZ-String algorithm) or uncompressed. For programmatic creation, use uncompressed JSON.

---

## Frontmatter Options

```yaml
---
excalidraw-plugin: parsed                    # Required - tells plugin this is Excalidraw
tags:
  - excalidraw
excalidraw-default-mode: view                # view | zen (default viewing mode)
excalidraw-export-transparent: true          # PNG/SVG export transparency
excalidraw-export-dark: false                # Export in dark mode
excalidraw-export-padding: 10                # Export padding in pixels
excalidraw-export-pngscale: 1                # PNG export scale factor
excalidraw-link-prefix: ""                   # Prefix for internal links
excalidraw-url-prefix: ""                    # Prefix for URLs
excalidraw-link-brackets: true               # Show brackets around links
---
```

---

## JSON Schema

### Top-Level Structure

```json
{
  "type": "excalidraw",
  "version": 2,
  "source": "https://excalidraw.com",
  "elements": [],
  "appState": {},
  "files": {}
}
```

| Field | Type | Description |
|-------|------|-------------|
| `type` | string | Always `"excalidraw"` |
| `version` | number | Schema version (use `2`) |
| `source` | string | Origin URL |
| `elements` | array | Drawing elements (shapes, text, etc.) |
| `appState` | object | Editor state (background, grid, etc.) |
| `files` | object | Embedded images (base64) |

### AppState

```json
{
  "appState": {
    "gridSize": null,
    "viewBackgroundColor": "#ffffff"
  }
}
```

| Property | Type | Description |
|----------|------|-------------|
| `gridSize` | number/null | Grid size (null = no grid) |
| `viewBackgroundColor` | string | Canvas background color |

---

## Element Types

### Supported Types

| Type | Description |
|------|-------------|
| `rectangle` | Rectangle shape |
| `ellipse` | Oval/circle shape |
| `diamond` | Diamond/rhombus shape |
| `line` | Straight or multi-point line |
| `arrow` | Line with arrowhead(s) |
| `text` | Text element |
| `freedraw` | Freehand drawing |
| `image` | Embedded image |

---

## Common Element Properties

All elements share these base properties:

```json
{
  "id": "unique-id-string",
  "type": "rectangle",
  "x": 100,
  "y": 100,
  "width": 200,
  "height": 100,
  "angle": 0,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "groupIds": [],
  "frameId": null,
  "roundness": null,
  "seed": 1234567890,
  "version": 1,
  "versionNonce": 987654321,
  "isDeleted": false,
  "boundElements": null,
  "updated": 1699999999999,
  "link": null,
  "locked": false
}
```

### Property Reference

| Property | Type | Values | Description |
|----------|------|--------|-------------|
| `id` | string | unique | Unique identifier (use UUID or random string) |
| `type` | string | see types | Element type |
| `x`, `y` | number | coordinates | Top-left position |
| `width`, `height` | number | pixels | Dimensions |
| `angle` | number | radians | Rotation (0 = no rotation) |
| `strokeColor` | string | hex color | Outline color |
| `backgroundColor` | string | hex/name | Fill color or `"transparent"` |
| `fillStyle` | string | see below | Fill pattern |
| `strokeWidth` | number | 1, 2, 4 | Line thickness |
| `strokeStyle` | string | solid/dashed/dotted | Line style |
| `roughness` | number | 0, 1, 2 | Hand-drawn effect (0=none, 2=max) |
| `opacity` | number | 0-100 | Transparency |
| `groupIds` | array | strings | Group membership |
| `seed` | number | integer | Random seed for consistent rendering |
| `version` | number | integer | Increments on each change |
| `versionNonce` | number | integer | Random, regenerated on change |

### Fill Styles

| Value | Description |
|-------|-------------|
| `"solid"` | Solid fill |
| `"hachure"` | Diagonal lines (default) |
| `"cross-hatch"` | Cross-hatched lines |

### Roundness

For rounded corners on rectangles/diamonds:

```json
{
  "roundness": {
    "type": 3
  }
}
```

---

## Shape Elements

### Rectangle

```json
{
  "id": "rect-1",
  "type": "rectangle",
  "x": 100,
  "y": 100,
  "width": 200,
  "height": 100,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "#a5d8ff",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "angle": 0,
  "groupIds": [],
  "frameId": null,
  "roundness": { "type": 3 },
  "seed": 123456789,
  "version": 1,
  "versionNonce": 987654321,
  "isDeleted": false,
  "boundElements": null,
  "updated": 1699999999999,
  "link": null,
  "locked": false
}
```

### Ellipse

```json
{
  "id": "ellipse-1",
  "type": "ellipse",
  "x": 350,
  "y": 100,
  "width": 150,
  "height": 100,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "#b2f2bb",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "angle": 0,
  "groupIds": [],
  "frameId": null,
  "roundness": { "type": 2 },
  "seed": 234567890,
  "version": 1,
  "versionNonce": 876543210,
  "isDeleted": false,
  "boundElements": null,
  "updated": 1699999999999,
  "link": null,
  "locked": false
}
```

### Diamond

```json
{
  "id": "diamond-1",
  "type": "diamond",
  "x": 550,
  "y": 100,
  "width": 120,
  "height": 120,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "#ffec99",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "angle": 0,
  "groupIds": [],
  "frameId": null,
  "roundness": { "type": 2 },
  "seed": 345678901,
  "version": 1,
  "versionNonce": 765432109,
  "isDeleted": false,
  "boundElements": null,
  "updated": 1699999999999,
  "link": null,
  "locked": false
}
```

---

## Linear Elements (Line & Arrow)

Lines and arrows use a `points` array for multi-point paths.

### Arrow

```json
{
  "id": "arrow-1",
  "type": "arrow",
  "x": 300,
  "y": 150,
  "width": 100,
  "height": 0,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "angle": 0,
  "points": [
    [0, 0],
    [100, 0]
  ],
  "lastCommittedPoint": null,
  "startBinding": null,
  "endBinding": null,
  "startArrowhead": null,
  "endArrowhead": "arrow",
  "groupIds": [],
  "frameId": null,
  "roundness": { "type": 2 },
  "seed": 456789012,
  "version": 1,
  "versionNonce": 654321098,
  "isDeleted": false,
  "boundElements": null,
  "updated": 1699999999999,
  "link": null,
  "locked": false
}
```

### Arrow Properties

| Property | Type | Values | Description |
|----------|------|--------|-------------|
| `points` | array | `[[x,y], ...]` | Path points relative to x,y |
| `startArrowhead` | string/null | `"arrow"`, `"bar"`, `"dot"`, `"triangle"`, `null` | Start arrowhead |
| `endArrowhead` | string/null | same as above | End arrowhead |
| `startBinding` | object/null | binding info | Connection to start element |
| `endBinding` | object/null | binding info | Connection to end element |

### Line (no arrowheads)

```json
{
  "id": "line-1",
  "type": "line",
  "x": 100,
  "y": 300,
  "width": 200,
  "height": 100,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "dashed",
  "roughness": 1,
  "opacity": 100,
  "angle": 0,
  "points": [
    [0, 0],
    [100, 50],
    [200, 100]
  ],
  "lastCommittedPoint": null,
  "startBinding": null,
  "endBinding": null,
  "startArrowhead": null,
  "endArrowhead": null,
  "groupIds": [],
  "frameId": null,
  "roundness": { "type": 2 },
  "seed": 567890123,
  "version": 1,
  "versionNonce": 543210987,
  "isDeleted": false,
  "boundElements": null,
  "updated": 1699999999999,
  "link": null,
  "locked": false
}
```

---

## Text Elements

```json
{
  "id": "text-1",
  "type": "text",
  "x": 120,
  "y": 130,
  "width": 160,
  "height": 25,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "angle": 0,
  "text": "Hello World",
  "fontSize": 20,
  "fontFamily": 1,
  "textAlign": "center",
  "verticalAlign": "middle",
  "baseline": 18,
  "containerId": null,
  "originalText": "Hello World",
  "lineHeight": 1.25,
  "groupIds": [],
  "frameId": null,
  "roundness": null,
  "seed": 678901234,
  "version": 1,
  "versionNonce": 432109876,
  "isDeleted": false,
  "boundElements": null,
  "updated": 1699999999999,
  "link": null,
  "locked": false
}
```

### Text Properties

| Property | Type | Values | Description |
|----------|------|--------|-------------|
| `text` | string | any | The displayed text |
| `fontSize` | number | pixels | Font size (16, 20, 28, 36) |
| `fontFamily` | number | 1, 2, 3 | 1=Virgil (hand), 2=Helvetica, 3=Cascadia (code) |
| `textAlign` | string | left/center/right | Horizontal alignment |
| `verticalAlign` | string | top/middle/bottom | Vertical alignment |
| `containerId` | string/null | element ID | If text is inside a shape |
| `originalText` | string | same as text | Original text before wrapping |
| `lineHeight` | number | 1.25 | Line spacing multiplier |

---

## Text Elements Section

The `## Text Elements` section lists text content for searchability:

```markdown
## Text Elements
Hello World ^text-1
Another Label ^text-2
```

Format: `{text content} ^{element-id}`

---

## Color Palette

### Default Colors

| Color | Hex | Use |
|-------|-----|-----|
| Black | `#1e1e1e` | Default stroke |
| White | `#ffffff` | Background |
| Red | `#e03131` | Alerts, errors |
| Orange | `#fd7e14` | Warnings |
| Yellow | `#fab005` | Highlights |
| Green | `#2f9e44` | Success |
| Blue | `#1971c2` | Primary |
| Violet | `#7048e8` | Accent |
| Gray | `#868e96` | Neutral |

### Background Colors (lighter versions)

| Color | Hex |
|-------|-----|
| Light Red | `#ffc9c9` |
| Light Orange | `#ffd8a8` |
| Light Yellow | `#ffec99` |
| Light Green | `#b2f2bb` |
| Light Blue | `#a5d8ff` |
| Light Violet | `#d0bfff` |
| Light Gray | `#dee2e6` |

---

## Complete Example: Flowchart

```markdown
---
excalidraw-plugin: parsed
tags:
  - excalidraw
  - flowchart
---

# Simple Flowchart

A basic decision flowchart.

# Excalidraw Data

## Text Elements
Start ^text-start
Decision? ^text-decision
Yes ^text-yes
No ^text-no
End ^text-end

## Drawing
```json
{
  "type": "excalidraw",
  "version": 2,
  "source": "https://excalidraw.com",
  "elements": [
    {
      "id": "start",
      "type": "ellipse",
      "x": 100,
      "y": 50,
      "width": 100,
      "height": 60,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "#b2f2bb",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "groupIds": [],
      "frameId": null,
      "roundness": { "type": 2 },
      "seed": 111111111,
      "version": 1,
      "versionNonce": 111111112,
      "isDeleted": false,
      "boundElements": [{ "id": "text-start", "type": "text" }],
      "updated": 1699999999999,
      "link": null,
      "locked": false
    },
    {
      "id": "text-start",
      "type": "text",
      "x": 125,
      "y": 68,
      "width": 50,
      "height": 25,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "transparent",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "text": "Start",
      "fontSize": 20,
      "fontFamily": 1,
      "textAlign": "center",
      "verticalAlign": "middle",
      "baseline": 18,
      "containerId": "start",
      "originalText": "Start",
      "lineHeight": 1.25,
      "groupIds": [],
      "frameId": null,
      "roundness": null,
      "seed": 111111113,
      "version": 1,
      "versionNonce": 111111114,
      "isDeleted": false,
      "boundElements": null,
      "updated": 1699999999999,
      "link": null,
      "locked": false
    },
    {
      "id": "decision",
      "type": "diamond",
      "x": 75,
      "y": 180,
      "width": 150,
      "height": 100,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "#ffec99",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "groupIds": [],
      "frameId": null,
      "roundness": { "type": 2 },
      "seed": 222222221,
      "version": 1,
      "versionNonce": 222222222,
      "isDeleted": false,
      "boundElements": [{ "id": "text-decision", "type": "text" }],
      "updated": 1699999999999,
      "link": null,
      "locked": false
    },
    {
      "id": "text-decision",
      "type": "text",
      "x": 105,
      "y": 217,
      "width": 90,
      "height": 25,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "transparent",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "text": "Decision?",
      "fontSize": 20,
      "fontFamily": 1,
      "textAlign": "center",
      "verticalAlign": "middle",
      "baseline": 18,
      "containerId": "decision",
      "originalText": "Decision?",
      "lineHeight": 1.25,
      "groupIds": [],
      "frameId": null,
      "roundness": null,
      "seed": 222222223,
      "version": 1,
      "versionNonce": 222222224,
      "isDeleted": false,
      "boundElements": null,
      "updated": 1699999999999,
      "link": null,
      "locked": false
    },
    {
      "id": "arrow-start-decision",
      "type": "arrow",
      "x": 150,
      "y": 110,
      "width": 0,
      "height": 70,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "transparent",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "points": [[0, 0], [0, 70]],
      "lastCommittedPoint": null,
      "startBinding": null,
      "endBinding": null,
      "startArrowhead": null,
      "endArrowhead": "arrow",
      "groupIds": [],
      "frameId": null,
      "roundness": { "type": 2 },
      "seed": 333333331,
      "version": 1,
      "versionNonce": 333333332,
      "isDeleted": false,
      "boundElements": null,
      "updated": 1699999999999,
      "link": null,
      "locked": false
    },
    {
      "id": "end",
      "type": "ellipse",
      "x": 100,
      "y": 350,
      "width": 100,
      "height": 60,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "#ffc9c9",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "groupIds": [],
      "frameId": null,
      "roundness": { "type": 2 },
      "seed": 444444441,
      "version": 1,
      "versionNonce": 444444442,
      "isDeleted": false,
      "boundElements": [{ "id": "text-end", "type": "text" }],
      "updated": 1699999999999,
      "link": null,
      "locked": false
    },
    {
      "id": "text-end",
      "type": "text",
      "x": 130,
      "y": 368,
      "width": 40,
      "height": 25,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "transparent",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "text": "End",
      "fontSize": 20,
      "fontFamily": 1,
      "textAlign": "center",
      "verticalAlign": "middle",
      "baseline": 18,
      "containerId": "end",
      "originalText": "End",
      "lineHeight": 1.25,
      "groupIds": [],
      "frameId": null,
      "roundness": null,
      "seed": 444444443,
      "version": 1,
      "versionNonce": 444444444,
      "isDeleted": false,
      "boundElements": null,
      "updated": 1699999999999,
      "link": null,
      "locked": false
    },
    {
      "id": "arrow-decision-end",
      "type": "arrow",
      "x": 150,
      "y": 280,
      "width": 0,
      "height": 70,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "transparent",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "points": [[0, 0], [0, 70]],
      "lastCommittedPoint": null,
      "startBinding": null,
      "endBinding": null,
      "startArrowhead": null,
      "endArrowhead": "arrow",
      "groupIds": [],
      "frameId": null,
      "roundness": { "type": 2 },
      "seed": 555555551,
      "version": 1,
      "versionNonce": 555555552,
      "isDeleted": false,
      "boundElements": null,
      "updated": 1699999999999,
      "link": null,
      "locked": false
    }
  ],
  "appState": {
    "gridSize": null,
    "viewBackgroundColor": "#ffffff"
  },
  "files": {}
}
`` `
```

---

## Best Practices

### 1. Unique IDs
Generate unique IDs for each element. Use descriptive names like `rect-header`, `arrow-1-2`, `text-title`.

### 2. Consistent Seeds
Use random seed values (large integers) for consistent hand-drawn rendering.

### 3. Text in Shapes
To put text inside a shape:
1. Create the shape with `boundElements` referencing the text ID
2. Create the text with `containerId` referencing the shape ID
3. Position the text centered within the shape

### 4. Connecting Arrows
Position arrows between shapes by calculating:
- Start point: edge of source shape
- End point: edge of target shape
- Use `points` array for the path

### 5. Layout Guidelines
- Start shapes at coordinates like (100, 100)
- Use consistent spacing (e.g., 50-100px between elements)
- Align related elements on a grid

### 6. Version Fields
Always include:
- `version`: 1 (increment on edits)
- `versionNonce`: random integer
- `updated`: timestamp in milliseconds

---

## Trigger Phrases

Claude should recognize these phrases for Excalidraw:

- "create a diagram"
- "draw a flowchart"
- "make an excalidraw"
- "visualize this"
- "sketch this out"
- "diagram showing..."
- "create a visual"

---

## Limitations

1. **Complex diagrams**: Very detailed diagrams may be better created in the Excalidraw UI
2. **Images**: Embedding images requires base64 encoding in the `files` object
3. **Curved arrows**: Complex curved paths need multiple points in the `points` array
4. **Hand-drawn feel**: The `roughness` and `seed` values affect the sketchy appearance

---

## References

- [Obsidian Excalidraw Plugin](https://github.com/zsviczian/obsidian-excalidraw-plugin)
- [Excalidraw JSON Schema](https://docs.excalidraw.com/docs/codebase/json-schema)
- [Creating Elements Programmatically](https://docs.excalidraw.com/docs/@excalidraw/excalidraw/api/excalidraw-element-skeleton)
