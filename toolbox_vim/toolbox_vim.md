# Toolbox: Vim — Walkthrough

## Task 1: Installing Vim

Vim (Vi IMproved) is a powerful terminal-based text editor widely used in Linux environments.

### Installation

**Debian-based distributions**
```bash
sudo apt install vim
```

**Arch-based distributions**
```bash
sudo pacman -S vim
```

**Fedora-based distributions**
```bash
sudo dnf install vim-enhanced
```

### Launch Vim
```bash
vim
```

---

## Task 2: Vim Modes & Basic Navigation

Vim works with different modes. Understanding them is essential.

### Vim Modes

- **Command mode**: Default mode used to run commands
- **Insert mode**: Used to insert/write text
- **Visual mode**: Used to visually select text

### Questions & Answers

**How do we enter INSERT mode?**  
`i`

**How do we start entering text into a new document?**  
Simply start typing once in insert mode

**How do we return to command mode?**  
`Esc`

### Cursor Movement (Command Mode)

| Action | Key |
|------|-----|
| Move left | `h` |
| Move right | `l` |
| Move up | `k` |
| Move down | `j` |

### Word Navigation

- Jump to start of a word: `w`
- Jump to end of a word: `e`

### Insert & Append Commands

- Insert before cursor: `i`
- Insert at beginning of line: `I`
- Append after cursor: `a`
- Append at end of line: `A`
- Open a new line below current line: `o`

---

## Task 3: Saving & Quitting

### Common Commands

- Write (save) without quitting:
```vim
:w
```

- Write as root:
```vim
:w !sudo tee %
```

- Write and quit:
```vim
:wq
```

- Quit:
```vim
:q
```

- Force quit (discard changes):
```vim
:q!
```

- Save and quit all active tabs:
```vim
:wqa
```

---

## Task 4: Copy, Paste & Delete

### Yank (Copy)

- Copy a line: `yy`
- Copy two lines: `2yy`
- Copy to end of line: `y$`

### Paste

- Paste after cursor: `p`
- Paste before cursor: `P`

### Delete (Cut)

- Cut a line: `dd`
- Cut two lines: `2dd`
- Cut to end of line: `D`
- Cut a character: `x`

> Note: In Vim, delete actions also copy the content into the buffer.

---

## Task 5: Search & Replace

### Search

- Search forward:
```vim
/ pattern
```

- Search backward:
```vim
? pattern
```

- Repeat search (same direction): `n`
- Repeat search (opposite direction): `N`

### Search & Replace

Replace all occurrences of **old** with **new**:
```vim
:%s/old/new/g
```

### Grep in Multiple Files

Use Vim’s internal grep:
```vim
:vimgrep
```

---

## Notes

Vim has a steep learning curve, but mastering these basics already makes you much faster in terminals, CTFs, and servers.

