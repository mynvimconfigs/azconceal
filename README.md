# azconceal.nvim

A Neovim plugin for concealing selected text and managing restricted movements within the editor.

The plugin allows you to add a mark (a) to a point in the text, a mark (b) to a second point in the text, and then to conceal everything in the text except for the region between a and b.

This will help you focus your work on the segment you are developing, while declutering your buffer screen real state from other parts of the text.

You can also visually select a text and conceal the selection.

## Installation

Use a plugin manager like `vim-plug` to install, by inconluding the following code into your init.nvim file:

```vim
Plug 'mynvimconfigs/azconceal'
```

After installing, restart Neovim and run `:PlugInstall` to complete the installation.

To use the standard key bindings, put the following code into your init.nvim file (or adapt the key choices to your like):

' --------------------------------------------------------
" Config azconceal key bindings
lua << EOF
-- Key mappings for conceal/unconceal functionality
vim.api.nvim_set_keymap('v', '<Leader>c', ':<C-U>set nofoldenable<CR>:<C-U>call ConcealSelectedText()<CR>:<C-U>set foldtext=CustomFoldText()<CR>:<C-U>set foldmethod=manual<CR>', { noremap = true, silent = true })
vim.api.nvim_set_keymap(
  'n',
  '<Leader>u',
  [[:<C-U>set nofoldenable<CR>:<C-U>set foldtext=foldtext()<CR>:source ~/.config/nvim/plugin/unrestrict_movements.nvim<CR>:set foldmethod=marker<CR>:call UnconcealAllText()<CR>:<C-U>set foldmethod=marker<CR>zm]],
  { noremap = true, silent = true }
)
EOF
nnoremap <leader>x ggV'ak:<C-U>set foldtext=CustomFoldText()<CR>:<C-U>set foldmethod=manual<CR>:<C-U>call ConcealSelectedText()<CR>'zjVG$:<C-U>set foldtext=CustomFoldText()<CR>:<C-U>set foldmethod=manual<CR>:<C-U>call ConcealSelectedText()<CR>:source ~/.config/nvim/plugin/restrict_movements.nvim<CR>k
' --------------------------------------------------------


## Usage

Press "ma" (without quotes) in command mode to add mark a to a point in the text.

Go to another point and press "mb" (without quotes) to add mark b.

Then press `<Leader>x` to conceal everything but the region between a and b.

Or visually select a text and press `<Leader>c` to conceal it.

`<Leader>u` will unconceal everything.

### Key Bindings
- `<Leader>c`: Conceal visually selected text and create a fold.
- `<Leader>u`: Unconceal all text and restore unrestricted movement.
- `<Leader>x`: Conceal all text in a region (between) and restrict movement.

### Commands
- `:call ConcealSelectedText()`: Manually conceal selected text.
- `:call UnconcealAllText()`: Unconceal all text in the buffer.

### Configuration
No additional configuration is required, but you can modify the key mappings in `plugin/azconceal.nvim`.

## Contributing
Feel free to open issues or submit pull requests for improvements or bug fixes.
