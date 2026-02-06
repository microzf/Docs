---
title: Visual Studio 2026 Code Version Control Methods
author: rick-anderson
description: Learn how to use version control features in Visual Studio 2026 for ASP.NET Core projects.
ms.author: riande
ms.date: 02/06/2026
uid: tutorials/vs-2026-version-control
---

# Visual Studio 2026 Code Version Control Methods

By [Rick Anderson](https://twitter.com/RickAndMSFT)

This tutorial demonstrates how to use version control features in Visual Studio 2026 to manage your ASP.NET Core projects. Visual Studio 2026 provides comprehensive Git integration and supports various source control providers.

## Prerequisites

* [Visual Studio 2026](https://visualstudio.microsoft.com/downloads/) with the ASP.NET and web development workload
* Basic understanding of Git concepts
* An ASP.NET Core project to work with

## Git Integration in Visual Studio 2026

Visual Studio 2026 includes built-in Git support, making it easy to manage your source code without leaving the IDE.

### Creating a Git Repository

1. Open your ASP.NET Core project in Visual Studio 2026.
2. Select **Git > Create Git Repository** from the menu bar.
3. In the **Create a Git Repository** dialog:
   * Choose to create a local repository only, or
   * Connect to a remote repository (GitHub, Azure DevOps, etc.)
4. Click **Create and Push** to initialize the repository.

### Git Changes Window

The Git Changes window is your central hub for version control operations:

1. Open the Git Changes window by selecting **View > Git Changes** or pressing **Ctrl+0, Ctrl+G**.
2. The window displays:
   * **Changes**: Modified, added, or deleted files
   * **Staged Changes**: Files ready to be committed
   * **Commit Message**: Area to describe your changes

### Committing Changes

To commit your changes:

1. Review the changed files in the **Git Changes** window.
2. Stage files by clicking the **+** icon next to each file, or stage all changes with **Stage All**.
3. Enter a descriptive commit message in the message box.
4. Click **Commit Staged** to commit your changes locally.
5. To commit and push in one action, click the dropdown next to **Commit Staged** and select **Commit All and Push**.

### Branching and Merging

Visual Studio 2026 makes branch management intuitive:

#### Creating a Branch

1. Open the **Git Repository** window (**View > Git Repository**).
2. Right-click on the branch you want to base your new branch on.
3. Select **New Local Branch From**.
4. Enter a branch name and click **Create**.

Alternatively, use the branch selector in the status bar:
1. Click the branch name in the lower-right corner of the window.
2. Select **New Branch**.
3. Enter the branch name and choose the base branch.

#### Switching Branches

1. Click the branch selector in the status bar, or
2. Open the **Git Repository** window and double-click the target branch.

#### Merging Branches

1. Switch to the branch you want to merge into (usually `main` or `master`).
2. Open the **Git Repository** window.
3. Right-click the branch you want to merge.
4. Select **Merge [branch-name] into Current Branch**.
5. Resolve any conflicts if they occur.

### Resolving Merge Conflicts

When conflicts occur during a merge:

1. Visual Studio 2026 displays the conflicted files in the **Git Changes** window.
2. Click on a conflicted file to open the **Merge Editor**.
3. The Merge Editor shows:
   * **Current** (your changes)
   * **Incoming** (changes from the other branch)
   * **Result** (the final merged version)
4. Choose which changes to keep:
   * Click **Take Current** to keep your changes
   * Click **Take Incoming** to accept the other branch's changes
   * Manually edit the **Result** pane for custom resolution
5. Click **Accept Merge** when done.
6. Stage and commit the resolved files.

### Pushing and Pulling Changes

#### Pushing to Remote Repository

1. After committing changes, click **Push** in the **Git Changes** window, or
2. Select **Git > Push** from the menu bar.

#### Pulling from Remote Repository

1. Click the **Pull** button in the Git Changes window, or
2. Select **Git > Pull** from the menu bar.
3. Visual Studio 2026 will fetch and merge changes from the remote repository.

#### Sync

The **Sync** option (Git > Sync) performs both pull and push operations in sequence.

## Team Explorer (Legacy)

While Git Changes is the recommended interface, Team Explorer is still available for those familiar with it:

1. Select **View > Team Explorer**.
2. The Home page provides quick access to:
   * Changes
   * Branches
   * Sync
   * Pull Requests

## GitHub Integration

Visual Studio 2026 provides seamless GitHub integration:

### Connecting to GitHub

1. Select **File > Account Settings**.
2. Click **Add** under **All Accounts**.
3. Select **GitHub** and sign in with your credentials.

### Cloning a GitHub Repository

1. Select **Git > Clone Repository**.
2. Enter the GitHub repository URL or browse your repositories.
3. Choose a local path and click **Clone**.

### Creating Pull Requests

1. Push your branch to GitHub.
2. Open the **Git Repository** window.
3. Right-click your branch and select **Create Pull Request**.
4. Visual Studio opens your browser to GitHub's pull request creation page.

## Azure DevOps Integration

Visual Studio 2026 also integrates with Azure DevOps:

### Connecting to Azure DevOps

1. Select **File > Account Settings**.
2. Add your Azure DevOps account.
3. Select **Team > Manage Connections > Connect to a Project**.
4. Choose your organization and project.

### Working with Azure Repos

1. Clone repositories using **Git > Clone Repository**.
2. Select **Azure DevOps** as the source.
3. Choose your organization, project, and repository.

## Best Practices for Version Control in Visual Studio 2026

### Commit Best Practices

* **Commit often**: Make small, logical commits rather than large, monolithic ones.
* **Write clear commit messages**: Start with a brief summary (50 characters or less), followed by a detailed description if needed.
* **Review changes before committing**: Use the diff viewer to ensure you're committing only intended changes.

### Branch Strategy

* **Use feature branches**: Create a new branch for each feature or bug fix.
* **Keep branches short-lived**: Merge feature branches back to the main branch frequently.
* **Name branches descriptively**: Use patterns like `feature/add-login` or `bugfix/fix-validation`.

### .gitignore Configuration

Visual Studio 2026 automatically creates a `.gitignore` file for ASP.NET Core projects. Verify it includes:

```gitignore
# Build results
[Dd]ebug/
[Dd]ebugPublic/
[Rr]elease/
[Rr]eleases/
bin/
obj/

# Visual Studio files
.vs/
*.suo
*.user
*.userosscache
*.sln.docstates

# NuGet packages
*.nupkg
**/packages/*
!**/packages/build/

# User-specific files
*.rsuser
```

### Code Reviews

* Use pull requests for code reviews before merging to the main branch.
* Enable branch protection rules in GitHub or Azure DevOps.
* Require at least one approval before merging.

## Advanced Features

### Stashing Changes

Visual Studio 2026 supports Git stash operations:

1. In the **Git Changes** window, click the **Stash** dropdown.
2. Select **Stash All** to save your current changes temporarily.
3. To apply stashed changes, click **Stash** and select **Apply Latest Stash**.

### Cherry-Picking Commits

1. Open the **Git Repository** window.
2. Navigate to the commit you want to cherry-pick.
3. Right-click the commit and select **Cherry-Pick**.

### Interactive Rebase

1. Open the **Git Repository** window.
2. Right-click on a commit and select **Rebase Current Branch onto**.
3. Choose the target commit or branch.
4. Use the interactive rebase window to squash, edit, or reorder commits.

### Git History and Blame

#### Viewing Git History

1. Right-click on a file in **Solution Explorer**.
2. Select **View History**.
3. The Git History window shows all commits affecting that file.

#### Using Blame

1. Right-click on a file in **Solution Explorer**.
2. Select **Git > View Blame**.
3. Each line shows who last modified it and when.

## Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Open Git Changes | Ctrl+0, Ctrl+G |
| Open Git Repository | Ctrl+0, Ctrl+R |
| Commit All | Ctrl+0, Ctrl+G, then Ctrl+Enter |
| Stage All Changes | Ctrl+0, Ctrl+G, then Ctrl+A |
| Push | Ctrl+0, Ctrl+G, then Ctrl+P |
| Pull | Ctrl+0, Ctrl+G, then Ctrl+L |

## Troubleshooting

### Authentication Issues

If you experience authentication issues:

1. Update your credentials in **File > Account Settings**.
2. For GitHub, consider using a Personal Access Token (PAT).
3. For Azure DevOps, ensure your account has proper permissions.

### Merge Conflict Resolution

If you're unsure how to resolve a conflict:

1. Use the **Merge Editor** to compare changes visually.
2. Consult with your team members who made the conflicting changes.
3. If needed, abort the merge and discuss the conflict resolution strategy.

### Performance Issues

For large repositories:

1. Enable **Git > Settings > Fetch on Open** to fetch changes only when needed.
2. Use **Sparse Checkout** to work with only specific directories.
3. Consider using **Git LFS** (Large File Storage) for large binary files.

## Additional Resources

* [Git Documentation](https://git-scm.com/doc)
* [GitHub Guides](https://guides.github.com/)
* [Azure DevOps Documentation](https://docs.microsoft.com/azure/devops/)
* [Visual Studio Git Documentation](https://docs.microsoft.com/visualstudio/version-control/)

## Next Steps

* Learn about [Continuous Integration with Azure DevOps](xref:azure/devops/cicd)
* Explore [Publishing to Azure](xref:tutorials/publish-to-azure-webapp-using-vs)
* Read about [ASP.NET Core DevOps best practices](xref:azure/devops/index)
