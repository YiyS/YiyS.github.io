---
layout: post
title:  "my config of vim"
date:   2016-08-28
desc: "vim折腾记"
keywords: "vim"
categories: [linux]
tags: [vim]
icon: fa-linux
---


## vim界面美化

### 主题solarized

`````````````
    " set theme
    execute pathogen#infect()
    syntax on
    filetype plugin indent on
    syntax enable
    colorscheme solarized

    " Backspace deletes like most programs in insert mode
    set backspace=2
    " Show the cursor position all the time
    set ruler
    " Display incomplete commands
    set showcmd
    " Set fileencodings
    set fileencodings=utf-8,bg18030,gbk,big5
    
    filetype plugin indent on

    " Softtabs.2 spaces
    set tabstop=2
    set shiftwidth=2
    set shiftround
    set expandtab

    " Display extra whitespace
    set list listchars=tab:»·,trail:·

    " Make it obvious where 80 characters is
    set textwidth=80
    set colorcolumn=+1

    " Numbers
    set number
    set numberwidth=5

    set matchpairs+=<:>
    set hlsearch

    " Highlight current line
    au WinLeave * set nocursorline nocursorcolumn
    au WinEnter * set cursorline cursorcolumn
    set cursorline cursorcolumn

````````````````````

### 插件NERDTree

F5打开/关闭NERDTree

````````````````
    let NERDChristmasTree=0
    let NERDTreeWinSize=25
    let NERDTreeChDirMode=2
    let NERDTreeIgnore=['\~$','\.pyc$','.swp$']
    let NERDTreeeShowBookmarks=1
    let NERDTreeWinPos="left"

    " Automatically open a NERDTree if no files where specified
    autocmd StdinReadPre * let s:std_in=1
    autocmd VimEnter * if argc() == 0 && !exists("s:std_in") | NERDTree | endif

    " Close vim if the only window left open is a NERDTree

    " Open a NERDTree while vim start up
    autocmd vimenter * NERDTree
    autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif

    " Open a NERDTree
    nmap <F5> :NERDTreeToggle<cr>
``````````````````

### 插件Tagbar

对大多数语言都是支持的, F6打开/关闭Tagbar

````````````````
    let g:tagbar_width=25
    let g:tagbar_autofocus=1
    autocmd vimenter * Tagbar
    nmap <F6> :TagbarToggle<CR>
``````````````````

### 插件Syntastic

````````````````
    set statusline+=%#warningmsg#
    set statusline+=%{SyntasticStatuslineFlag()}
    set statusline+=%*

    let g:syntastic_always_populate_loc_list = 1
    let g:syntastic_auto_loc_list = 1
    let g:syntastic_check_on_open = 1
    let g:syntastic_check_on_wq = 0
``````````````````

### 插件NERD commenter


\cc:注释当前行

\cn:同上

\c<space>:改变注释状态，注释/去注释

\cm:用指定的注释符注释当前行

\ci: 逐行改变注释状态

\cs:注释当前行with a pretty block formatted layout.

\cy:同ccexcept that the commented line(s) are yanked first.

\c$:从光标位置起注释当前行

\cA:添加注释符

\ca:改变注释符

\cl:注释，注释符左对齐

\cb:注释，注释符两边对齐

\cu:去注释当前行

````````````````
    " Add spaces after comment delimiters by default
    let g:NERDSpaceDelims = 1
    "
    " " Use compact syntax for prettified multi-line comments
    let g:NERDCompactSexyComs = 1
    "
    " " Align line-wise comment delimiters flush left instead of following code
    " indentation
     let g:NERDDefaultAlign = 'left'
    "
    " " Set a language to use its alternate delimiters by default
    let g:NERDAltDelims_java = 1
    "
    " " Add your own custom formats or override the defaults
    let g:NERDCustomDelimiters = { 'c': { 'left': '/**','right': '*/' } }
    "
    " " Allow commenting and inverting empty lines (useful when commenting a
    " region)
    let g:NERDCommentEmptyLines = 1
    "
    " " Enable trimming of trailing whitespace when uncommenting
    let g:NERDTrimTrailingWhitespace = 1

    filetype plugin on
``````````````````

### 插件Nvim-R


#### Start and close

Start R (default);\rf

Start R (custom):\rc

Close R (no save):\rq

Stop R  :RStop


#### Send

File:\aa

File (echo):\ae

File (open .Rout):\ao

Block (cur):\bb

Block (cur, echo):\be

Block (cur, down):\bd

Block (cur, echo and down):\ba

Chunk (cur):\cc

Chunk (cur, echo): \ce

Chunk (cur, down): \cd

Chunk (cur, echo and down): \ca

Chunk (from first to here):\ch

Function (cur):\ff

Function (cur, echo):\fe

Function (cur and down):\fd

Function (cur, echo and down):\fa

Selection:\ss

Selection (echo):\se

Selection (and down):\sd

Selection (echo and down):\sa

Selection (evaluate and insert output in new tab):\so

Paragraph:\pp

Paragraph (echo):\pe

Paragraph (and down):\pd

Paragraph (echo and down):\pa

Line:\l

Line (and down):\d

Line (and new one):\q

Left part of line (cur):\r<Left>

Right part of line (cur):\r<Right>

Line (evaluate and insert the output as comment):\o

#### Command
List space:\rl

Clear console:\rr

Clear all:\rm

Print (cur):\rp

Names (cur):\rn

Structure (cur):\rt

View data.frame (cur):\rv

Arguments (cur):\ra

Example (cur):\re

Help (cur):\rh

Summary (cur):\rs

Plot (cur):\rg

Plot and summary (cur):\rb

Set working directory (cur file path):\rd

Sweave (cur file):\sw

Sweave and PDF (cur file):\sp

Sweave, BibTeX and PDF (cur file) (Linux/Unix):\sb

Knit (cur file):\kn

Knit, BibTeX and PDF (cur file) (Linux/Unix):\kb

Knit and PDF (cur file):\kp

Knit and Beamer PDF (cur file):\kl

Knit and HTML (cur file, verbose):\kh

Knit and ODT (cur file):\ko

Knit and Word Document (cur file):\kw

Markdown render (cur file):\kr

Spin (cur file) (only .R):\ks

Open PDF (cur file):\op

Search forward (SyncTeX):\gp

Go to LaTeX (SyncTeX):\gt

Build tags file (cur dir): :RBuildTags

#### Edit

Insert "<-" : _

Complete object name : ^X^O

Complete function arguments : ^X^A

Indent (line):==

Indent (selected lines) : =

Indent (whole buffer):gg=G

Toggle comment (line, sel):\xx

Comment (line, sel) : \xc

Uncomment (line, sel):\xu

Add/Align right comment (line, sel) : \;

Go (next R chunk):\gn

Go (previous R chunk):\gN


#### Object Browser

Show/Update:\ro

Expand (all lists):\r=

Collapse (all lists):\r-

Toggle (cur):Enter

Help (plugin):

Help (R):Rhelp


### Tmux快捷键


C-a-arrow keys:在窗格间移动光标

C-a-C-Up:重定窗格大小

C-a-[:进入 copy/scroll back 模式

C-a-]:Paste the content of Tmux paste buffer

C-a-z:隐藏其他窗格, `fg` to get Tmux back to the foreground

q:退出 copy and scroll mode

Space:Start text selection

v-Space:Start rectangular text selection

Enter:Copy the selection to Tmux paste buffer

````````````````
    " Change Leader and LocalLeader keys:
    let maplocalleader = ","
    let mapleader = ";"

    " Use Ctrl+Space to do omnicompletion:
    if has("gui_running")
      inoremap <C-Space> <C-x><C-o>
    else
      inoremap <Nul> <C-x><C-o>
    endif

    " Press the space bar to send lines and selection to R:
    vmap <Space> <Plug>RDSendSelection
    nmap <Space> <Plug>RDSendLine

    " R output highlighted using current colorscheme
    let rout_follow_colorscheme = 1


    " config for Tmux
    let R_in_buffer = 0
    let R_applescript = 0
    let R_tmux_split = 1
``````````````````







