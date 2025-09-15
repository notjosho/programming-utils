# Vim Basics

**Resources:**
- [Vim Tutorial](https://www.openvim.com/)
- [Vim Cheat Sheet](https://vim.rtorr.com/)
- [Vim Official Documentation](https://vimdoc.sourceforge.net/)

## Modes
- **Normal mode**: Navigation and commands (default)
- **Insert mode**: Text editing (press `i`)
- **Visual mode**: Text selection (press `v`)
- **Command mode**: Execute commands (press `:`)

## Basic Commands

### Entering Insert Mode
```vim
i                   # Insert before cursor
a                   # Insert after cursor
o                   # New line below
O                   # New line above
```

### Navigation (Normal Mode)
```vim
h j k l             # Left, down, up, right
w                   # Next word
b                   # Previous word
0                   # Beginning of line
$                   # End of line
gg                  # Go to first line
G                   # Go to last line
```

### Editing (Normal Mode)
```vim
x                   # Delete character
dd                  # Delete line
yy                  # Copy line
p                   # Paste
u                   # Undo
Ctrl+r              # Redo
```

### Save and Quit
```vim
:w                  # Save
:q                  # Quit
:wq                 # Save and quit
:q!                 # Quit without saving
```

## Search and Replace
```vim
/pattern            # Search forward
?pattern            # Search backward
n                   # Next match
N                   # Previous match
:%s/old/new/g       # Replace all occurrences
```

## Advanced Navigation
```vim
Ctrl+f              # Page down
Ctrl+b              # Page up
:42                 # Go to line 42
*                   # Search for word under cursor
```

## Visual Mode
```vim
v                   # Character visual mode
V                   # Line visual mode
Ctrl+v              # Block visual mode
d                   # Delete selection
y                   # Copy selection
```

## Useful Commands
```vim
:set number         # Show line numbers
:set paste          # Paste mode (preserves formatting)
:syntax on          # Enable syntax highlighting
:help command       # Get help for command
```

