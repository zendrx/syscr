# Installation

Crystal is a compiled, statically-typed language with Ruby-like syntax. Before you can write Crystal code, you need to install the compiler on your system.

## Prerequisites

- macOS 10.15+ or Linux (Ubuntu 18.04+, Debian 10+, Fedora 32+, etc.)
- Windows 10+ with WSL2 (recommended) – no native Windows support yet
- Terminal/command line basics (navigating directories, running commands)
- A code editor (VS Code with the Crystal extension is highly recommended)
- Basic understanding of your system's package manager (Homebrew, apt, dnf, pacman, etc.)

## macOS Installation

### Option 1: Homebrew (Easiest)

Homebrew is the most popular package manager for macOS. If you don't have it, install it first:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

Once Homebrew is ready, install Crystal:

brew install crystal
```

This installs both the `crystal` compiler and the `shards` dependency manager.

### Option 2: MacPorts

If you prefer MacPorts over Homebrew, you can use:

```bash
sudo port install crystal
```

### Verify Installation

After installation, check that Crystal is available:

crystal --version

You should see output similar to:

```bash
Crystal 1.12.2 (2024-01-15)

LLVM: 17.0.6
Default target: arm64-apple-darwin23.0.0
```
The exact version numbers may differ, but as long as you see a version and LLVM info, you're good.

## Linux Installation

### Using the Official Install Script (Recommended for All Linux Distros)

The Crystal team provides a universal install script that detects your distribution, adds the official repository, and **installs the latest stable version** – all in one go. You do **not** need to run `apt install` or `dnf install` separately after the script; it handles everything.

Run:

```bash
curl -fsSL https://crystal-lang.org/install.sh | sudo bash
```

That's it. The script will:
- Detect your Linux distribution (Ubuntu, Debian, Fedora, Arch, etc.)
- Add the official Crystal repository (if applicable)
- Install the `crystal` compiler and `shards` package manager

After the script finishes, verify the installation:

crystal --version

If you see a version number, you are ready.

### Manual Installation per Distribution (if you prefer to do it yourself)

If you cannot or do not want to use the install script, you can install manually:

#### Ubuntu / Debian

Add the official repository:

curl -fsSL https://crystal-lang.org/install.sh | sudo bash

Then install (though the script already does this, but if you only want to add the repo, you can skip the install part – but the script installs by default, so this is redundant).

#### Fedora

sudo dnf install crystal

#### Arch Linux

sudo pacman -S crystal

#### Alpine Linux

apk add crystal shards

### Verify Installation

crystal --version

## Windows Installation (via WSL2)

Crystal does not have a native Windows compiler yet, but it runs perfectly in Windows Subsystem for Linux (WSL2). This is the officially recommended way for Windows users.

### Step 1: Enable WSL2

Open PowerShell as Administrator and run:

wsl --install

This installs WSL2 and a default Ubuntu distribution. Reboot if prompted.

### Step 2: Launch Ubuntu

After reboot, launch Ubuntu from the Start Menu or run:

wsl -d Ubuntu

### Step 3: Install Crystal inside WSL

Inside the Ubuntu terminal, you are now on a full Linux environment. Install Crystal using the official script (the same as Linux):

curl -fsSL https://crystal-lang.org/install.sh | sudo bash

The script will detect that you are on Ubuntu (or whatever distribution you chose) and install Crystal automatically.

### Step 4: Verify

crystal --version

### Step 5 (Optional): Access files from Windows

Your WSL files are accessible from Windows at \\wsl$\Ubuntu\home\yourusername. You can also open VS Code from WSL by typing `code .` in the WSL terminal (if you have the Remote - WSL extension installed).

## Install Shards (Dependency Manager)

Shards is Crystal's package manager and is usually bundled with the compiler. The install script and package managers install it automatically. Verify it's installed:

shards --version

If you get a version number, skip this section. If not, install it manually:

### macOS (Homebrew)

brew install shards

### Linux

If for some reason the script didn't install shards, you can install it separately:

Ubuntu/Debian: sudo apt install shards
Fedora: sudo dnf install shards
Arch: sudo pacman -S shards

### Windows WSL

Same as your Linux distribution inside WSL.

## Editor Setup

### VS Code (Recommended)

1. Download and install VS Code from https://code.visualstudio.com
2. Launch VS Code.
3. Open the Extensions view (Ctrl+Shift+X or Cmd+Shift+X).
4. Search for "Crystal Language" and install the official extension by "crystal-lang".
5. For better syntax highlighting and autocompletion, also install "Crystal Tools" if available.

### Other Editors

- Vim / Neovim: Install the `crystal.vim` plugin.
- Emacs: Install `crystal-mode`.
- Sublime Text: Install the "Crystal" package via Package Control.

## Testing Your Installation

Create a simple test file to confirm everything works:

echo 'puts "Hello from Crystal!"' > test.cr

Now run it:

crystal test.cr

If you see "Hello from Crystal!" printed, congratulations – your Crystal environment is ready!

## Troubleshooting Common Issues

### "crystal: command not found"

This means Crystal is not in your PATH. Add it manually:

```bash
For bash (edit ~/.bashrc):
echo 'export PATH="$PATH:/usr/local/bin"' >> ~/.bashrc
source ~/.bashrc

For zsh (edit ~/.zshrc):
echo 'export PATH="$PATH:/usr/local/bin"' >> ~/.zshrc
source ~/.zshrc
```

If you installed via a package manager, the binary is usually in /usr/bin, which should already be in PATH. Check with `which crystal`.

### Permission denied when running install commands

Prepend `sudo` to install commands, or install Crystal in a user‑local directory (not covered here).

### SSL certificate errors on Linux

When running `curl`, you might get SSL errors. Install the certificates:

sudo apt install ca-certificates   # Debian/Ubuntu
sudo dnf install ca-certificates   # Fedora

### Shards not found even after Crystal install

Sometimes shards is a separate package. Install it as described above.

### Build tools missing (compilation errors)

Crystal needs a C compiler (gcc/clang) and standard build tools. Install them:

Ubuntu/Debian: sudo apt install build-essential
Fedora: sudo dnf install gcc gcc-c++
Arch: sudo pacman -S base-devel

### macOS: "xcrun: error: invalid active developer path"

Install Xcode Command Line Tools:

xcode-select --install

### The install script fails with "No such file or directory"

Make sure `curl` is installed. If not, install it first: `sudo apt install curl` (or equivalent). Also ensure you have `sudo` privileges.

### The script installs an older version?

The official script always points to the latest stable release. If you need a specific version, you can use package managers directly.

## What's Next?

You now have Crystal installed and verified. The next lesson will guide you through writing your first program – Hello World. You'll learn how to run Crystal code, compile it, and understand the basics of the language.

Proceed to the **Hello World** lesson.
