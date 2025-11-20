# Contributing to the Cluster Update Diagram

Thank you for helping maintain our documentation! This guide will help you collaborate on the diagram.

## 🚀 Quick Start

### Prerequisites
- Git installed on your machine
- Web browser (for draw.io online editor)
- OR draw.io desktop application (optional)
- OR VS Code with draw.io extension (optional)

### Initial Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd <repository-name>
   ```

2. **Create a feature branch**
   ```bash
   git checkout -b update-diagram-<your-change>
   ```

3. **Open the diagram in draw.io**
   - Visit [app.diagrams.net](https://app.diagrams.net/)
   - Click "Open Existing Diagram"
   - Select `cluster_update_process.drawio` from your local file system

## 📝 Making Changes

### For Simple Text Updates

1. **Open the diagram**
   - Use [app.diagrams.net](https://app.diagrams.net/) and open `cluster_update_process.drawio`
   - Or use VS Code with the [draw.io extension](https://marketplace.visualstudio.com/items?itemName=hediet.vscode-drawio)

2. **Find and edit text**
   - Click on the text element you want to change
   - Double-click to edit
   - Type your changes
   - Click outside the element to save

3. **Save your changes**
   - File → Save As
   - Save back to `cluster_update_process.drawio`

### For Structural Changes

If you need to add/remove steps or modify the flow:

1. **Understand the layout**
   - Main workflow: Center column (around x=670)
   - Side notes: Left (x=100-380) and right (x=950-1270)
   - Consistent spacing: 30-50 pixels between steps

2. **Use existing patterns**
   - Copy similar elements (Ctrl+C, Ctrl+V)
   - Maintain the color scheme (see below)
   - Use alignment tools (Arrange → Align)

3. **Maintain consistency**
   - Use the same fonts (Arial for text, monospace for code)
   - Follow the color scheme for different box types
   - Keep icons consistent with existing style

4. **Test your changes**
   - Zoom out to see the full diagram (View → Zoom)
   - Check that arrows connect properly
   - Ensure no text overflows boxes

### Color Scheme

**Always use these colors for consistency:**

| Element Type | Fill Color | Stroke Color | Use Case |
|--------------|-----------|--------------|----------|
| Process Box | #E8F4F8 | #2E86AB | General process steps |
| Decision Diamond | #FFF3E0 | #FF9800 | Decision points |
| Action Box | #E8F5E9 | #4CAF50 | Actionable tasks |
| Warning Box | #FFEBEE | #F44336 | Warnings/cautions |
| Info Panel | #F5F5F5 | #999999 | Side information |

## 💾 Saving and Exporting

### IMPORTANT: Two Files to Maintain

When you make changes, you must update **both** files:

1. **cluster_update_process.drawio** (editable source)
   - This is the source of truth
   - Edit this file with draw.io

2. **cluster_update_process.svg** (for GitHub display)
   - Export from draw.io after editing
   - GitHub displays this in README

### Export to SVG

After editing the `.drawio` file:

1. File → Export as → SVG
2. Settings:
   - ✓ Transparent Background (or white)
   - ✓ Include a copy of my diagram
   - Width: Leave as is (1400px)
   - Border width: 0
3. Save as `cluster_update_process.svg` (overwrite existing)

## 🔍 Review Process

### Before Committing

**Checklist:**
- [ ] Changes made in draw.io (`.drawio` file)
- [ ] Exported to SVG (`.svg` file updated)
- [ ] SVG opens correctly in a browser
- [ ] All text is readable and properly positioned
- [ ] Colors and styling are consistent
- [ ] Changes align with the actual cluster update process
- [ ] Commit message clearly describes the change

### Commit Your Changes

```bash
# Stage BOTH files
git add cluster_update_process.drawio
git add cluster_update_process.svg

# Commit with a descriptive message
git commit -m "feat: add new Docker cleanup verification step"

# Push to your branch
git push origin update-diagram-<your-change>
```

**Note:** Always commit both files together to keep them in sync.

### Create a Pull Request

1. Go to the repository on GitHub
2. Click "Pull Requests" → "New Pull Request"
3. Select your branch
4. Fill in the PR description:
   - What changed and why?
   - Which step(s) were modified?
   - Any special considerations?
   - Screenshot of the updated diagram (optional but helpful)

5. Use the PR template if available
6. Request review from team members
7. Address any feedback
8. Once approved, merge to main

## 🎨 Editing Tips

### Common Tasks

**Adding a new step:**
1. Copy an existing step box (Ctrl+C, Ctrl+V)
2. Drag to the desired position
3. Edit the text (double-click)
4. Add connectors (use the connector tool)
5. Ensure proper spacing (30-50px between steps)

**Updating step text:**
1. Click the text element
2. Double-click to edit
3. Type your changes
4. Click outside to save

**Adding a decision point:**
1. Search for "diamond" in shapes panel
2. Drag diamond shape to canvas
3. Resize to ~200x80 pixels
4. Apply decision-box colors (light orange fill, orange stroke)
5. Add question text inside
6. Add "Yes" and "No" paths with arrows

**Adding a warning note:**
1. Create a rectangle on the left or right side
2. Apply warning-box colors (light red fill, red stroke)
3. Add warning icon from shapes panel
4. Add text inside
5. Connect to relevant step with dashed line

### Drawing Tools

**Selection and editing:**
- Click to select
- Double-click to edit text
- Drag corners to resize
- Drag edges to move

**Alignment:**
- Select multiple items (Ctrl+Click)
- Arrange → Align → choose alignment
- Use guidelines (View → Guides)

**Connectors:**
- Select connector tool from toolbar
- Click source, drag to destination
- Arrows auto-snap to connection points
- Right-click line → Format for dashed style

### Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Copy | Ctrl+C (Cmd+C) |
| Paste | Ctrl+V (Cmd+V) |
| Duplicate | Ctrl+D (Cmd+D) |
| Delete | Delete/Backspace |
| Group | Ctrl+G (Cmd+G) |
| Align | Ctrl+Shift+L/C/R |
| Undo | Ctrl+Z (Cmd+Z) |
| Redo | Ctrl+Y (Cmd+Shift+Z) |

## 🐛 Troubleshooting

### Diagram Won't Open in Draw.io
- Ensure the file has `.drawio` extension
- Check file isn't corrupted (compare with git history)
- Try opening in desktop app if online editor fails

### SVG Not Displaying in GitHub
- Verify SVG was exported correctly from draw.io
- Check file size (GitHub has limits, usually ~1MB)
- Open SVG in browser locally to test
- Ensure "Include a copy of my diagram" was checked during export

### Changes Not Showing in Export
- Make sure you saved the `.drawio` file first
- Re-export to SVG
- Check you're overwriting the correct file
- Hard refresh browser (Ctrl+F5) when testing

### Text Overflows Box
- Increase box size by dragging corners
- Or reduce font size (select text → Format panel)
- Or split into multiple lines

### Arrows Not Connecting
- Enable connection points (View → Connection Points)
- Look for blue X marks on shapes
- Drag arrow endpoints to these connection points

## 📋 Best Practices

1. **Make small, focused changes** - One logical update per PR
2. **Always export to SVG** - Keep both files in sync
3. **Test before committing** - Preview SVG in browser
4. **Write clear commit messages** - Use conventional commit format
5. **Coordinate major changes** - Discuss with team for structural modifications
6. **Keep backups** - Git protects you, but save interim work
7. **Update documentation** - If you change the process, update README too
8. **Use draw.io features** - Layers, grouping, and alignment tools

## 📐 Layout Guidelines

### Main Workflow (Center)
- X-position: ~670px (centered)
- Box width: 340px
- Box height: 70px (simple), 90-110px (complex)
- Vertical spacing: 30-50px between steps

### Side Panels
- Left notes: X-position 100-380
- Right panels: X-position 950-1270
- Box width: 280-320px

### Consistency is Key
- Align boxes horizontally in the same column
- Keep consistent spacing between steps
- Use the same icon sizes throughout
- Maintain color scheme for different element types

## 💬 Getting Help

- Check the [Editing Guide](EDITING.md) for detailed draw.io instructions
- Open an issue for questions about major changes
- Tag team members in PR comments for specific expertise
- Visit [draw.io documentation](https://www.drawio.com/doc/) for tool help

## 🔗 Useful Resources

- [Draw.io Online Editor](https://app.diagrams.net/)
- [Draw.io Desktop App](https://github.com/jgraph/drawio-desktop/releases)
- [Draw.io Documentation](https://www.drawio.com/doc/)
- [Draw.io Keyboard Shortcuts](https://www.drawio.com/shortcuts)
- [Git Workflow Guide](https://www.atlassian.com/git/tutorials/comparing-workflows)

## 📝 Commit Message Format

Use conventional commit format:

```
type: brief description

Examples:
- feat: add new validation step before deployment
- fix: correct arrow alignment in step 5
- docs: update command list in side panel
- style: adjust spacing between steps 7 and 8
- refactor: reorganize side panels for clarity
```

**Types:**
- `feat`: New feature or step added
- `fix`: Correction to existing content
- `docs`: Documentation updates
- `style`: Visual/layout changes
- `refactor`: Reorganization without content changes

---

**Questions?** Open an issue or reach out to the team lead. Check [EDITING.md](EDITING.md) for detailed editing instructions.
