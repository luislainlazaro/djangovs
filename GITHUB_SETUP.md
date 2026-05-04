# GitHub Setup & Merge Request Guide

## Local Git Setup Complete ✓

You have local Git branches ready for each development step:

```
feature/1-environment-setup      - Virtual environment & Django installation
feature/2-project-scaffolding    - Django project & login app creation
feature/3-authentication-config  - Views, URLs, and auth logic
feature/4-frontend-templates     - HTML templates with styling
feature/5-database-admin         - Migrations and admin setup
feature/6-documentation          - README and documentation
```

## Step 1: Create GitHub Repository

1. Go to [GitHub](https://github.com/new)
2. Create a new repository:
   - Repository name: `djangovs` (or your preferred name)
   - Description: "Django Login App - User authentication with registration"
   - Choose visibility (Public/Private)
   - **Do NOT** initialize with README (we already have one)
   - Click "Create repository"

3. Copy your repository URL (use HTTPS or SSH)

## Step 2: Configure Remote

Run this command with your repository URL:

```bash
cd /local/home/userdev_k22n/src/djangovs
git remote add origin https://github.com/YOUR_USERNAME/djangovs.git
```

Or with SSH:
```bash
git remote add origin git@github.com:YOUR_USERNAME/djangovs.git
```

Verify the remote is configured:
```bash
git remote -v
```

## Step 3: Push Master Branch

```bash
git branch -M master main
git push -u origin main
```

## Step 4: Push Feature Branches

Push all feature branches to GitHub:

```bash
git push origin feature/1-environment-setup
git push origin feature/2-project-scaffolding
git push origin feature/3-authentication-config
git push origin feature/4-frontend-templates
git push origin feature/5-database-admin
git push origin feature/6-documentation
```

Or push all at once:
```bash
git push origin --all
```

## Step 5: Create Merge Requests on GitHub

On GitHub, create Pull Requests for each branch:

### PR 1: Environment Setup
- **Title**: "Setup: Python virtual environment and Django installation"
- **Description**: 
  - Created virtual environment
  - Installed Django 6.0.4
  - Configured Python environment

### PR 2: Project Scaffolding
- **Title**: "Setup: Create Django project and login app"
- **Description**:
  - Created djangoproject (main project)
  - Created login app
  - Project structure initialized

### PR 3: Authentication Config
- **Title**: "Feature: Add authentication views and URL routing"
- **Description**:
  - Implemented login view with user authentication
  - Implemented register view with validation
  - Implemented logout functionality
  - Created protected home view
  - Set up URL routing for all endpoints

### PR 4: Frontend Templates
- **Title**: "UI: Create responsive login templates"
- **Description**:
  - Base template with gradient styling and message handling
  - Login template with form
  - Registration template with password confirmation
  - Home template for authenticated users
  - Modern responsive design

### PR 5: Database & Admin
- **Title**: "Setup: Configure database and create admin user"
- **Description**:
  - Ran Django migrations
  - Created superuser account
  - Database configured and initialized

### PR 6: Documentation
- **Title**: "Docs: Add comprehensive README and setup guide"
- **Description**:
  - Complete setup instructions
  - Feature documentation
  - URL routing reference
  - Troubleshooting guide
  - Security notes

## Creating PRs via Web Interface

For each branch:

1. Go to your repository on GitHub
2. Click "Pull requests" tab
3. Click "New pull request"
4. Select:
   - Base: `main`
   - Compare: `feature/X-name`
5. Add title and description
6. Click "Create pull request"

## Alternative: Using GitHub CLI

If you have [GitHub CLI](https://cli.github.com/) installed:

```bash
# Login to GitHub
gh auth login

# Create PR from current branch
git checkout feature/1-environment-setup
gh pr create --title "Setup: Python environment" --body "Created virtual environment and installed Django"

# Create PR with interactive mode
gh pr create --web
```

## Tips for Merge Requests

- **Use descriptive titles** - Start with action (Setup, Feature, Fix, Docs)
- **Reference issues** - Use "Closes #123" format
- **Include context** - Explain why changes were made
- **Link documentation** - Reference README sections
- **Test thoroughly** - Verify functionality before merging

## After Merge

Once PRs are merged to `main`:

```bash
git checkout main
git pull origin main
```

## Current Git Status

Check your current setup:
```bash
git remote -v          # View remotes
git branch -v          # View all branches
git log --oneline      # View commit history
```

## Need Help?

- [GitHub Docs: Creating PRs](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)
- [GitHub Docs: About branches](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches)
