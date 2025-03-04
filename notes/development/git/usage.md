# Usage

*- cheat sheet.*

## Cheat Sheet

### Start

- Create new repository in current directory:
    ```sh
    git init
    ```
- Clone repository:
    ```sh
    git clone --depth 1 <REPOSITORY>
    ```

### Commit

- Add all project files to index and commit them:
    ```sh
    git add -vA
    git commit -m '<MESSAGE>'
    ```

### Status

- Show uncommited changed files:
    ```sh
    git status -s
    ```
- Show commit history:
    ```sh
    git log --oneline --graph --stat
    ```
- Show changes of specific (default: last) commit:
    ```sh
    git show [COMMIT]
    ```

### Restore

- Restore project to last commit:
    ```sh
    git reset --hard && git clean -fxd
    ```

### Remote

- Push commits to git platform:
    ```sh
    git push
    ```
- Obtain commits from git platform:
    ```sh
    git pull
    ```
