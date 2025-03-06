# MacOS Iterm2 Documentation

## Short Description

This comprehensive manual details the advanced configuration of terminal environments on macOS, focusing on tools such as **iTerm2**, **Neovim**, **Tmux**, and complementary enhancements. The guide is tailored for developers and power users aiming to elevate their productivity through meticulous customization.

---

## Table of Contents

1. [Getting Started](#getting-started)
2. [Installation](#installation)
3. [Repositories and File Locations](#repositories-and-file-locations)
4. [Common Shortcuts](#common-shortcuts)
5. [Troubleshooting](#issues)
6. [Tutorials](#tutorials)
7. [Sample Projects](#sample-projects)
8. [References](#references)

---

## Getting Started

### Overview

#### [iTerm2](https://iterm2.com/)

A robust terminal emulator for macOS, iTerm2 is renowned for its extensive customization capabilities.

#### [iTerm2 Themes](https://iterm2colorschemes.com/)

Enhance the aesthetic and readability of iTerm2 by employing pre-configured color schemes.

#### [Nerd Fonts](https://www.nerdfonts.com/)

Optimize code appearance with developer-oriented fonts enriched with symbols and icons.

#### [Oh My Zsh](https://ohmyz.sh)

A comprehensive framework for Zsh configuration, offering themes and plugins to streamline the command-line experience.

##### Notable Plugins

- **[Powerlevel10k](https://github.com/romkatv/powerlevel10k)**: An exceptionally customizable theme.
- **[Autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)**: Provides dynamic command suggestions as you type.
- **[Syntax Highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)**: Enhances command readability through syntax coloring.

#### [Homebrew](https://brew.sh)

A premier package manager for macOS, facilitating seamless software installation and management.

#### [Neovim](https://neovim.io/)

A modern reimagining of Vim, tailored to improve text editing efficiency and extensibility.

##### Popular Configurations

- **[NVChad](https://nvchad.com/)**: A powerful configuration framework for Neovim.
    - **[NVimTree](https://github.com/nvim-tree/nvim-tree.lua)**: A file explorer plugin.
    - **[Treesitter](https://github.com/nvim-treesitter/nvim-treesitter)**: Enables advanced syntax highlighting and code manipulation.
    - **[Telescope](https://github.com/nvim-telescope/telescope.nvim)**: A fuzzy file and text finder.

#### [Tmux](https://github.com/tmux/tmux/wiki)

A terminal multiplexer designed to manage multiple terminal sessions with efficiency.

##### Tmux Plugins

- **[Tpm](https://github.com/tmux-plugins/tpm)**: The Tmux Plugin Manager (TPM) simplifies plugin management in Tmux.
- **[Tmux Sensible](https://github.com/tmux-plugins/tmux-sensible)**: A plugin that offers a curated set of default settings to streamline the Tmux configuration.
- **[Vim-Tmux-Navigator](https://github.com/christoomey/vim-tmux-navigator)**: Enables seamless navigation between Vim splits and Tmux panes using the same key bindings.
- **[Tmux-Yank](https://github.com/tmux-plugins/tmux-yank)**: Enhances the copying and pasting experience within Tmux sessions.

---

## Installation

### iTerm2

```bash
brew install --cask iterm2
```

#### Configuring Themes

1. Open Preferences (`CMD + i`).
2. Navigate to **Colors** > **Load Presets**.
3. Import themes from [iTerm2 Color Schemes](https://iterm2colorschemes.com/).

#### Installing Nerd Fonts

```bash
brew tap homebrew/cask-fonts
brew install font-hack-nerd-font
```

### Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

#### Adding Plugins

```bash
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
source $ZSH/oh-my-zsh.sh
```

#### Installing Powerlevel10k

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

#### Installing Autosuggestions

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

#### Installing Syntax Highlighting

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

### Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Neovim

```bash
brew install neovim
```

#### NVChad

```bash
git clone https://github.com/NvChad/starter ~/.config/nvim && nvim
```

Run `:MasonInstallAll` in Neovim.

### Tmux

```bash
brew install tmux
```

#### Installing TPM

```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

```bash
# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'
```

```bash
# Type this in terminal if tmux is already running
tmux source ~/.tmux.conf
```

---

## Repositories and File Locations

- **iTerm2**: `~/.iterm2`
- **Tmux**: `~/.config/tmux/tmux.conf`
- **Oh My Zsh**: `~/.zshrc`
- **Neovim**: `~/.config/nvim`
    - **NVChad Configurations**:
        - `~/.config/nvim/lua`
        - Files: `chadrc.lua`, `init.lua`
- **Homebrew**: `/opt/homebrew`
- **Nerd Fonts**: `~/Library/Fonts/`

---

## Common Shortcuts

### iTerm2

- `Control + C`: Kill command.
- `Control + D`: End of input/file.
- `Space`, `f`, `Control + f`: Advance one page.
- `d`, `Control + d`: Advance half a page.
- `b`, `Control + b`: Go back one page.
- `u`, `Control + u`: Go back half a page.

### Homebrew

- List packages: `brew list` | `brew leaves` | `brew deps --tree --installed`

### Neovim

#### Keys

- `leader = space` ; `C = command` ; `A = option` ; `S = shift` ; `.` = repeat last edit ; `ctrl + h/j/k/l = toggle`

#### Commands

- `:vs`: Vertical split
- `:sp`: Horizontal split

#### Macro Recording

- `qq`: Start recording
- `q`: Stop recording
- `3@q`: Execute your macro three times

##### NVChad Keymaps

- `leader+c+h`: Cheatsheet
- `leader`: Suggestion
- `leader + e + q`: Toggle Tree sitter
- `leader + e`: Focus Tree sitter
- `leader + x`: Close tab
- `leader + f + m`: Format file

##### NvimTree Keys

- `c`: Copy
- `x`: Cut
- `p`: Paste
- `d`: Delete
- `r`: Rename
- `a`: New file
- `H`: Hide/display hidden files
- `E`: Expand all
- `W`: Collapse all

#### Commands

- `:TSInstall {language}`: Install language parser.
- `:help mason.vim`: Help information.
- `:MasonInstallAll`: Install all packages.
- `:Mason`: Display Mason.

### Tmux

- `Control + A + {`: Enter visual mode.
- `Control + A + ]`: Paste buffer.

---

## Issues

### NVChad Keymaps Conflict

The solution is to change overlapping key bindings in Neovim's custom configuration.

### Tmux Global Clipboard Doesn't Work

- [Copy and Paste in Tmux](https://www.seanh.cc/2020/12/27/copy-and-paste-in-tmux/)
- [Shortcut to Copy and Paste from Internal Tmux Clipboard](https://stackoverflow.com/questions/48129640/how-can-i-copy-text-from-a-tmux-window-to-the-system-clipboard)

#### Install `xsel` Clipboard

```bash
brew install xsel
```

#### Add Configurations to `tmux.conf`

```bash
set -g @yank_action 'copy-pipe-no-clear'
bind -T copy-mode    C-c send -X copy-pipe-no-clear "xsel -i --clipboard"
bind -T copy-mode-vi C-c send -X copy-pipe-no-clear "xsel -i --clipboard"
```

### GCC Doesn't Work After Installation

- [Install GCC-12/G++-12 on macOS Apple M1](https://trinhminhchien.com/install-gcc-g-on-macos-monterey-apple-m1/)

---

## Tutorials

- [How To Make Your Boring Mac Terminal So Much Better](https://www.youtube.com/watch?v=CF1tMjvHDRA&list=PLTPTYxCPWwnyWrNjBFFvmJ-h9v_i0pk7W&index=2&t=60s)
- [How To Setup Your Mac Terminal](https://www.josean.com/posts/terminal-setup)
- [Turn NVIM into a Full-Featured IDE with Only One Command](https://www.youtube.com/watch?v=Mtgo-nP_r8Y&list=PLTPTYxCPWwnyWrNjBFFvmJ-h9v_i0pk7W&index=5)
- [The Perfect Neovim Setup for C++](https://www.youtube.com/watch?v=lsFoZIg-oDs&list=PLTPTYxCPWwnyWrNjBFFvmJ-h9v_i0pk7W&index=5)
- [The Perfect Neovim Setup for Python](https://www.youtube.com/watch?v=4BnVeOUeZxc&list=PLTPTYxCPWwnyWrNjBFFvmJ-h9v_i0pk7W&index=4)
- [Tmux Has Forever Changed the Way I Write Code](https://www.youtube.com/watch?v=DzNmUNvnB04&t=122s)

---

## Sample Projects

- [josean-dev/dev-environment-files](https://github.com/josean-dev/dev-environment-files)
- [tuffgniuz/nvim.lua](https://github.com/tuffgniuz/nvim.lua/blob/master/lua/options/init.lua)
- [ThePrimeagen/init.lua](https://github.com/ThePrimeagen/init.lua/commit/33eee9ad0c035a92137d99dae06a2396be4c892e#diff-4653caf82f39017df5f84e04cd3f9d05ccd3244d9da1ecb47b85bcad69b86d5c)
- [Neovim Configuration](https://github.com/topics/neovim-configuration?l=lua)
- [dreamsofcode-io/neovim-cpp](https://github.com/dreamsofcode-io/neovim-cpp)
- [dreamsofcode-io/neovim-python](https://github.com/dreamsofcode-io/neovim-python)
- [dreamsofcode-io/tmux](https://github.com/dreamsofcode-io/tmux)

---

## References

- [Brew Manpage](https://docs.brew.sh/Manpage)
- [Neovim Documentation](https://neovim.io/doc/user/)
- [NVChad Docs](https://nvchad.com/docs/quickstart/install/)
- [NVChad UI/NvimTree](https://docs.rockylinux.org/books/nvchad/nvchad_ui/nvimtree/)
- [ryanoasis/nerd-font](https://github.com/ryanoasis/nerd-fonts)
- [Tmux Cheat Sheet](https://tmuxcheatsheet.com/)

---

## Architecture

- [Arm](https://en.wikipedia.org/wiki/Apple_M1)
