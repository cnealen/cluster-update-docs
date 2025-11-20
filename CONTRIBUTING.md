# Contributing to the Cluster Update Diagram

Thank you for helping maintain our documentation! This guide will help you collaborate on the diagram.

## 🚀 Quick Start

### Prerequisites
- Git installed on your machine
- Text editor (VS Code, Sublime Text, etc.)
- Basic understanding of SVG/XML (optional but helpful)

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

## 📝 Making Changes

### For Simple Text Updates

The SVG file is text-based and can be edited directly. Most text elements are near the bottom of the file.

1. **Open the diagram**
   ```bash
   # Open in your preferred editor
   code docs/cluster_update_process.svg
   # or
   vim docs/cluster_update_process.svg
   ```

2. **Find the text you want to change**
   - Search for the text content (e.g., "Check Repository Updates")
   - Text elements look like: `<text x="670" y="110" class="text">Your Text Here</text>`

3. **Edit carefully**
   - Keep the XML structure intact
   - Don't modify `x`, `y`, or `class` attributes unless you know what you're doing
   - Only change the text between `<text>` and `</text>` tags

### For Structural Changes

If you need to add/remove steps or modify the flow:

1. **Understand the structure**
   - Boxes are `<rect>` elements with classes like `process-box`, `action-box`, `decision-box`
   - Arrows are `<path>` elements with the `arrow` class
   - Text is in `<text>` elements

2. **Use existing patterns**
   - Copy a similar element and modify its properties
   - Maintain consistent spacing (usually 100 units between major steps)
   - Keep the same styling classes for consistency

3. **Test your changes**
   - Open the SVG in a web browser to preview
   - Verify nothing is cut off or overlapping

## 🔍 Review Process

### Before Committing

**Checklist:**
- [ ] SVG file is valid XML (no syntax errors)
- [ ] File opens correctly in a browser
- [ ] All text is readable and properly positioned
- [ ] Changes align with the actual cluster update process
- [ ] Commit message clearly describes the change

### Commit Your Changes

```bash
# Stage your changes
git add docs/cluster_update_process.svg

# Commit with a descriptive message
git commit -m "Update step 5 to reflect new Docker cleanup procedure"

# Push to your branch
git push origin update-diagram-<your-change>
```

### Create a Pull Request

1. Go to the repository on GitHub
2. Click "Pull Requests" → "New Pull Request"
3. Select your branch
4. Fill in the PR description:
   - What changed?
   - Why did it change?
   - Any special considerations?

5. Request review from team members
6. Address any feedback
7. Once approved, merge to main

## 🎨 Editing Tips

### Common Tasks

**Adding a new step:**
```xml
<!-- Copy this template and adjust x, y coordinates -->
<rect x="500" y="280" width="340" height="70" rx="5" class="action-box"/>
<text x="670" y="310" class="text" text-anchor="middle">Your Step Title</text>
<text x="670" y="330" class="text" text-anchor="middle">(Additional details)</text>

<!-- Add an arrow to/from it -->
<path d="M 670 250 L 670 280" class="arrow"/>
```

**Updating text:**
```xml
<!-- Find the line -->
<text x="670" y="110" class="text">1. Check Repository Updates</text>

<!-- Change to -->
<text x="670" y="110" class="text">1. Verify Repository Updates</text>
```

**Adding a warning note:**
```xml
<rect x="100" y="500" width="280" height="70" rx="5" class="warning-box"/>
<text x="240" y="530" class="text" text-anchor="middle">⚠️ Your Warning Here</text>
<text x="240" y="550" class="text" text-anchor="middle">(Additional context)</text>
```

### Coordinate System

- Origin (0,0) is top-left
- X increases going right
- Y increases going down
- Main workflow is centered around x="670"
- Steps are typically 100-120 units apart vertically

### Style Classes

- `process-box` - Blue boxes for general steps
- `action-box` - Green boxes for actions
- `decision-box` - Orange diamond for decisions
- `warning-box` - Red boxes for warnings/cautions
- `text` - Standard text styling
- `arrow` - Solid arrows for main flow
- `dashed-arrow` - Dashed arrows for notes/references

## 🐛 Troubleshooting

### SVG Won't Display in GitHub
- Check for XML syntax errors (missing closing tags, quotes, etc.)
- Ensure file encoding is UTF-8
- Validate with an XML validator

### Text is Cut Off
- Increase the SVG canvas size at the top: `<svg width="1400" height="1850">`
- Adjust the element's Y position to fit within canvas

### Changes Not Showing
- Hard refresh your browser (Ctrl+F5 or Cmd+Shift+R)
- Clear browser cache
- Check if you're viewing the correct branch

## 📋 Best Practices

1. **Make small, focused changes** - One logical update per PR
2. **Test before committing** - Always preview the SVG
3. **Write clear commit messages** - Future you will thank you
4. **Coordinate major changes** - Discuss with team for structural modifications
5. **Keep backups** - Git will save you, but better safe than sorry
6. **Update documentation** - If you change the process, update README too

## 💬 Getting Help

- Open an issue for major changes or questions
- Tag team members in PR comments for specific expertise
- Check the [Editing Guide](docs/EDITING.md) for more details

## 🔗 Useful Resources

- [SVG Tutorial](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial)
- [Git Workflow Guide](https://www.atlassian.com/git/tutorials/comparing-workflows)
- [Markdown Guide](https://www.markdownguide.org/)

---

**Questions?** Open an issue or reach out to the team lead.
