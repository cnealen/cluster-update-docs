# Quick Reference Card

Keep this handy for common tasks! 📋

## 🚀 Common Workflows

### Making a Simple Change

```bash
# 1. Update your local copy
git pull origin main

# 2. Create a branch
git checkout -b fix-typo-step5

# 3. Edit the SVG
vim docs/cluster_update_process.svg  # or your preferred editor

# 4. Preview in browser
open docs/cluster_update_process.svg

# 5. Commit and push
git add docs/cluster_update_process.svg
git commit -m "fix: correct typo in step 5 description"
git push origin fix-typo-step5

# 6. Create PR on GitHub
# Visit the repository and click "Compare & pull request"
```

### Updating Text Only

Find and replace text in the SVG:

```bash
# Search for the text
grep -n "Check Repository" docs/cluster_update_process.svg

# Edit with your preferred tool
# Text is usually in <text> elements like:
# <text x="670" y="110">Your Text Here</text>
```

### Adding a Warning Box

```xml
<!-- Copy this template and adjust coordinates -->
<rect x="100" y="YOUR_Y" width="280" height="70" rx="5" class="warning-box"/>
<use href="#warning-icon" x="110" y="YOUR_Y+15" width="20" height="20"/>
<text x="240" y="YOUR_Y+30" class="text" text-anchor="middle">⚠️ Warning</text>
<text x="240" y="YOUR_Y+50" class="text" text-anchor="middle">(Details)</text>
```

## 📝 Git Commands Cheat Sheet

```bash
# Check status
git status

# See what changed
git diff

# View commit history
git log --oneline -10

# Undo uncommitted changes
git checkout -- docs/cluster_update_process.svg

# Update from remote
git pull origin main

# Switch branches
git checkout branch-name

# Create and switch to new branch
git checkout -b new-branch-name

# Delete local branch
git branch -d branch-name

# View all branches
git branch -a

# Stash changes temporarily
git stash save "WIP: updating diagram"
git stash pop  # Restore changes
```

## 🎨 SVG Quick Edits

### Change Text
```xml
<!-- Find this -->
<text x="670" y="110">Old Text</text>

<!-- Change to -->
<text x="670" y="110">New Text</text>
```

### Move Element Down
```xml
<!-- Original at y=500 -->
<rect x="500" y="500" .../>

<!-- Move 50 units down to y=550 -->
<rect x="500" y="550" .../>
```

### Change Box Color
```xml
<!-- Blue process box -->
<rect ... class="process-box"/>

<!-- Change to green action box -->
<rect ... class="action-box"/>

<!-- Or to orange decision -->
<rect ... class="decision-box"/>

<!-- Or to red warning -->
<rect ... class="warning-box"/>
```

### Add Icon to Step
```xml
<!-- Add after <rect> for a step -->
<use href="#docker-icon" x="510" y="YOUR_Y+15" width="24" height="18"/>

<!-- Available icons: -->
<!-- docker-icon, gitlab-icon, terminal-icon, singularity-icon -->
<!-- tar-icon, sif-icon, workflow-icon, storage-icon -->
<!-- registry-icon, warning-icon, success-icon, clean-icon -->
```

## 🔍 Finding Things in the SVG

```bash
# Find specific text
grep -n "Repository Updates" docs/cluster_update_process.svg

# Find all process boxes
grep -n 'class="process-box"' docs/cluster_update_process.svg

# Find all arrows
grep -n 'class="arrow"' docs/cluster_update_process.svg

# Count steps
grep -c '<rect' docs/cluster_update_process.svg
```

## ✅ Pre-Commit Checklist

- [ ] File syntax is valid (test with `xmllint --noout file.svg`)
- [ ] Opens in browser without errors
- [ ] Text is readable (not too small or overlapping)
- [ ] Changes are within SVG canvas bounds
- [ ] Commit message follows format
- [ ] Tested locally before pushing

## 🧪 Testing Your Changes

```bash
# Validate XML syntax
xmllint --noout docs/cluster_update_process.svg

# View in browser (macOS)
open docs/cluster_update_process.svg

# View in browser (Linux)
xdg-open docs/cluster_update_process.svg

# View in browser (Windows)
start docs/cluster_update_process.svg

# Get file info
file docs/cluster_update_process.svg
ls -lh docs/cluster_update_process.svg
```

## 📐 Coordinate Quick Reference

```
Canvas: 1400 x 1850 pixels

Main Workflow Column:
- X position: 500-840 (center at 670)
- Box width: 340
- Standard height: 70 (simple) or 90-110 (complex)

Vertical Spacing:
- Between steps: 100 units
- Text lines: 20 units apart

Text Positioning:
- Center main steps at x=670
- Left notes at x=240
- Right panels at x=1110
```

## 🆘 Emergency Fixes

### Broke the SVG and it won't display?

```bash
# Revert your changes
git checkout HEAD -- docs/cluster_update_process.svg

# Or restore from specific commit
git checkout COMMIT_HASH -- docs/cluster_update_process.svg
```

### Accidentally committed to main?

```bash
# Undo last commit (keeps changes)
git reset --soft HEAD~1

# Create proper branch
git checkout -b my-fix-branch
git commit -m "fix: your actual fix"
```

### Need to update PR after review?

```bash
# Make your changes
# Then amend the last commit
git add docs/cluster_update_process.svg
git commit --amend --no-edit

# Force push (updates PR)
git push origin your-branch-name --force
```

## 📞 Getting Help

1. **Check CONTRIBUTING.md** - Full collaboration guide
2. **Check docs/EDITING.md** - Detailed editing reference
3. **Open an issue** - For questions or problems
4. **Ask team lead** - For process questions

## 🔗 Useful Links

- Repository: `https://github.com/YOUR_USERNAME/cluster-update-docs`
- Issues: `https://github.com/YOUR_USERNAME/cluster-update-docs/issues`
- Pull Requests: `https://github.com/YOUR_USERNAME/cluster-update-docs/pulls`

## 💡 Pro Tips

- Always pull before starting work: `git pull origin main`
- Use descriptive branch names: `fix-arrow-step7` not `fix`
- Commit often with small, logical changes
- Test in browser before pushing
- Use the PR template - it helps reviewers
- Ask questions early rather than guessing

---

**Print this page** and keep it at your desk! 🖨️

**Bookmark in your browser** for quick access! 🔖
