# Vim Guide by Alfian
### Move
h left\
j down\
k up\
l right\
w next word first\
e next word last\
gg first line\
shift+g last line\
esc exit all mode

### Loop
number+action\
4w to go next 4 words\
10w to go next 10 words\
100ialfianguide -> exit, then it will type alfianguide until 100

### Save Quit
w save\
q quit\
wq save and quit\
w! force save\
q! force quit

### Insert
i insert mode\
a append in next last word/text\
shift+a append in last word of line\
shift+i insert in first word of line

### Visual
v visual mode, to block select text\
shift+v block line

### Copy
y yank or copy\
shift + " + + + y to yank into +clipboard

### Delete
d delete\
dw delete word\
dd delete line\
daw delete around word

### Undo Redo
u undo\
ctrl+r redo

### Add line
o add line bottom\
shift+o add line up

### Find & Replace

```
:%s/text/replace
```

so it will replace 'text with 'replace'

### Mapping 
```
" handleAllMappingCommand
let mapleader=','

" save
noremap <silent> <Leader>s   :w<CR>
noremap <silent> <Leader>wq  :wq<CR>
noremap <silent> <Leader>e  :q!<CR>

" find
noremap <silent> <Leader>f /

" split
noremap <silent> <Leader>l  :split<CR>

" replace
noremap <silent> <Leader>r   :%s/

" replace
noremap <silent> <Leader>rhp :%s/html/pdf<CR>

" comment
noremap <silent> <Leader>c   :TComment<CR>

" tabular
noremap <silent> <Leader>te  :Tabularize /=<CR>
noremap <silent> <Leader>tt  :Tabularize /:<CR>
noremap <silent> <Leader>t   :Tabularize /

" markDown
noremap <silent> <leader>mp  :MarkdownPreview<CR>

" java
noremap <silent> <Leader>jc  :!javac %<CR>
noremap <silent> <Leader>jr  :!java

" java
noremap <silent> <Leader>rb  :!cargo build<CR>
noremap <silent> <Leader>rr  :!cargo run<CR>
noremap <silent> <Leader>rc  :!cargo check<CR>

" nerdtree
noremap <silent> <Leader>n   :NERDTreeFind<CR>

" yank into clipboard
noremap <silent> <Leader>y "+y

" put from clipboard
" noremap <silent> <Leader>p "+P<CR><ESC>
noremap <silent> <Leader>p "+p
```
### Plugin Manager and Plugins
```
Use your own plugin manager, mine was, vundle plugin manager.

Nice Plugins

" default
Plugin 'VundleVim/Vundle.vim'

" theming
Plugin 'itchyny/lightline.vim'
Plugin 'mhartington/oceanic-next'

" tools
Plugin 'scrooloose/nerdtree'
Plugin 'xuyuanp/nerdtree-git-plugin'
Bundle 'matze/vim-move'
Plugin 'godlygeek/tabular'
Plugin 'tomtom/tcomment_vim'
Plugin 'nathanaelkane/vim-indent-guides'
Plugin 'wakatime/vim-wakatime'
Plugin 'airblade/vim-gitgutter'

" wrapper
Plugin 'tpope/vim-fugitive'
Plugin 'iamcco/markdown-preview.nvim'

" programmingLanguage
Plugin 'sheerun/vim-polyglot'
Plugin 'ap/vim-css-color'

" linter
Plugin 'neoclide/coc.nvim'
Plugin 'w0rp/ale'
```
