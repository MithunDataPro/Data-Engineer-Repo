# Version Control Systems (VCS)
**Version Control Systems (VCS)** are essential tools for managing changes to projects, particularly in software development. Below is an overview of popular version control systems, including centralized and distributed systems.

### Table of Contents
1. Git
2. GitLab
3. Azure DevOps
4. Visual Studio
5. Subversion (SVN)
6. Mercurial
7. Perforce (Helix Core)
8. Bazaar
9. ClearCase
10. TFS (Team Foundation Server)
11. CVS (Concurrent Versions System)
12. VSS (Visual SourceSafe)
13. Plastic SCM

---

## 1. Git
**Git** is a distributed version control system, known for its speed and flexibility. Each user has a full copy of the project’s history, allowing for offline work and easy collaboration.

- **Key Features:**

- Distributed: Every user has the entire repository.
- Powerful branching and merging.
- Offline capabilities.
- Used by platforms like GitHub, GitLab, Bitbucket.
  
- **Common Commands:**
  ```bash
  git init    # Initialize a new Git repository
  git clone   # Clone an existing repository
  git add     # Stage changes for commit
  git commit  # Commit staged changes
  git push    # Push changes to a remote repository
  git pull    # Fetch and merge changes from a remote repository

``
---

## 2. GitLab
**GitLab** is a web-based **DevOps** lifecycle tool that provides Git repository management, issue tracking, **continuous integration (CI)**, and **deployment pipelines (CD)**. It uses **Git** as its underlying version control system.

- **Key Features:**

- Git-based repository management.
- Integrated CI/CD pipelines.
- Issue tracking and project management.
- Role-based access control (RBAC).
  
- **Common Commands (similar to Git):**
  ```bash
  git clone https://gitlab.com/your-repo.git  # Clone repository from GitLab
  git push origin master  # Push changes to GitLab

``

---

## 3. Azure DevOps
**Azure DevOps** (previously known as TFS or VSTS) is a cloud-based service that provides tools for version control, build automation, continuous delivery, and more. It supports Git and its own version control system, TFVC (Team Foundation Version Control).

- **Key Features:**

- Supports Git and TFVC.
- Built-in CI/CD tools.
- Agile planning (Scrum, Kanban).
- Integration with Visual Studio.

- **Common Commands for Git:**
  ```bash
  git clone https://dev.azure.com/your-project  # Clone repository from Azure DevOps
  git push origin main  # Push changes to Azure DevOps

``

---

## 4. Visual Studio
**Visual Studio** integrates version control directly within the development environment. It supports Git repositories and can connect to services like GitHub, GitLab, and Azure DevOps. Visual Studio also integrates with TFVC (Team Foundation Version Control).

- **Key Features:**

- Built-in Git support.
- Integration with Azure DevOps.
- Visual interface for version control actions.
- Supports branching, merging, and pull requests.

- **Common Git Commands in Visual Studio:**
- Clone a repository using the built-in Git interface.
- Stage, commit, push, and pull changes directly from the IDE.

---

## 5. Subversion (SVN)
**Subversion (SVN)** is a centralized version control system. All files and their history are stored in a central repository, and developers must connect to this central server to commit changes.

- **Key Features:**

- Centralized repository.
- Atomic commits and revision tracking.
- Good support for binary files.

- **Common Commands:**
  ```bash
  svn checkout https://your-svn-repo  # Check out working copy
  svn commit  # Commit changes to the repository
  svn update  # Update working copy with repository changes

``
---

## 6. Mercurial
**Mercurial** is a distributed version control system focused on simplicity and performance, often used in large projects.

- **Key Features:**

- Distributed system: Full history on each developer’s machine.
- Fast and lightweight.
- Cross-platform support.

- **Common Commands:**
  ```bash
  hg init  # Initialize a new repository
  hg clone https://your-repo  # Clone a repository
  hg commit  # Commit changes to the repository
  hg push  # Push changes to a remote repository

``
---

## 7. Perforce (Helix Core)
**Perforce (Helix Core)** is a centralized version control system, often used for large-scale projects like game development. It’s known for handling large binary files efficiently.

- **Key Features:**

- Centralized system with support for large binary files.
- Strong branching and merging capabilities.
- Role-based access control.

- **Common Commands:**
  ```bash
  p4 checkout  # Check out files for editing
  p4 submit  # Submit changes to the repository
  p4 sync  # Synchronize workspace with repository

``

---
