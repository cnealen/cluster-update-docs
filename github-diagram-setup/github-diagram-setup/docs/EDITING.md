# SVG Diagram Editing Guide

This guide provides technical details for editing the cluster update process diagram.

## 📐 Diagram Structure

### Canvas Dimensions
```xml
<svg width="1400" height="1850" xmlns="http://www.w3.org/2000/svg">
```
- **Width:** 1400px
- **Height:** 1850px
- Adjust if adding content that extends beyond these bounds

### Color Scheme

The diagram uses consistent color classes defined in the `<defs><style>` section:

| Class | Fill Color | Stroke Color | Use Case |
|-------|-----------|--------------|----------|
| `process-box` | #E8F4F8 (Light Blue) | #2E86AB (Blue) | General process steps |
| `decision-box` | #FFF3E0 (Light Orange) | #FF9800 (Orange) | Decision points |
| `action-box` | #E8F5E9 (Light Green) | #4CAF50 (Green) | Actionable tasks |
| `warning-box` | #FFEBEE (Light Red) | #F44336 (Red) | Warnings/cautions |

### Icon System

Custom icons are defined in the `<defs>` section and referenced using `<use>`:

```xml
<!-- Definition (in <defs>) -->
<g id="docker-icon">
  <!-- icon paths -->
</g>

<!-- Usage (in diagram) -->
<use href="#docker-icon" x="510" y="775" width="24" height="18"/>
```

Available icons:
- `gitlab-icon` - GitLab logo
- `docker-icon` - Docker logo
- `terminal-icon` - Command line
- `singularity-icon` - Singularity container
- `tar-icon` - TAR archive
- `sif-icon` - SIF file
- `workflow-icon` - Workflow UI
- `storage-icon` - Storage system
- `registry-icon` - Package registry
- `user-check-icon` - User verification
- `clean-icon` - Cleanup action
- `warning-icon` - Warning symbol
- `success-icon` - Success checkmark

## ✏️ Common Editing Tasks

### 1. Modify Step Text

**Location:** Main workflow steps (y: 80-1550)

```xml
<!-- Find the text element -->
<text x="670" y="110" class="text" text-anchor="middle">1. Check Repository Updates</text>

<!-- Modify the content -->
<text x="670" y="110" class="text" text-anchor="middle">1. Verify Repository Updates</text>
```

**Tips:**
- Keep text concise (35 characters or less per line)
- Use `text-anchor="middle"` for centered text
- Standard x-position for main workflow: `x="670"`

### 2. Add a New Process Step

**Template:**
```xml
<!-- Box -->
<rect x="500" y="[Y_POSITION]" width="340" height="70" rx="5" class="process-box"/>

<!-- Optional: Add icon -->
<use href="#[ICON_NAME]" x="510" y="[Y_POSITION + 15]" width="24" height="24"/>

<!-- Title text -->
<text x="670" y="[Y_POSITION + 30]" class="text" text-anchor="middle">Step Title</text>

<!-- Subtitle text (optional) -->
<text x="670" y="[Y_POSITION + 50]" class="text" text-anchor="middle">(Details)</text>

<!-- Arrow to next step -->
<path d="M 670 [Y_POSITION + 70] L 670 [NEXT_Y_POSITION]" class="arrow"/>
```

**Spacing Guidelines:**
- Main steps: 100 units apart
- With expanded content: 120-150 units apart
- Decision diamonds need ~80 units vertical space

### 3. Create a Decision Diamond

```xml
<!-- Diamond shape (100x80 units) -->
<path d="M 670 [Y] L 770 [Y+40] L 670 [Y+80] L 570 [Y+40] Z" class="decision-box"/>

<!-- Icon (optional) -->
<use href="#workflow-icon" x="658" y="[Y+15]" width="24" height="20"/>

<!-- Question text -->
<text x="670" y="[Y+35]" class="text" text-anchor="middle">Question Line 1</text>
<text x="670" y="[Y+50]" class="text" text-anchor="middle">Question Line 2?</text>

<!-- "Yes" path (downward) -->
<path d="M 670 [Y+80] L 670 [Y+120]" class="arrow"/>

<!-- "No" path (leftward) -->
<path d="M 570 [Y+40] L 400 [Y+40]" class="arrow"/>
```

### 4. Add Side Notes/Warnings

```xml
<!-- Warning box on left side -->
<rect x="100" y="[Y]" width="280" height="70" rx="5" class="warning-box"/>
<use href="#warning-icon" x="110" y="[Y+15]" width="20" height="20"/>
<text x="240" y="[Y+30]" class="text" text-anchor="middle">⚠️ Warning Title</text>
<text x="240" y="[Y+50]" class="text" text-anchor="middle">(Additional context)</text>

<!-- Dashed arrow pointing to relevant step -->
<path d="M 380 [Y+35] L 500 [TARGET_Y]" class="dashed-arrow"/>
```

### 5. Update Commands in Side Panel

**Location:** Key Commands box (x: 950, y: 500)

```xml
<!-- Find the commands list -->
<text x="10" y="50" class="text" font-family="monospace" font-size="12">git fetch origin</text>
<text x="10" y="70" class="text" font-family="monospace" font-size="12">docker images</text>

<!-- Add new command (increase y by 20 for each line) -->
<text x="10" y="230" class="text" font-family="monospace" font-size="12">your new command</text>
```

**Note:** If adding many commands, increase the box height:
```xml
<rect x="0" y="0" width="320" height="[NEW_HEIGHT]" .../>
```

### 6. Modify Important Notes

**Location:** Important Notes box (x: 950, y: 760)

```xml
<!-- Each note is 20 units apart -->
<text x="10" y="50" class="text" font-size="12">• Your note here</text>
<text x="10" y="70" class="text" font-size="12">• Another note</text>
```

## 🎨 Advanced Techniques

### Creating Custom Icons

1. **Define in `<defs>` section:**
```xml
<g id="my-custom-icon">
  <circle cx="12" cy="12" r="10" fill="#4CAF50"/>
  <path d="M 8 12 L 11 15 L 16 9" stroke="white" stroke-width="2"/>
</g>
```

2. **Use in diagram:**
```xml
<use href="#my-custom-icon" x="100" y="100" width="24" height="24"/>
```

### Curved Arrows

For non-straight connections:
```xml
<!-- Curved path using quadratic Bezier curve -->
<path d="M 670 150 Q 700 180 670 210" class="arrow"/>
<!-- Format: M startX startY Q controlX controlY endX endY -->
```

### Multi-line Text with Bullets

```xml
<text x="670" y="930" class="text" text-anchor="middle">• First point</text>
<text x="670" y="950" class="text" text-anchor="middle">• Second point</text>
<text x="670" y="970" class="text" text-anchor="middle">• Third point</text>
```

### Highlighting Changes

Use bold or colored text for emphasis:
```xml
<!-- Bold text -->
<text x="670" y="110" class="text" font-weight="bold">Important Step</text>

<!-- Red text (for emphasis) -->
<text x="670" y="110" class="text" fill="#F44336">Critical Warning</text>
```

## 🔧 Layout Coordinates

### Main Workflow (Center Column)
- **X-position:** 500-840 (centered at 670)
- **Box width:** 340 units
- **Box height:** 70 units (simple), 90-110 units (complex)
- **Vertical spacing:** 100 units between boxes

### Left Side Notes
- **X-range:** 100-380
- **Box width:** 160-280 units

### Right Side Panels
- **X-position:** 950
- **Box width:** 320 units
- **Spacing between boxes:** 20 units

### Decision Diamonds
- **Width:** 200 units (100 left/right from center)
- **Height:** 80 units
- **Formula:** `M centerX Y L rightX midY L centerX bottomY L leftX midY Z`

## 📊 Positioning Cheat Sheet

```
Main Box:        x=500  width=340   (centered at x=670)
Left Notes:      x=100  width=280   (centered at x=240)
Right Panels:    x=950  width=320   (centered at x=1110)

Standard Heights:
- Simple step:   70 units
- Complex step:  90-110 units
- Decision:      80 units
- Warning:       70 units

Vertical Gaps:
- Step to step:  30 units
- Before decision: 40 units
```

## 🧪 Testing Your Changes

### Quick Validation

1. **Syntax check:**
   ```bash
   xmllint --noout docs/cluster_update_process.svg
   ```

2. **Browser preview:**
   - Open the SVG file directly in Chrome/Firefox
   - Look for rendering issues

3. **GitHub preview:**
   - Push to a test branch
   - View on GitHub to ensure it renders correctly

### Common Issues

| Problem | Cause | Solution |
|---------|-------|----------|
| Text cut off | Outside SVG bounds | Increase `<svg height="">` |
| Icon not showing | Wrong `href` reference | Check icon ID in `<defs>` |
| Arrow misaligned | Incorrect coordinates | Recalculate start/end points |
| Text overlapping | Y-positions too close | Increase spacing by 20+ units |

## 📦 Version Control Best Practices

### Commit Message Format

```
type: brief description

Detailed explanation of what changed and why

Examples:
- fix: correct step 5 arrow alignment
- feat: add new validation step before deployment
- docs: update command list in side panel
- style: adjust spacing between steps 7 and 8
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

- [SVG Path Syntax](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Paths)
- [SVG Text Documentation](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/text)
- [Color Picker Tool](https://htmlcolorcodes.com/)
- [SVG Editor (for visual editing)](https://boxy-svg.com/)

---

**Need more help?** Check the [CONTRIBUTING.md](../CONTRIBUTING.md) for workflow guidance.
