A vim plugin to search and replace across project files interactively.

## Overview

Based on the vim-script by Yegappan Lakshmanan
http://www.vim.org/scripts/script.php?script_id=1813

Modifications to the original:

 * Default to recursive search.
 * Add settings to change search command and options.

This plugin allows you to search and replace a pattern across multiple
files. The lines containing a specified pattern in multiple files are
displayed in a buffer. You can edit the lines in this buffer and make
the desired modifications to them. You can then incorporate these
changes back into the corresponding files interactively.

The following commands are provided by this plugin:

```
:Gsearch         Search for a given pattern in the specified group of
                 files and display the matches in the replace buffer.
:Gbuffersearch   Search for a given pattern in all the buffers
                 in the Vim buffer list.
:Gargsearch      Search for a given pattern in all the files in the
                 Vim argument list.
:Gqfopen         Use the results from the quickfix list.
:Greplace        Incorporate the modifications from the replace buffer
                 into the corresponding files.
```

Refer to [greplace.txt](doc/greplace.txt) for more information.

This plugin will only run on Vim version 7.0 and above.

## Usage

1.  Invoke `:Gsearch <search>` where `<search>` is the search pattern.
    If `<search>` isn't specified you will be prompted for it.
2.  Make replacement modifications inside the search buffer window that opens.
3.  Invoke `:Greplace` to apply changes across all files. You will be
    asked interactively whether to apply each replacement `y` (yes), `n` (no),
    or `a` (apply all changes).
4.  Save changes to all files with `:wall` (write all) if desired.

## Customization

To customize command used for `:Gsearch` you can update both the command and
the default options.

  * [git grep](https://www.kernel.org/pub/software/scm/git/docs/git-grep.html)

        let g:greplace_cmd='git grep'
        let g:greplace_cmd_opts='--line-number'

  * [ag](https://github.com/ggreer/the_silver_searcher)

        let g:greplace_cmd='ag'
        let g:greplace_cmd_opts='--numbers --noheading'

  * [ack](http://beyondgrep.com/)

        let g:greplace_cmd='ack'
        let g:greplace_cmd_opts='--noheading'

