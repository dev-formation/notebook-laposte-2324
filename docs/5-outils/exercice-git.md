---
sidebar_position: 4
---

# Git : Exercice

1. **Create a new repository**
    - Create a new repository on GitHub.
    - Copy the URL of the new repository.
    - Open your terminal and navigate to the directory where you want to clone your repository.
    - Run `git clone <URL>` to clone the repository to your local machine.
    - Run `cd <repository-name>` to navigate into your new repository.
    - Run `git status` to see the status of your repository.
    - Run `git log` to see the commit history of your repository.
    - Run `git remote -v` to see the remote repository.
    - Run `git branch` to see the branches in your repository.
    - Run `git checkout main` to switch to the main branch.
    - Run `code .` to open the repository in VS Code. (or open it by yourself)

2. **Create a new file and commit it to the main branch**

    - Create a new file named `index.html` and add some text to it.
    - Run `git add index.html` to stage the file for commit.
    - Run `git commit -m "Initial commit"` to commit the file to the main branch.

3. **Create a new branch**

    - Run `git branch newfeature` to create a new branch named `newfeature`.
    - Run `git checkout newfeature` to switch to the new branch.

4. **Make changes and commit them to the new branch**

    - Open `index.html`, make some changes, and save the file.
    - Run `git add index.html` and `git commit -m "Made changes in newfeature"` to commit the changes.

5. **Push the changes to the remote repository**

    - You can now push your changes with `git push -u origin newfeature`.

6. **Create a merge conflict**

    - Switch back to the main branch with `git checkout main`.
    - Make some changes to the same lines in `index.html` that you changed in `newfeature`.
    - Commit these changes with `git add index.html` and `git commit -m "Made conflicting changes in main"`.

7. **Merge the branches and resolve the conflict**
    - Try to merge `newfeature` into `main` with `git merge newfeature`. You should get a message about a merge conflict.
    - Open `index.html` and you'll see Git has marked the areas where there are conflicts.
    - Edit the file to resolve the conflicts, then save the file.
    - Stage the resolved file with `git add index.html`, and then commit the resolved changes with `git commit -m "Resolved merge conflict"`.

