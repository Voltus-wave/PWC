# Pull Request Creation Guide - Qmentis Repository

## Overview
This guide demonstrates how to create a pull request in the Qmentis repository with:
- **Base branch (main)**: `main` 
- **Head branch**: `new_branch` (found as `remotes/origin/new-branch`)

## Current Repository Analysis
- **Repository**: Currently in PWC repository (`github.com/Voltus-wave/PWC`)
- **Available branches**:
  - `main` (local)
  - `remotes/origin/main` (remote)
  - `remotes/origin/new-branch` (remote) ✅ **This matches your "new_branch"**

## Steps to Create Pull Request

### Method 1: Using GitHub CLI (Recommended)

1. **Authenticate with GitHub**:
```bash
gh auth login
```

2. **Switch to the head branch**:
```bash
git checkout -b new-branch origin/new-branch
```

3. **Create the Pull Request**:
```bash
gh pr create \
  --title "Pull Request: new-branch to main" \
  --body "Merging changes from new-branch into main branch" \
  --base main \
  --head new-branch
```

### Method 2: Using Git + Manual GitHub

1. **Fetch and checkout the branch**:
```bash
git fetch origin
git checkout -b new-branch origin/new-branch
```

2. **Push the branch (if needed)**:
```bash
git push origin new-branch
```

3. **Create PR via GitHub Web Interface**:
   - Go to the repository page on GitHub
   - Click "Compare & pull request" 
   - Set base: `main`, compare: `new-branch`
   - Add title and description
   - Click "Create pull request"

### Method 3: Using GitHub API

```bash
curl -X POST \
  -H "Authorization: token YOUR_GITHUB_TOKEN" \
  -H "Accept: application/vnd.github.v3+json" \
  https://api.github.com/repos/OWNER/REPO/pulls \
  -d '{
    "title": "Pull Request: new-branch to main",
    "head": "new-branch",
    "base": "main",
    "body": "Merging changes from new-branch into main"
  }'
```

## For Qmentis Repository Specifically

If you need to work with a different Qmentis repository:

1. **Add Qmentis as remote** (if it's a separate repository):
```bash
git remote add qmentis https://github.com/USERNAME/Qmentis.git
git fetch qmentis
```

2. **Create PR in Qmentis repository**:
```bash
gh pr create --repo USERNAME/Qmentis \
  --title "Pull Request: new-branch to main" \
  --body "Merging changes from new-branch into main branch" \
  --base main \
  --head new-branch
```

## Prerequisites Checklist

- ✅ GitHub CLI installed and configured
- ✅ Proper repository access permissions
- ✅ Branches exist: `main` and `new-branch`
- ✅ Changes are committed and pushed to `new-branch`

## Troubleshooting

**If branch doesn't exist:**
```bash
git checkout -b new-branch
# Make your changes
git add .
git commit -m "Your changes"
git push origin new-branch
```

**If repository access issues:**
- Check GitHub permissions
- Verify correct repository URL
- Ensure authentication is configured

## Next Steps

Once the PR is created:
1. Review the changes
2. Request reviewers if needed
3. Address any feedback
4. Merge when ready

---
*Generated for PWC repository analysis - adapt repository names and URLs as needed for actual Qmentis repository*