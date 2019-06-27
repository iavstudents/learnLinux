# Vim Guide by Alfian
## Move
h left\
j down\
k up\
l right\
w next word first\
e next word last\
gg first line\
shift+g last line\
esc exit all mode

## Loop
number+action\
4w to go next 4 words\
10w to go next 10 words\
100ialfianguide -> exit, then it will type alfianguide until 100

## Save Quit
w save\
q quit\
wq save and quit\
w! force save\
q! force quit

## Insert
i insert mode\
a append in next last word/text\
shift+a append in last word of line\
shift+i insert in first word of line

## Visual
v visual mode, to block select text\
shift+v block line

## Copy
y yank or copy\
shift + " + + + y to yank into +clipboard

## Delete
d delete\
dw delete word\
dd delete line\
daw delete around word

## Undo Redo
u undo\
ctrl+r redo

## Add line
o add line bottom\
shift+o add line up

## Find & Replace

```
:%s/text/replace
```

so it will replace 'text with 'replace'

## Mapping 

<!-- " handle all mapping command -->
let mapleader=','

<!-- " Save -->
noremap <silent> <Leader>wq :wq<CR>
noremap <silent> <Leader>qq :q!<CR>

<!-- " Find -->
noremap <silent> <Leader>f /

<!-- " Replace  -->
noremap <silent> <Leader>r :%s/
<!-- " Replace  -->
noremap <silent> <Leader>rhp :%s/html/pdf<CR>

<!-- " Comment -->
noremap <silent> <Leader>cc  :TComment<CR>

<!-- " Tabular -->
noremap <silent> <Leader>cee :Tabularize /=<CR>
noremap <silent> <Leader>cet :Tabularize /#<CR>
noremap <silent> <Leader>ce  :Tabularize /

<!-- " Go -->
noremap <silent> <Leader>gb  :GoBuild<CR>
noremap <silent> <Leader>gr  :GoRun<CR>

## Plugin Manager and Plugins

Use vundle plugin manager

Nice Plugins

<!-- " Theming -->
Plugin 'itchyny/lightline.vim'
Plugin 'mhartington/oceanic-next'

<!-- " Tools -->
Plugin 'scrooloose/nerdtree'
Plugin 'xuyuanp/nerdtree-git-plugin'
Bundle 'matze/vim-move'
Plugin 'godlygeek/tabular'
Plugin 'tomtom/tcomment_vim'
Plugin 'nathanaelkane/vim-indent-guides'
" Plugin 'wakatime/vim-wakatime'

<!-- " Writing -->
Plugin 'reedes/vim-pencil'

<!-- " wrapper -->
Plugin 'tpope/vim-fugitive'
Plugin 'fatih/vim-go'
Plugin 'iamcco/markdown-preview.nvim'

<!-- " Programming Language -->
Plugin 'sheerun/vim-polyglot'
Plugin 'ap/vim-css-color'

<!-- " Linter -->
<!-- " Plugin 'neoclide/coc.nvim' -->
Plugin 'w0rp/ale'

