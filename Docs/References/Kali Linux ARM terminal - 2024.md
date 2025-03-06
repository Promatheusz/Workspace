# Kali Linux Terminal Documentation on ARM

## Short Description

Comprehensive documentation for configuring and optimizing the terminal experience on Kali Linux for ARM architecture.

## Getting Started

### Overview

#### [ZSH](https://wiki.archlinux.org/title/zsh)
Zsh, or Z Shell, is an enhanced version of the Bourne Shell (sh), featuring improvements for interactive use, command-line editing, and scripting.

##### [Powerlevel10k](https://github.com/romkatv/powerlevel10k)
Powerlevel10k is a highly customizable Zsh theme that enhances usability and aesthetics.

#### [Snapcraft](https://snapcraft.io/)
Snapcraft, developed by Canonical, builds and manages snaps—containerized packages that include all dependencies, ensuring cross-platform compatibility.

#### [Neovim](https://neovim.io/)
Neovim is a modern Vim-based text editor designed for extensibility and integration.

##### [Nerd Fonts](https://www.nerdfonts.com/)
Nerd Fonts are developer-friendly fonts with symbols and icons that enhance terminal and editor visuals.

##### [NVChad](https://nvchad.com/)
NVChad is a customizable Neovim configuration framework with preconfigured plugins for an optimized development experience.

###### Additional Neovim Tools:
- **[Nvimtree](https://github.com/nvim-tree/nvim-tree.lua):** File explorer.
- **[Treesitter](https://github.com/nvim-treesitter/nvim-treesitter):** Syntax highlighting and code analysis.
- **[Tabufline](https://github.com/romgrk/barbar.nvim):** Advanced tab management.
- **[Null-ls](https://github.com/jose-elias-alvarez/null-ls.nvim):** Diagnostics and formatting.
- **[Mason](https://github.com/williamboman/mason.nvim):** Portable LSP server manager.
- **[Telescope](https://github.com/nvim-telescope/telescope.nvim):** Fuzzy finder.
- **[Lazy.nvim](https://github.com/folke/lazy.nvim):** Plugin manager.
- **[LSP Config](https://github.com/neovim/nvim-lspconfig):** Language server framework.
- **[Which Key](https://github.com/folke/which-key.nvim):** Displays keybinding hints.

#### [Tmux](https://github.com/tmux/tmux/wiki)
Tmux is a terminal multiplexer that allows multiple terminal sessions in one window.

##### Tmux Plugins:
- **[TPM](https://github.com/tmux-plugins/tpm):** Plugin manager.
- **[Tmux Sensible](https://github.com/tmux-plugins/tmux-sensible):** Preconfigured defaults.
- **[Vim-Tmux Navigator](https://github.com/christoomey/vim-tmux-navigator):** Seamless navigation between Vim and Tmux.
- **[Tmux Yank](https://github.com/tmux-plugins/tmux-yank):** Copy-paste functionality enhancements.

---

## Installation

### Powerlevel10k
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

### Snapcraft
```bash
sudo apt install -y snapd
sudo systemctl enable --now snapd apparmor
```

### Nerd Fonts
1. Download a font (e.g., JetBrains Mono) from [Nerd Fonts](https://www.nerdfonts.com/font-downloads).
2. Unzip and move files to `~/.local/share/fonts`.

### Neovim
Install via Snap:
```bash
sudo snap install nvim --classic
```

#### NVChad
```bash
git clone --depth=1 https://github.com/NvChad/NvChad ~/.config/nvim --branch v2.0
```

### Tmux
Install:
```bash
sudo apt install tmux
```

#### TPM
```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```
Initialize in `~/.tmux.conf`:
```bash
run '~/.tmux/plugins/tpm/tpm'
```
Reload configuration:
```bash
tmux source ~/.tmux.conf
```

### Docker
```bash
sudo snap install docker
```

---

## Repositories and Configurations

- **ZSH:** `~/.zshrc`
- **Neovim:** `~/.config/nvim`
  - **NVChad Configs:** `~/.config/nvim/lua`
    - `chadrc.lua`: Overwrite NVChad configuration.
    - `init.lua`: Overwrite Neovim configuration.
- **Tmux:** `~/.tmux.conf`
- **Snapcraft:** `/var/lib/snapd`
- **Nerd Fonts:** `~/.local/share/fonts`
- **Environment Variables:** `/etc/environment`
- **Secure Variables:** `/etc/sudoers`

---

## Common Shortcuts

### Neovim
- **Leader Key:** 
	- leader = space
	- C = command 
	- A = option
	-  S = shift
	-  . = repeat last edit 
	- ctrl + h/j/k/l = toggle 
- **Commands:**
  - `:vs` - Vertical split
  - `:sp` - Horizontal split
- **Macros:**
  - `qq` - Start recording
  - `q` - Stop recording
  - `3@q` - Execute macro 3 times
  - `:TSInstall {language}` - Install Treesitter language support
- **Mason:**
  - `:MasonInstallAll` - Install all packages
  - `:Mason` - Display Mason interface

#### NVChad Keymaps:
- `Leader+c+h` - Cheatsheet
- `Leader+e` - Focus NvimTree
- `Leader+x` - Close tab
- `Leader+f+m` - Format file

#### Nvimtree Keymaps:
- `c` - Copy
- `x` - Cut
- `p` - Paste
- `d` - Delete
- `r` - Rename
- `a` - New file
- `H` - Hide/display hidden files
- `E` - Expand all
- `W` - Collapse all

### Tmux
- `Ctrl+A + {` - Enter visual mode
- `Ctrl+A + ]` - Paste buffer

---

## Known Issues

### Snapcraft Not Included in PATH
[Issue Reference](https://stackoverflow.com/questions/57121916/the-command-could-not-be-located-because-snap-bin-is-not-included-in-the-path)

```bash
# Add /snap/bin to PATH
echo "/snap/bin" >> /etc/environment
source /etc/environment
```

### Snapcraft Software Issues with Sudo
Modify `/etc/sudoers`:
```bash
# Enable write
chmod +w sudoers
# Edit PATH
vim sudoers
# Disable write
chmod -w sudoers
```

### Running x86 Code on ARM
Refer to [Kali's x86-on-ARM guide](https://www.kali.org/docs/arm/x86-on-arm/).

### NVChad Keymap Conflicts
Resolve conflicts by customizing keymaps in NVChad's configuration files.

### Tmux Global Clipboard Issues
- [Copy and Paste in tmux](https://www.seanh.cc/2020/12/27/copy-and-paste-in-tmux/)
- [Shortcut for copy-paste](https://stackoverflow.com/questions/48129640/how-can-i-copy-text-from-a-tmux-window-to-the-system-clipboard)

#### Requirements:
- [xsel clipboard](https://ostechnix.com/access-clipboard-contents-using-xclip-and-xsel-in-linux/)

### GDB Undefined Instructions
Install gdb-multiarch:
```bash
sudo apt install gdb-multiarch
```
Use QEMU for architecture emulation:
```bash
sudo apt install qemu-user-static
qemu-x86_64-static ./program
```

---

## Tutorials
- [Turn NVIM into a full-featured IDE](https://www.youtube.com/watch?v=Mtgo-nP_r8Y)
- [The perfect Neovim setup for C++](https://www.youtube.com/watch?v=lsFoZIg-oDs)
- [The perfect Neovim setup for Python](https://www.youtube.com/watch?v=4BnVeOUeZxc)
- [Tmux: Transform the way you code](https://www.youtube.com/watch?v=DzNmUNvnB04)

## Sample Projects
- [josean-dev/dev-environment-files](https://github.com/josean-dev/dev-environment-files)
- [tuffgniuz/nvim.lua](https://github.com/tuffgniuz/nvim.lua/blob/master/lua/options/init.lua)
- [ThePrimeagen/init.lua](https://github.com/ThePrimeagen/init.lua/)
- [dreamsofcode-io/neovim-cpp](https://github.com/dreamsofcode-io/neovim-cpp)
- [dreamsofcode-io/neovim-python](https://github.com/dreamsofcode-io/neovim-python)
- [dreamsofcode-io/tmux](https://github.com/dreamsofcode-io/tmux)

## References
- [Kali docs](https://www.kali.org/docs/)
- [Neovim documentation](https://neovim.io/doc/user/)
- [NVChad Docs](https://nvchad.com/docs/quickstart/install/)
- [Tmux Cheat Sheet](https://tmuxcheatsheet.com/)

## Architecture
- [Kali Linux on ARM](https://www.kali.org/docs/arm/)
- [Images on Apple Silicon](https://www.kali.org/get-kali/#kali-platforms)

