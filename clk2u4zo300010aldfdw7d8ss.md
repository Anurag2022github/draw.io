---
title: "Understanding Git Fetch, Git Log, Git Revert, Git Reset, Git Merge, Git Rebase, and Git Cherry-pick with Examples"
seoDescription: "this is an advance concepts of Git with Git Fetch, Git Log, Git Revert, Git Reset, Git Merge, Git Rebase, and Git Cherry-pick"
datePublished: Fri Jul 14 2023 17:10:46 GMT+0000 (Coordinated Universal Time)
cuid: clk2u4zo300010aldfdw7d8ss
slug: understanding-git-fetch-git-log-git-revert-git-reset-git-merge-git-rebase-and-git-cherry-pick-with-examples
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689354285406/2553e57f-c84b-4163-9093-1cba4e0d5f37.png
tags: git, devops, devops-articles, 90daysofdevops, trainwithshubham

---

Introduction: Git is a powerful version control system widely used in software development to manage source code. It provides various commands and features that allow developers to handle different aspects of their codebase effectively. This technical blog aims to delve into some essential Git commands, namely Git fetch, Git log, Git revert, Git reset, Git merge, Git rebase, and Git cherry-pick, using easy-to-understand examples. By understanding these commands and their practical usage, you will gain a deeper insight into how Git manages code changes.

1. Git Fetch: Git fetch allows you to retrieve the latest changes from a remote repository without merging them into your local branch. Here's an example:
    
    Example: Fetching changes from a remote repository
    
    ```plaintext
    rubyCopy code$ git fetch origin
    ```
    
2. Git Log: Git log displays the commit history of a repository. It shows information such as commit messages, authors, timestamps, and the relationships between commits. Let's explore some examples:
    
    Example 1: Viewing the commit history
    
    ```plaintext
    shellCopy code$ git log
    ```
    
    Example 2: Filtering the commit history by author
    
    ```plaintext
    shellCopy code$ git log --author="John Doe"
    ```
    
    Example 3: Formatting the output of git log
    
    ```plaintext
    perlCopy code$ git log --pretty=format:"%h - %an, %ar : %s"
    ```
    
3. Git Revert: Git revert is used to undo a previous commit by creating a new commit that undoes the changes introduced in the original commit. Here are some examples:
    
    Example 1: Reverting a single commit
    
    ```plaintext
    phpCopy code$ git revert <commit-hash>
    ```
    
    Example 2: Reverting multiple commits
    
    ```plaintext
    phpCopy code$ git revert <commit-hash1> <commit-hash2> ...
    ```
    
4. Git Reset: Git reset allows you to move the current branch to a specific commit, effectively modifying the commit history. Here are some examples:
    
    Example 1: Soft reset (preserving changes in the working directory)
    
    ```plaintext
    cssCopy code$ git reset --soft <commit-hash>
    ```
    
    Example 2: Mixed reset (preserving changes in the working directory and index)
    
    ```plaintext
    cssCopy code$ git reset --mixed <commit-hash>
    ```
    
    Example 3: Hard reset (discarding all changes)
    
    ```plaintext
    cssCopy code$ git reset --hard <commit-hash>
    ```
    
5. Git Merge: Git merge is used to combine changes from different branches into the current branch. Let's explore some examples:
    
    Example 1: Basic merge operation
    
    ```plaintext
    phpCopy code$ git merge <branch-name>
    ```
    
    Example 2: Resolving merge conflicts
    
    ```plaintext
    rubyCopy code$ git merge <branch-name>
    # Resolve conflicts in the files
    $ git add <resolved-file>
    $ git merge --continue
    ```
    
6. Git Rebase: Git rebase is a command used to integrate changes from one branch onto another by moving or combining commits. Here are some examples:
    
    Example 1: Performing an interactive rebase
    
    ```plaintext
    cssCopy code$ git rebase -i <commit-hash>
    ```
    
    Example 2: Squashing commits during rebase
    
    ```plaintext
    cssCopy code$ git rebase -i HEAD~<number-of-commits>
    ```
    
7. Git Cherry-pick: Git cherry-pick is used to apply specific commits from one branch to another. Let's see some examples:
    
    Example 1: Cherry-picking a single commit
    
    ```plaintext
    phpCopy code$ git cherry-pick <commit-hash>
    ```
    
    Example 2: Cherry-picking multiple commits
    
    ```plaintext
    phpCopy code$ git cherry-pick <commit-hash1> <commit-hash2> ...
    ```
    

Conclusion: Git provides powerful commands like Git fetch, Git log, Git revert, Git reset, Git merge, Git rebase, and Git cherry-pick to manage code changes effectively. By using these commands with the help of the provided examples, you can handle different scenarios, including retrieving remote changes, viewing commit history, reverting commits, modifying commit history, merging branches, integrating changes, and applying specific commits. Understanding and utilizing these commands will empower you to maintain a clean and manageable codebase throughout your software development process.