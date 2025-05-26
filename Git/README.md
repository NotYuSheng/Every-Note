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

### Branch
```
git branch -m your-branch
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

### Clone
```
git clone https://github.com/your-username/your-repository.git
```

### Add Remote Repository
```
git remote add origin https://github.com/your-username/your-repository
```
