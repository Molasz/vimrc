# ⚡ Vim Configuration

> Part of [42 Barcelona — molasz-a](https://github.com/Molasz/42), a monorepo centralizing every project completed at 42 Barcelona.

Personal Vim configuration optimized for development, with multi-language support, Git integration, and a visual environment.

---

## 🚀 Installation

1. Clone this repository or copy `.vimrc` to your home directory:

```bash
cp .vimrc ~/.vimrc
```

2. Open Vim. The **vim-plug** plugin manager will be installed automatically if not already present.

3. Plugins will install themselves on first launch thanks to:

```vim
autocmd VimEnter * PlugInstall --sync | source $MYVIMRC
```

4. Or install them manually:

```bash
vim +PlugInstall +qall
```

---

## 🔧 General Settings

### File Format & Encoding

```vim
set fileformat=unix     " Unix-style line endings (LF)
set encoding=UTF-8      " UTF-8 character encoding
```

### Indentation

```vim
set tabstop=4           " A tab character displays as 4 spaces
set softtabstop=4       " Pressing Tab in insert mode moves 4 spaces
set shiftwidth=4        " Auto-indent uses 4 spaces
set autoindent          " Keeps indentation from the previous line
set smartindent         " Context-aware smart indentation
set noexpandtab         " Uses real tab characters, NOT spaces
set smarttab            " Inserts/removes tabs intelligently at line start
```

### Visual & Usability

```vim
set nowrap              " Disables line wrapping (long lines scroll horizontally)
set list                " Shows invisible characters (tabs, trailing spaces)
set number              " Shows absolute line numbers
set relativenumber      " Shows relative line numbers (great for jumping with N+j/k)
set cursorline          " Highlights the current line
set cursorcolumn        " Highlights the current column
set scrolloff=8         " Keeps 8 lines of context above/below the cursor
set noshowmode          " Hides the mode indicator (e.g. -- INSERT --), handled by airline
set showcmd             " Shows the current command in the bottom bar
set conceallevel=1      " Hides some markup characters (e.g. in Markdown)
set shortmess+=c        " Suppresses completion menu messages
```

### Undo, Backup & Swap

```vim
set noswapfile          " Disables .swp swap files
set nobackup            " Disables backup files
set undodir=~/.vim/undodir  " Directory for persistent undo history
set undofile            " Enables persistent undo across sessions
```

### Clipboard

```vim
set clipboard=unnamed, unnamedplus   " Syncs Vim's yank/paste with the system clipboard
```

### Search

```vim
set ignorecase          " Case-insensitive search by default
set smartcase           " Case-sensitive if the query contains uppercase letters
set incsearch           " Shows matches incrementally as you type
set hlsearch            " Highlights all search matches
nnoremap <expr> <CR> &buftype ==# 'quickfix' ? "\<CR>" : ":noh\<CR>\<CR>:\<BS>"
```

### Miscellaneous

```vim
set noerrorbells visualbell t_vb=   " Disables all bell sounds and flashes
set signcolumn=number               " Shows signs (errors, git) in the number column
```

---

## 🎨 Theme & Colors

```vim
set termguicolors                   " Enables true color (24-bit) in the terminal
let g:gruvbox_italic=1              " Enables italic text in Gruvbox
colorscheme gruvbox                 " Applies the Gruvbox color scheme
set background=dark                 " Uses the dark variant of the theme
hi Normal guibg=NONE ctermbg=NONE   " Transparent background (uses terminal's bg)
```

A custom 16-color terminal palette is also defined to match the Gruvbox color spec.

---

## 🔌 Plugins

Managed with [vim-plug](https://github.com/junegunn/vim-plug).

| Plugin                        | Description                            |
| ----------------------------- | -------------------------------------- |
| `morhetz/gruvbox`             | Retro groove color scheme              |
| `preservim/nerdtree`          | File system explorer sidebar           |
| `Xuyuanp/nerdtree-git-plugin` | Git status icons in NERDTree           |
| `vim-airline/vim-airline`     | Lightweight and informative status bar |
| `sheerun/vim-polyglot`        | Syntax highlighting for 100+ languages |
| `tpope/vim-commentary`        | Toggle comments with `gcc` / `gc`      |
| `dense-analysis/ale`          | Async linting and fixing engine        |
| `preservim/tagbar`            | Tag/symbol browser sidebar             |
| `tpope/vim-fugitive`          | Full Git integration inside Vim        |
| `pbondoer/vim-42header`       | Inserts the 42 School file header      |
| `wakatime/vim-wakatime`       | Automatic coding time tracking         |

---

## ⌨️ Keybindings

### NERDTree

```vim
<C-t>       " Toggle the NERDTree file explorer sidebar
```

NERDTree opens automatically on startup. It closes automatically when it is the last window open.

### Tagbar

```vim
<F8>        " Toggle the Tagbar symbol/tag browser
```

### Search

```vim
<CR>        " Clear search highlighting (press Enter in normal mode)
```

### Leader Key

```vim
let mapleader = "\\"        " Leader key is set to backslash

<leader>\   " Jump back to the previous cursor position (``)
<space>     " Open the command line (same as pressing :)
```

---

## 🧩 NERDTree Behavior

```vim
let NERDTreeShowHidden=1            " Show hidden files (dotfiles)
let NERDTreeRespectWildIgnore=1     " Respect wildignore patterns
set wildignore+=*.DS_Store,*.min.*,*.o,*.d,.git  " Files/dirs hidden in NERDTree
```

NERDTree auto-opens on Vim launch and moves focus to the file buffer, not the tree. It auto-quits if it is the only remaining window.

---

## 🏫 42 School Header

```vim
let g:user42 = 'molasz'
let g:mail42 = 'molasz.dev@gmail.com'
```

Used by the `vim-42header` plugin to insert the 42 School standard file header. Update these values with your own login and email.

---

## ⏱️ WakaTime

The `wakatime/vim-wakatime` plugin tracks your coding activity automatically. On first use, you will be prompted to enter your [WakaTime API key](https://wakatime.com/settings/api-key).
