<p align="center">
    <h2 align="center">Flexoki for neovim</h2>
</p>

> Flexoki is an inky color scheme for prose and code. Flexoki is designed for reading and writing on digital screens. It is inspired by analog printing inks and warm shades of paper

This repo contains a light and dark theme for Flexoki, based on [https://stephango.com/flexoki](https://stephango.com/flexoki). This repo was based off of [rose-pine/neovim](https://github.com/rose-pine/neovim).

## Getting started

Install `flexoki-nvim` using your favourite plugin manager:

**lazy.nvim**

```lua
{ "nuvic/flexoki-nvim", name = "flexoki" }
```

**paq-nvim**

```lua
{ "nuvic/flexoki-nvim", as = "flexoki" }
```

## Gallery

**Flexoki Dawn**

![flexoki-dawn](https://github.com/user-attachments/assets/8ad5bd55-6da8-4966-8c4e-360be0a8847a)

**Flexoki Moon**

![flexoki-moon](https://github.com/user-attachments/assets/f29beed6-6cf8-48d3-90cb-b4a10f00e373)

## Options

> [!IMPORTANT]
> Configure options _before_ setting colorscheme.

Each `italic` category controls specific highlight groups:

| Category | Highlight groups |
|---|---|
| `comments` | `Comment`, `Folded` |
| `functions` | `Function`, `@function`, `@function.builtin`, `@function.method`, `@function.method.call`, `@function.macro` |
| `keywords` | `Keyword`, `@keyword` |
| `parameters` | `@parameter`, `@variable.parameter` |
| `variables` | `@variable` |
| `properties` | `@property` |
| `strings` | `String`, `@string` |
| `types` | `Type`, `@type`, `@type.builtin` |
| `markup` | `@text.emphasis`, `@markup.italic`, `htmlItalic`, `mkdCode` |
| `suggestions` | `NeogitChange*`, `NeogitFilePath`, `CopilotSuggestion` |

Flexoki has two variants: moon, and dawn. By default, `vim.o.background` is followed, using dawn when light and moon when dark.

Colour values accept named colours from the palette, e.g. "cyan_two", or valid hex, e.g. "#fa8072".

```lua
require("flexoki").setup({
    variant = "auto", -- auto, moon, or dawn
    dark_variant = "moon", -- variant to use when background is dark
    dim_inactive_windows = false,
    extend_background_behind_borders = true,

    enable = {
        terminal = true,
        legacy_highlights = true, -- enable legacy tree-sitter capture groups
        migrations = true, -- auto-migrate deprecated options
    },

    styles = {
        bold = true,
        italic = {
            comments = false,
            functions = false,
            keywords = false,
            parameters = false,
            variables = false,
            properties = false,
            types = false,
            strings = false,
            markup = false,
            suggestions = false,
        },
        transparency = false,
    },

    groups = {
        border = "muted",
        link = "purple_two",
        panel = "surface",

        error = "red_two",
        hint = "purple_two",
        info = "cyan_two",
        ok = "green_two",
        warn = "orange_two",
        note = "blue_two",
        todo = "magenta_two",

        git_add = "green_one",
        git_change = "yellow_one",
        git_delete = "red_one",
        git_dirty = "yellow_one",
        git_ignore = "muted",
        git_merge = "purple_one",
        git_rename = "blue_one",
        git_stage = "purple_one",
        git_text = "blue_one",
        git_untracked = "subtle",

        h1 = "purple_two",
        h2 = "cyan_two",
        h3 = "magenta_two",
        h4 = "orange_two",
        h5 = "blue_two",
        h6 = "green_two",
    },

    palette = {
        -- Override the builtin palette per variant
        -- moon = {
        --     base = '#100f0f',
        --     overlay = '#1c1b1a',
        -- },
    },

    highlight_groups = {
        -- Comment = { fg = "subtle" },
        -- VertSplit = { fg = "muted", bg = "muted" },
    },

    before_highlight = function(group, highlight, palette)
        -- Disable all undercurls
        -- if highlight.undercurl then
        --     highlight.undercurl = false
        -- end
        --
        -- Change palette colour
        -- if highlight.fg == palette.blue_two then
        --     highlight.fg = palette.cyan_two
        -- end
    end,
})

vim.cmd("colorscheme flexoki")
-- vim.cmd("colorscheme flexoki-moon")
-- vim.cmd("colorscheme flexoki-dawn")
```

> [!NOTE]
> Visit the [wiki](https://github.com/nuvic/flexoki-nvim/wiki) for issues with plugins.

## Supported plugins

Flexoki includes highlight definitions for the following plugins:

| Plugin | Highlights |
|---|---|
| [alpha-nvim](https://github.com/goolord/alpha-nvim) | DashboardHeader, DashboardCenter, DashboardFooter, DashboardShortcut |
| [avante.nvim](https://github.com/yetone/avante.nvim) | AvanteTitle, AvanteSubtitle, AvanteThirdTitle, reversed variants |
| [barbar.nvim](https://github.com/romgrk/barbar.nvim) | BufferCurrent, BufferInactive, BufferVisible, BufferTabpageFill |
| [copilot.vim](https://github.com/github/copilot.vim) | CopilotSuggestion |
| [dashboard-nvim](https://github.com/glepnir/dashboard-nvim) | DashboardHeader, DashboardCenter, DashboardFooter, DashboardShortcut |
| [diffview.nvim](https://github.com/sindrets/diffview.nvim) | DiffViewDiffAdd, DiffViewDiffDelete, DiffViewDiffChange, DiffViewDiffText |
| [flash.nvim](https://github.com/folke/flash.nvim) | FlashLabel |
| [fzf-lua](https://github.com/ibhagwan/fzf-lua) | FzfLuaBorder, FzfLuaNormal, FzfLuaTitle, FzfLuaCursorLine and more |
| [gitsigns.nvim](https://github.com/lewis6991/gitsigns.nvim) | GitSignsAdd/Change/Delete, inline variants, SignColumn |
| [grug-far.nvim](https://github.com/MagicDuck/grug-far.nvim) | GrugFarHelpHeader, GrugFarResultsMatch, GrugFarResultsPath and more |
| [hop.nvim](https://github.com/phaazon/hop.nvim) | HopNextKey, HopNextKey1, HopNextKey2, HopUnmatched |
| [indent-blankline.nvim](https://github.com/lukas-reineke/indent-blankline.nvim) | IblIndent, IblScope, IblWhitespace (modern + legacy) |
| [lazy.nvim](https://github.com/folke/lazy.nvim) | LazyNormal, LazyButton, LazyCommit, LazyH1, LazyH2, LazyUrl and more |
| [leap.nvim](https://github.com/ggandor/leap.nvim) | LeapLabelPrimary, LeapLabelSecondary, LeapMatch |
| [lsp_signature.nvim](https://github.com/ray-x/lsp_signature.nvim) | LspSignatureActiveParameter |
| [lspsaga.nvim](https://github.com/tami5/lspsaga.nvim) | LspSagaCodeAction*, LspSagaDiagnostic*, LspSagaHover*, SagaShadow and more |
| [mason.nvim](https://github.com/williamboman/mason.nvim) | MasonHeader, MasonNormal, MasonHighlight, MasonMuted and more |
| [mini.nvim](https://github.com/echasnovski/mini.nvim) | Full support: MiniStatusline, MiniFiles, MiniPick, MiniStarter, MiniDiff, MiniNotify, MiniTabline, MiniClue, MiniJump, MiniMap and more |
| [modes.nvim](https://github.com/mvllow/modes.nvim) | ModesCopy, ModesDelete, ModesInsert, ModesReplace, ModesVisual |
| [neo-tree.nvim](https://github.com/nvim-neo-tree/neo-tree.nvim) | NeoTreeGit*, NeoTreeTab*, NeoTreeTitleBar |
| [neogit](https://github.com/NeogitOrg/neogit) | NeogitChange*, NeogitDiff*, NeogitFilePath, NeogitHunkHeader |
| [neorg](https://github.com/nvim-neorg/neorg) | NeorgHeading*Prefix, NeorgHeading*Title, NeorgMarkerTitle |
| [neotest](https://github.com/nvim-neotest/neotest) | NeotestPassed, NeotestFailed, NeotestRunning, NeotestSkipped, NeotestFocused and more |
| [noice.nvim](https://github.com/folke/noice.nvim) | NoiceCursor |
| [nvim-cmp](https://github.com/hrsh7th/nvim-cmp) | CmpItemAbbr*, CmpItemKind*, CmpItemAbbrMatch |
| [nvim-dap-ui](https://github.com/rcarriga/nvim-dap-ui) | DapUIBreakpoints*, DapUIFloatBorder, DapUIThread, DapUIScope, DapUIVariable and more |
| [nvim-navic](https://github.com/SmiteshP/nvim-navic) | NavicIcons* (27 icon types), NavicSeparator, NavicText |
| [nvim-notify](https://github.com/rcarriga/nvim-notify) | NotifyERROR/INFO/WARN/DEBUG/TRACE borders, icons, titles |
| [nvim-tree.lua](https://github.com/kyazdani42/nvim-tree.lua) | NvimTreeFolder*, NvimTreeGit*, NvimTreeOpenedFile, NvimTreeRootFolder and more |
| [nvim-treesitter-context](https://github.com/nvim-treesitter/nvim-treesitter-context) | TreesitterContext, TreesitterContextLineNumber |
| [pounce.nvim](https://github.com/rlane/pounce.nvim) | PounceAccept, PounceAcceptBest, PounceGap, PounceMatch |
| [rainbow-delimiters.nvim](https://github.com/HiPhish/rainbow-delimiters.nvim) | 7 delimiters colors (RainbowDelimiter*) |
| [render-markdown.nvim](https://github.com/MeanderingProgrammer/render-markdown.nvim) | RenderMarkdownBullet, RenderMarkdownH*Bg, RenderMarkdownQuote, RenderMarkdownCode and more |
| [snacks.nvim](https://github.com/folke/snacks.nvim) | SnacksDashboard*, SnacksPicker*, SnacksNotifier*, SnacksIndent*, SnacksWords |
| [telescope.nvim](https://github.com/nvim-telescope/telescope.nvim) | TelescopeBorder, TelescopeMatching, TelescopeNormal, TelescopeSelection, TelescopeTitle and more |
| [todo-comments.nvim](https://github.com/folke/todo-comments.nvim) | TodoBg/Fg/Sign for TODO, WARN, HACK, FIX, NOTE, PERF, TEST |
| [toggleterm.nvim](https://github.com/akinsho/toggleterm.nvim) | Terminal window highlights (via plugin module) |
| [trouble.nvim](https://github.com/folke/trouble.nvim) | TroubleNormal, TroubleText, TroubleSource, TroubleCount, TroubleFolder, TroubleIndent and more |
| [vim-illuminate](https://github.com/RRethy/vim-illuminate) | IlluminatedWordRead, IlluminatedWordText, IlluminatedWordWrite |
| [vimwiki](https://github.com/vimwiki/vimwiki) | VimwikiHeader1-6, VimwikiLink, VimwikiList, VimwikiNoExistsLink |
| [which-key.nvim](https://github.com/folke/which-key.nvim) | WhichKey, WhichKeyBorder, WhichKeyFloat, WhichKeyGroup, WhichKeyTitle and more |
| [incline.nvim](https://github.com/b0o/incline.nvim) | InclineNormal, InclineNormalNC |
| [bufferline.nvim](https://github.com/akinsho/bufferline.nvim) | Tab and buffer highlights (via plugin module) |
| [obsidian.nvim](https://github.com/epwalsh/obsidian.nvim) | Bullet, reference, and done markers (via plugin module) |
| [galaxyline.nvim](https://github.com/NTBBloodbath/galaxyline.nvim) | Statusline color mapping (via plugin module) |
| [markid](https://github.com/David-Kunz/markid) | Accent colors for markers (via plugin module) |

## Lualine themes

Flexoki provides two standalone themes for [lualine.nvim](https://github.com/nvim-lualine/lualine.nvim):

```lua
require("lualine").setup({
    options = {
        theme = require("lualine.themes.flexoki"),
        -- or for the alternative theme:
        -- theme = require("lualine.themes.flexoki-alt"),
    },
})
```

- **flexoki** -- Mode-colored statusline (blue for normal, yellow for insert, purple for visual, red for replace, orange for command)
- **flexoki-alt** -- Alternative theme using `surface` background for sections with per-mode accents

## Plugin modules

Highlight configurations for plugins that require manual setup are available under `lua/flexoki/plugins/`:

- `require("flexoki.plugins.bufferline")` -- Highlight definitions for [bufferline.nvim](https://github.com/akinsho/bufferline.nvim)
- `require("flexoki.plugins.toggleterm")` -- Terminal window highlights for [toggleterm.nvim](https://github.com/akinsho/toggleterm.nvim)
- `require("flexoki.plugins.obsidian")` -- Bullet and marker highlights for [obsidian.nvim](https://github.com/epwalsh/obsidian.nvim)
- `require("flexoki.plugins.galaxyline")` -- Color mapping for [galaxyline.nvim](https://github.com/NTBBloodbath/galaxyline.nvim)
- `require("flexoki.plugins.markid")` -- Accent color list for [markid](https://github.com/David-Kunz/markid)

## Contributing

We welcome and appreciate contributions of any kind. Create an issue or start a discussion for any proposed changes. Pull requests are encouraged for supporting additional plugins or [treesitter improvements](https://github.com/nvim-treesitter/nvim-treesitter/blob/master/CONTRIBUTING.md#highlights).

Feel free to update the [wiki](https://github.com/nuvic/flexoki-nvim/wiki/) with any recipes.
