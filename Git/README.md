# Git-Cheatsheet

## Commit convention

| Type          | When to use it                                                                    |
| ------------- | --------------------------------------------------------------------------------- |
| **feat:**     | Introducing a new feature                                                         |
| **fix:**      | A bug fix                                                                         |
| **docs:**     | Documentation only changes                                                        |
| **style:**    | Formatting, missing semicolons, whitespace, etc.                                  |
| **refactor:** | Code changes that neither fixes a bug nor adds a feature (e.g. restructuring)     |
| **perf:**     | A code change that improves performance                                           |
| **test:**     | Adding missing tests or correcting existing ones                                  |
| **build:**    | Changes that affect the build system or external dependencies (e.g. webpack, npm) |
| **ci:**       | CI configuration files and scripts (e.g. GitHub Actions, Travis)                  |
| **chore:**    | Other changes that don’t modify src or test files (e.g. repo cleanup, tooling)    |
| **revert:**   | Reverts a previous commit                                                         |

## Squashing commits
1. Check your commit history
```
git log --oneline
```

2. Find the merge base
```
git merge-base main HEAD
```
This gives you the commit hash where your branch split from `main`.

3. Rebase interactively from that commit
```
git rebase -i $(git merge-base main HEAD)
```

4. PR and Merge

Best Practice:
If your branch is clean after a squash, merge your PR right away to finalize the work.
Treat this as a checkpoint before continuing further development.

### Group and sqash accordingly
Before
```
pick c12 Fix typo in auth
pick c11 Add JWT helper
pick c10 Handle expired token
pick c9  Docker volume fix
pick c8  Add Dockerfile
pick c7  Hot reload config
pick c6  Add /register endpoint
pick c5  Add password hashing
pick c4  Add /login endpoint
pick c3  Setup routes
pick c2  Init Flask app
pick c1  Init project structure
```
After
```
pick c1 chore: Init project structure  
squash c2 chore: Init Flask app  
squash c3 chore: Setup routes  

pick c4 feat: Add /login endpoint  
squash c5 feat: Add password hashing  
squash c6 feat: Add /register endpoint  

pick c7 chore: Enable hot reload config  
squash c8 chore: Add Dockerfile  
squash c9 fix: Fix Docker volume binding  
squash c10 fix: Handle expired JWT token  
squash c11 feat: Add JWT helper  
squash c12 hotfix: Fix typo in auth
```

### Rebase abort
```
git rebase --abort
```

## Store credentials without pulling repo (Manually)
1. Configure username & email
```
git config --global user.name "your-username"
git config --global user.email "your-email"
```

2. Configure credentials file
```
nano ~/.git-credentials
```
```
https://<your-username>:<your-PAT>@github.com
```

3. Set permission
```
chmod 600 ~/.git-credentials
```

4. Configure git to use `store` with credential file
```
git config --global credential.helper "store --file ~/.git-credentials"
```

## Uploading Large file
1. Install Git and Git LFS
```
sudo apt update
sudo apt install git git-lfs
```

2. Configure Git LFS
```
git lfs install
```

3. Clone Your Repository
```
git clone https://github.com/your-username/your-repository.git
cd your-repository
```

4. Track Large Files
```
git lfs track "*.zip"
```

5. Add and Commit Your Large File
```
git add path/to/your/large-file.zip
git commit -m "Add large file"
```

6. Push to GitHub
```
git push origin main
```

## General
### Store credentials with existing repo
```
git config --global credential.helper store
git pull
```

### Initialize
```
git init
```

### Create new branch
```
git branch -b your-branch
```

### Current changes
```
git status
```

### Adding files
```
git add *
git commit -m "your-comment"
git branch -M main
git remote add origin https://github.com/your-username/your-repository
git push -u origin main
```

### Subsequent adding files
```
git add *
git commit -m "your-comment"
git branch -M main
git push -u origin main
```

### Unstage (remove from commit before pushing)
```
git restore --staged your-file
```

### Add Remote Repository
```
git remote add origin https://github.com/your-username/your-repository
```
