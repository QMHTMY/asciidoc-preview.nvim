<h1 align="center"> Asciidoc文档预览插件(Neo)vim </h1>

### 简述
&emsp; [[English](./README.md)] 在浏览器上直接预览[asciidoc](http://asciidoc.org/)文档的Vim插件。

### 适用系统
- Mac OS
- Windows
- Unix-like OS

### Vim要求
* vim >= 8.1  
* 或 [neovim](https://neovim.io) 

### 计划中的功能

- Multi-platforms (macos/linux/windows)
- Synchronised scrolling
- Fast asynchronous updates
- Emoji
- Task lists
- Local images
- Flexible configuration
<!-- - [Katex](https://github.com/Khan/KaTeX) for typesetting of math 
\- [Plantuml](https://github.com/plantuml/plantuml)
\- [Mermaid](https://github.com/knsv/mermaid)
\- [Chart.js](https://github.com/chartjs/Chart.js)
\- [sequence-diagrams](https://github.com/bramp/js-sequence-diagrams)
\- [Toc](https://github.com/nagaozen/asciidoc-it-toc-done-right) -->

<!-- ![screenshot](https://user-images.githubusercontent.com/5492542/47603494-28e90000-da1f-11e8-9079-30646e551e7a.gif) -->

<!-- ### install & usage 

Install with [vim-plug](https://github.com/junegunn/vim-plug):

```vim
" If you don't have nodejs and yarn
" use pre build
Plug 'QMHTMY/asciidoc-preview.nvim', { 'do': { -> asdp#util#install() } }

" If you have nodejs and yarn
Plug 'QMHTMY/asciidoc-preview.nvim', { 'do': 'cd app & yarn install'  }
```-->

<!-- Or install with [dein](https://github.com/Shougo/dein.vim):

```vim
call dein#add('QMHTMY/asciidoc-preview.nvim', {'build': 'yarn install', 'merged':0}),
```

Config:

```vim
" set to 1, nvim will open the preview window after entering the asciidoc buffer
" default: 0
let g:asdp_auto_start = 0

" set to 1, the nvim will auto close current preview window when change
" from asciidoc buffer to another buffer
" default: 1
let g:asdp_auto_close = 1

" set to 1, the vim will refresh asciidoc when save the buffer or
" leave from insert mode, default 0 is auto refresh asciidoc as you edit or
" move the cursor
" default: 0
let g:asdp_refresh_slow = 0

" set to 1, the AsciidocPreview command can be use for all files,
" by default it can be use in asciidoc file
" default: 0
let g:asdp_command_for_global = 0

" set to 1, preview server available to others in your network
" by default, the server listens on localhost (127.0.0.1)
" default: 0
let g:asdp_open_to_the_world = 0

" use custom IP to open preview page
" useful when you work in remote vim and preview on local browser
" more detail see: https://github.com/QMHTMY/asciidoc-preview.nvim/
" default empty
let g:asdp_open_ip = ''

" specify browser to open preview page
" default: ''
let g:asdp_browser = ''

" set to 1, echo preview page url in command line when open preview page
" default is 0
let g:asdp_echo_preview_url = 0

" a custom vim function name to open preview page
" this function will receive url as param
" default is empty
let g:asdp_browserfunc = ''

" options for asciidoc render
" mkit: asciidoc-it options for render
" katex: katex options for math
" uml: asciidoc-it-plantuml options
" maid: mermaid options
" disable_sync_scroll: if disable sync scroll, default 0
" sync_scroll_type: 'middle', 'top' or 'relative', default value is 'middle'
"   middle: mean the cursor position alway show at the middle of the preview page
"   top: mean the vim top viewport alway show at the top of the preview page
"   relative: mean the cursor position alway show at the relative positon of the preview page
" hide_yaml_meta: if hide yaml metadata, default is 1
" sequence_diagrams: js-sequence-diagrams options
let g:asdp_preview_options = {
    \ 'mkit': {},
    \ 'katex': {},
    \ 'uml': {},
    \ 'maid': {},
    \ 'disable_sync_scroll': 0,
    \ 'sync_scroll_type': 'middle',
    \ 'hide_yaml_meta': 1,
    \ 'sequence_diagrams': {}
    \ }

" use a custom asciidoc style must be absolute path
let g:asdp_asciidoc_css = ''

" use a custom highlight style must absolute path
let g:asdp_highlight_css = ''

" use a custom port to start server or random for empty
let g:asdp_port = ''

" preview page title
" ${name} will be replace with the file name
let g:asdp_page_title = '「${name}」'
```

Mappings:

```vim
" normal/insert
<Plug>AsciidocPreview
<Plug>AsciidocPreviewStop
<Plug>AsciidocPreviewToggle

" example
nmap <C-s> <Plug>AsciidocPreview
nmap <M-s> <Plug>AsciidocPreviewStop
nmap <C-p> <Plug>AsciidocPreviewToggle
```

Commands:

```vim
" Start the preview
:AsciidocPreview

" Stop the preview"
:AsciidocPreviewStop
```
-->

<!-- ### Custom Examples

**Toc:**

    ${toc}, [[toc]], [toc], [[_toc_]]

**plantuml:**

    @startuml
    Bob -> Alice : hello
    @enduml

Or
    ``` plantuml
    Bob -> Alice : hello
    ```

**katex:**

    $\sqrt{3x-1}+(1+x)^2$

    $$\begin{array}{c}

    \nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} &
    = \frac{4\pi}{c}\vec{\mathbf{j}}    \nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\

    \nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\

    \nabla \cdot \vec{\mathbf{B}} & = 0

    \end{array}$$

**mermaid:**

    ``` mermaid
    gantt
        dateFormat DD-MM-YYY
        axisFormat %m/%y

        title Example
        section example section
        activity :active, 01-02-2019, 03-08-2019
    ```

**js-sequence-diagrams:**

    ``` sequence-diagrams
    Andrew->China: Says
    Note right of China: China thinks\nabout it
    China->Andrew: How are you?
    Andrew->>China: I am good thanks!
    ```

**chart:**

    ``` chart
    {
      "type": "pie",
      "data": {
        "labels": [
          "Red",
          "Blue",
          "Yellow"
        ],
        "datasets": [
          {
            "data": [
              300,
              50,
              100
            ],
            "backgroundColor": [
              "#FF6384",
              "#36A2EB",
              "#FFCE56"
            ],
            "hoverBackgroundColor": [
              "#FF6384",
              "#36A2EB",
              "#FFCE56"
            ]
          }
        ]
      },
      "options": {}
    }
    ```

### FAQ

Question: Why is the synchronised scrolling lagging?

Answer: set `updatetime` to a small number, for instance: `set updatetime=100`

### About vim support

Vim support is powered by [vim-node-rpc](https://github.com/neoclide/vim-node-rpc)

> This plugin is integrated with vim-node-rpc, therefore you don't need to install vim-node-rpc

### Reference

- [coc.nvim](https://github.com/neoclide/coc.nvim)
- [vim-node-rpc](https://github.com/neoclide/vim-node-rpc)
- [chart.js](https://github.com/chartjs/Chart.js)
- [highlight](https://github.com/highlightjs/highlight.js)
- [neovim/node-client](https://github.com/neovim/node-client)
- [next.js](https://github.com/zeit/next.js)
- [asciidoc.css](https://github.com/QMHTMY/asciidoc.css)
- [asciidoc-it](https://github.com/asciidoc-it/asciidoc-it)
- [asciidoc-it-katex](https://github.com/waylonflinn/asciidoc-it-katex)
- [asciidoc-it-plantuml](https://github.com/gmunguia/asciidoc-it-plantuml)
- [asciidoc-it-chart](https://github.com/tylingsoft/asciidoc-it-chart)
- [mermaid](https://github.com/knsv/mermaid)
- [opener](https://github.com/domenic/opener)
- [sequence-diagrams](https://github.com/bramp/js-sequence-diagrams)
- [socket.io](https://github.com/socketio/socket.io)

### Buy Me A Coffee 

![btc](https://img.shields.io/keybase/btc/iamcco.svg?style=popout-square)

![image](https://user-images.githubusercontent.com/5492542/42771079-962216b0-8958-11e8-81c0-520363ce1059.png)
-->
