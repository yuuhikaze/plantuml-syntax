# Vim PlantUML Syntax/Plugin/FTDetect

### Description

This is a vim syntax file for [PlantUML](http://plantuml.com).

The `filetype` will be set to `plantuml` for `*.pu`, `*.uml`, `*.puml`, `*.iuml` or
`*.plantuml` files or if the first line of a file contains `@startuml`.

Additionally the `makeprg` is set to `plantuml` assuming you have this
executable in your path.  This file could contain something like

````sh
#!/bin/bash
java -jar $HOME/lib/java/plantuml.jar -tsvg $@
````

You can change the name of this file by setting `g:plantuml_executable_script`
and disable this feature by setting `g:plantuml_set_makeprg` to `0`.

See examples here: [Plantuml Syntax](https://aklt.github.io/plantuml/).

### Install

**Packer**

```lua
{
    'yuuhikaze/plantuml-syntax',
    ft = { 'puml', 'plantuml', 'uml', 'iuml' },
    config = function()
        vim.cmd([[autocmd BufRead,BufNewFile * if !did_filetype() && getline(1) =~# '@startuml\>'| setfiletype plantuml | endif]])
        vim.cmd([[autocmd BufRead,BufNewFile *.pu,*.uml,*.plantuml,*.puml,*.iuml set filetype=plantuml]])
    end
}
```
