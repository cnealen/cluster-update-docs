# Quick Setup Guide

Get your diagram repository up and running in 5 minutes!

## 1️⃣ Create GitHub Repository

### Option A: Using GitHub Web Interface

1. Go to https://github.com/new
2. Repository name: `cluster-update-docs` (or your choice)
3. Description: "Development cluster update process documentation"
4. Choose visibility: **Private** (recommended for internal docs) or Public
5. **Do NOT initialize** with README, .gitignore, or license
6. Click "Create repository"

### Option B: Using GitHub CLI

```bash
gh repo create cluster-update-docs --private --description "Development cluster update process documentation"
```

## 2️⃣ Initialize Local Repository

```bash
# Navigate to the setup folder you downloaded
cd github-diagram-setup

# Initialize git
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit: Add cluster update process diagram and documentation"

# Add remote (replace YOUR_USERNAME with your GitHub username)
git remote add origin https://github.com/YOUR_USERNAME/cluster-update-docs.git

# Push to GitHub
git branch -M main
git push -u origin main
```

## 3️⃣ Verify Setup

1. **Visit your repository** on GitHub
2. **Check the diagram displays** - Navigate to `docs/cluster_update_process.svg` and verify it renders
3. **Review README** - Main page should show the diagram and documentation

## 4️⃣ Invite Collaborators

### Give Team Members Access

1. Go to your repository on GitHub
2. Click **Settings** → **Collaborators**
3. Click **Add people**
4. Enter team members' GitHub usernames or emails
5. Choose permission level:
   - **Write** - Can push changes directly
   - **Maintain** - Write + some admin capabilities
   - **Admin** - Full control

### Set Up Branch Protection (Optional but Recommended)

1. **Settings** → **Branches** → **Add branch protection rule**
2. Branch name pattern: `main`
3. Enable:
   - ✅ Require pull request reviews before merging
   - ✅ Require approvals: 1
   - ✅ Dismiss stale pull request approvals when new commits are pushed
4. Save changes

## 5️⃣ Share with Team

Send this message to your team:

```
📊 Cluster Update Documentation Now on GitHub!

Repository: https://github.com/YOUR_USERNAME/cluster-update-docs

Quick Start:
1. Clone: git clone https://github.com/YOUR_USERNAME/cluster-update-docs.git
2. Read CONTRIBUTING.md for how to make changes
3. Check docs/CHECKLIST.md when performing updates

View the diagram: https://github.com/YOUR_USERNAME/cluster-update-docs/blob/main/docs/cluster_update_process.svg

Questions? See CONTRIBUTING.md or open an issue!
```

## 📋 Team Member Quick Start

For team members who want to contribute:

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/cluster-update-docs.git
cd cluster-update-docs

# Create a branch for your changes
git checkout -b update-diagram-description

# Make your changes to docs/cluster_update_process.svg
# (Use any text editor)

# Preview changes (open in browser)
open docs/cluster_update_process.svg  # macOS
xdg-open docs/cluster_update_process.svg  # Linux
start docs/cluster_update_process.svg  # Windows

# Commit and push
git add docs/cluster_update_process.svg
git commit -m "Update step 5 description"
git push origin update-diagram-description

# Create pull request on GitHub
# Go to repository page and click "Compare & pull request"
```

## 🔧 Customization Options

### Update Repository Name in Files

If you used a different repository name, update these references:

1. **README.md** - Update any hardcoded URLs
2. **CONTRIBUTING.md** - Update clone command examples
3. **This file** - Update examples

### Add Team-Specific Information

Consider adding:
- **CONTACTS.md** - Team contact info and escalation paths
- **FAQ.md** - Common questions about the cluster
- **TROUBLESHOOTING.md** - Detailed troubleshooting guide
- **CHANGELOG.md** - Track major changes to the process

### Set Up GitHub Actions (Advanced)

Automate SVG validation:

```yaml
# .github/workflows/validate-svg.yml
name: Validate SVG
on: [pull_request]
jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Validate SVG
        run: |
          sudo apt-get install -y libxml2-utils
          xmllint --noout docs/cluster_update_process.svg
```

## ⚙️ Advanced Configuration

### Enable GitHub Pages (Optional)

Host documentation as a website:

1. **Settings** → **Pages**
2. Source: Deploy from a branch
3. Branch: `main`, folder: `/ (root)`
4. Save
5. Your site will be at: `https://YOUR_USERNAME.github.io/cluster-update-docs/`

### Configure Notifications

1. **Watch** → **Custom**
2. Select:
   - ✅ Issues
   - ✅ Pull requests
   - ✅ Releases (if you create them)

### Add Repository Topics

1. Click gear icon next to "About"
2. Add topics: `documentation`, `cluster-management`, `devops`, `docker`, `kubernetes`

## 🎓 Resources

- [GitHub Docs - Quickstart](https://docs.github.com/en/get-started/quickstart)
- [Git Basics](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics)
- [Markdown Guide](https://www.markdownguide.org/)
- [SVG Tutorial](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial)

## ❓ Troubleshooting

### "Remote origin already exists"
```bash
git remote remove origin
git remote add origin https://github.com/YOUR_USERNAME/cluster-update-docs.git
```

### "Permission denied"
- Check you're logged into correct GitHub account
- Verify you have write access to the repository
- Try SSH instead of HTTPS:
  ```bash
  git remote set-url origin git@github.com:YOUR_USERNAME/cluster-update-docs.git
  ```

### "SVG not displaying on GitHub"
- Verify file is valid XML: `xmllint --noout docs/cluster_update_process.svg`
- Check file size (GitHub has limits)
- Ensure file is in `docs/` directory

### "Can't see changes after push"
- Hard refresh: Ctrl+F5 (Windows/Linux) or Cmd+Shift+R (Mac)
- Clear browser cache
- Check you're viewing the correct branch

## 🎉 Next Steps

1. ✅ Repository created and pushed
2. ✅ Team members invited
3. 📖 Everyone reads CONTRIBUTING.md
4. 🔄 Start using the workflow!

---

**Questions?** Open an issue in the repository or consult your team lead.
