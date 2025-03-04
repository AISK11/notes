# Setup

*- installation and configuration.*

## Installation

### Windows

1. Install [Scoop](https://scoop.sh/):
    ```posh
    ${env:SCOOP} = "${env:USERPROFILE}\AppData\Local\scoop" ; [Environment]::SetEnvironmentVariable('SCOOP', "${env:SCOOP}", 'User')
    Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy Bypass -Force ; Invoke-RestMethod -Uri 'https://get.scoop.sh/' | Invoke-Expression
    ```
1. Install [Git](https://gitforwindows.org/):
    ```posh
    scoop install main/git
    ```

## Configuration

1. Global user configuration file:
    - `~/.gitconfig`
        ```gitconfig
        [init]
            defaultBranch = main
        [credential]
            helper = store
        ```
