# Draw.io Diagram Editing Guide

This guide provides instructions for editing the cluster update process diagram using draw.io (diagrams.net).

## 🚀 Getting Started

### Opening the Diagram

You have three options to edit the diagram:

1. **Online Editor (Recommended)**
   - Visit [app.diagrams.net](https://app.diagrams.net/)
   - Click "Open Existing Diagram"
   - Select `cluster_update_process.drawio` from your local file system
   - Edit and save back to your local file

2. **Desktop Application**
   - Download from [github.com/jgraph/drawio-desktop](https://github.com/jgraph/drawio-desktop/releases)
   - Open `cluster_update_process.drawio` directly

3. **VS Code Extension**
   - Install the [Draw.io Integration extension](https://marketplace.visualstudio.com/items?itemName=hediet.vscode-drawio)
   - Open `.drawio` files directly in VS Code

## 🎨 Design System

### Color Scheme

The diagram uses a consistent color palette. When adding new elements, use these colors:

| Element Type | Fill Color | Stroke Color | Use Case |
|--------------|-----------|--------------|----------|
| **Process Box** | #E8F4F8 (Light Blue) | #2E86AB (Blue) | General process steps |
| **Decision Diamond** | #FFF3E0 (Light Orange) | #FF9800 (Orange) | Decision points |
| **Action Box** | #E8F5E9 (Light Green) | #4CAF50 (Green) | Actionable tasks |
| **Warning Box** | #FFEBEE (Light Red) | #F44336 (Red) | Warnings/cautions |
| **Info Panel** | #F5F5F5 (Light Gray) | #999999 (Gray) | Side information boxes |

### Typography

- **Main text:** Arial, 14px
- **Titles:** Arial, 20px, Bold
- **Code/Commands:** Monospace, 12px
- **Color:** #333333 (Dark Gray) for regular text, #1A1A1A for titles

### Icons

The diagram includes custom icons for:
- GitLab (red/orange logo)
- Docker (blue containers)
- Terminal (command line)
- Singularity (blue sphere)
- TAR/SIF files
- Workflow UI
- Storage
- Registry
- Warning/Success indicators

These icons are embedded in the draw.io file and can be found in the shapes panel on the left.

## ✏️ Common Editing Tasks

### 1. Modify Step Text

1. Click on the text you want to edit
2. Double-click to enter edit mode
3. Type your changes
4. Click outside to save

**Tips:**
- Keep text concise (35 characters or less per line)
- Use multiple text lines for complex descriptions
- Maintain consistent alignment (center-aligned for main workflow)

### 2. Add a New Process Step

1. **Copy an existing step** (recommended for consistency):
   - Select a similar box (e.g., process-box, action-box)
   - Press `Ctrl+C` (or `Cmd+C` on Mac)
   - Press `Ctrl+V` to paste
   - Drag to desired position

2. **Or create from scratch**:
   - Select the rectangle tool from the toolbar
   - Draw a rectangle (340x70 pixels for main workflow)
   - Apply the appropriate color from the color scheme above
   - Add rounded corners (5px radius) in the Format panel
   - Add text by double-clicking inside the shape

3. **Add connecting arrows**:
   - Select the connector tool
   - Click the source shape and drag to the destination
   - The arrow will automatically snap to connection points

### 3. Create a Decision Diamond

1. Select the diamond shape from the shapes panel (or search for "diamond")
2. Resize to approximately 200x80 pixels
3. Apply decision-box colors (light orange fill, orange stroke)
4. Add question text inside
5. Add two arrows:
   - One downward for "Yes" path
   - One sideways for "No" path
6. Label arrows with "Yes" and "No" text if needed

### 4. Add Side Notes/Warnings

1. Create a rectangle on the left (x: 100-380) or right (x: 950+) side
2. Apply warning-box or info-panel styling
3. Add an icon from the shapes panel
4. Add descriptive text
5. Connect to relevant step with a dashed line:
   - Select the connector tool
   - Right-click the line → Format → Dashed

### 5. Update Command Lists

1. Navigate to the "Key Commands" box on the right side (around y: 500)
2. Click inside the text area
3. Edit commands in monospace font
4. Keep one command per line
5. If adding many commands, resize the box:
   - Select the box
   - Drag the corner handles to resize

### 6. Modify Icons

The diagram includes custom SVG icons embedded in the file. To modify:

1. **Change existing icon placement**:
   - Click and drag icons to reposition
   - Use alignment tools (Arrange → Align) for precision

2. **Add new icons**:
   - Import SVG icons: File → Import → choose SVG file
   - Or use draw.io's built-in icon libraries
   - Search for icons in the shapes panel (left sidebar)

## 🎯 Layout Guidelines

### Main Workflow (Center Column)
- **X-position:** Centered around 670px
- **Box width:** 340 pixels
- **Box height:** 70 pixels (simple steps), 90-110 pixels (complex steps)
- **Vertical spacing:** 30-50 pixels between steps

### Side Panels
- **Left notes:** X-position 100-380
- **Right panels:** X-position 950-1270
- **Box width:** 280-320 pixels

### Decision Points
- Place in main workflow at center position
- Allow 80 pixels vertical space for the diamond
- Ensure clear "Yes" and "No" paths

## 💾 Saving and Exporting

### Save as .drawio (Editable Format)

1. File → Save As
2. Keep the `.drawio` extension
3. Save to your repository root

### Export as SVG (For GitHub Display)

1. File → Export as → SVG
2. Settings to use:
   - ✓ Transparent Background (or white, depending on preference)
   - ✓ Include a copy of my diagram
   - Width: Leave as is (1400px)
   - Border width: 0
3. Save as `cluster_update_process.svg`
4. Commit both `.drawio` and `.svg` files to git

**Important:** Always keep both files in sync. When you update the `.drawio` file, remember to export a new `.svg` version.

## 🧪 Best Practices

### Before Making Changes

1. **Create a backup**: Save a copy of the current file
2. **Review existing structure**: Understand how elements are organized
3. **Check git status**: Ensure you're on the correct branch

### While Editing

1. **Maintain consistency**: Use existing colors, fonts, and spacing
2. **Align elements**: Use draw.io's alignment tools (Arrange → Align)
3. **Test connections**: Ensure arrows connect properly to shapes
4. **Use layers**: Organize complex diagrams with layers (View → Layers)
5. **Group related items**: Select multiple items and use Ctrl+G to group

### After Making Changes

1. **Review the diagram**: Zoom out (View → Zoom) to see the full picture
2. **Export to SVG**: Keep the SVG version up to date
3. **Preview in browser**: Open the SVG file to check rendering
4. **Test on GitHub**: Push to a branch and verify GitHub renders it correctly

## 🔧 Advanced Techniques

### Creating Custom Shapes

1. Draw basic shapes (rectangles, circles, lines)
2. Select all shapes that form your custom shape
3. Right-click → Group (or Ctrl+G)
4. Save for reuse: Right-click → Edit Style → Copy Style

### Using Templates

1. Create a reference section with all your standard shapes
2. Place it on a separate layer (View → Layers)
3. Copy shapes from the template as needed
4. Hide the template layer before exporting

### Batch Styling

1. Select multiple shapes (Ctrl+Click or drag selection)
2. Apply style changes in Format panel
3. All selected shapes will update simultaneously

### Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Copy | Ctrl+C (Cmd+C) |
| Paste | Ctrl+V (Cmd+V) |
| Duplicate | Ctrl+D (Cmd+D) |
| Group | Ctrl+G (Cmd+G) |
| Ungroup | Ctrl+Shift+U (Cmd+Shift+U) |
| Align Left | Ctrl+Shift+L |
| Align Center | Ctrl+Shift+C |
| Align Right | Ctrl+Shift+R |
| Send to Back | Ctrl+Shift+B |
| Bring to Front | Ctrl+Shift+F |

## 🐛 Troubleshooting

### Issue: Arrows not connecting properly
**Solution:** Enable connection points (View → Connection Points), then reconnect arrows to the blue X marks.

### Issue: Text overflows box
**Solution:** Either increase box size or reduce font size. Select text and adjust in Format panel.

### Issue: Export looks different from editor
**Solution:** Ensure "Include a copy of my diagram" is checked in export settings. This embeds fonts and ensures consistency.

### Issue: Icons disappeared after export
**Solution:** Icons must be embedded in the file, not linked externally. Re-import icons and embed them (File → Import → check "Embed")

### Issue: SVG not rendering on GitHub
**Solution:** Check SVG file size (GitHub has limits). Simplify the diagram or reduce embedded images if file is too large.

## 📦 Version Control

### Commit Message Format

```
type: brief description

Examples:
- feat: add new validation step before deployment
- fix: correct step 5 arrow alignment
- docs: update command list in side panel
- style: adjust spacing between steps 7 and 8
- refactor: reorganize side panels for better clarity
```

### What to Commit

Always commit both files together:
```bash
git add cluster_update_process.drawio
git add cluster_update_process.svg
git commit -m "feat: add docker cleanup step"
```

### Branching Strategy

```bash
# Feature branches
git checkout -b feature/add-validation-step

# Bug fixes
git checkout -b fix/arrow-alignment

# Documentation updates
git checkout -b docs/update-commands
```

## 🔗 Resources

- [Draw.io Documentation](https://www.drawio.com/doc/)
- [Draw.io Keyboard Shortcuts](https://www.drawio.com/shortcuts)
- [SVG Export Guide](https://www.diagrams.net/doc/faq/export-to-svg)
- [Draw.io Video Tutorials](https://www.youtube.com/c/drawio)
- [Color Picker Tool](https://htmlcolorcodes.com/)

## 📞 Need Help?

- Check the draw.io help: Help → Help in the menu bar
- Visit the [draw.io community forum](https://github.com/jgraph/drawio/discussions)
- See [CONTRIBUTING.md](CONTRIBUTING.md) for workflow guidance

---

**Pro Tip:** Use draw.io's autosave feature (File → Autosave) to prevent losing work. The editor will automatically save to your browser's local storage.
