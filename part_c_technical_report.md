# C) Technical Report

## GitHub Repository Setup and Version Control

### Introduction

Git and GitHub are commonly used tools for managing software projects. Git provides version control, while GitHub provides remote storage and collaboration features.

The purpose of this exercise was to create a GitHub repository, connect it to a local project, create an initial commit, and upload the project files to GitHub.

### Implementation

The project was first organized in a local folder on the computer. Git was initialized in the project folder using the `git init` command.

The project files were then added to the staging area using:

```bash
git add .
```

After staging the files, an initial commit was created using:

```bash
git commit -m "Initial commit"
```

The local repository was then connected to the GitHub repository using a remote repository URL. The main branch was selected using:

```bash
git branch -M main
```

Finally, the project was uploaded to GitHub using:

```bash
git push -u origin main
```

### Results

The project files were successfully uploaded to the GitHub repository. The repository contained the project files and the initial commit.

The process demonstrated how Git can be used to create a history of changes while GitHub provides a remote location for storing and sharing the project.

### Technical Benefits

Using Git and GitHub provides several benefits:

1. **Version tracking:** Changes to project files can be recorded through commits.
2. **Remote storage:** Project files can be stored remotely on GitHub.
3. **Collaboration:** Developers can work together on the same project.
4. **Project history:** Previous commits provide a record of changes.
5. **Backup:** A remote repository provides an additional copy of the project.

### Challenges and Solutions

One common challenge for beginners is receiving an error that Git is not recognized as a command. This usually means Git is not installed correctly or its location has not been added to the system PATH.

Another possible problem is using the wrong GitHub repository URL. Checking the repository URL carefully before running the `git remote add origin` command helps prevent this problem.

### Conclusion

The exercise demonstrated the basic process of using Git and GitHub for version control. The project was initialized locally, committed to Git, connected to a remote GitHub repository, and pushed successfully.

This workflow provides a foundation for managing future software projects and maintaining a clear history of project changes.