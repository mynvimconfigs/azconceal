# azconceal.nvim

A Neovim plugin for concealing selected text and managing restricted movements within the editor.

The plugin allows you to add a mark (a) to a point in the text, a mark (b) to a second point in the text, and then to conceal everything in the text except for the region between a and b.

This will help you focus your work on the segment you are developing, while declutering your buffer screen real state from other parts of the text.

You can also visually select a text and conceal the selection.

## Installation

Use a plugin manager like `vim-plug` to install:

```vim
Plug 'mynvimconfigs/azconceal.nvim'
```

After installing, restart Neovim and run `:PlugInstall` to complete the installation.

## Usage

Press "ma" (without quotes) in command mode to add mark a to a point in the text.

Go to another point and press "mb" (without quotes) to add mark b.

Then press '<Leader>x' to conceal everything but the region between a and b.

Or visually select a text and press <Leader>c to conceal it.

<Leader>u will unconceal everything.

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
