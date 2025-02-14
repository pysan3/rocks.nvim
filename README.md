<!-- markdownlint-disable -->
<br />
<div align="center">
  <a href="https://github.com/nvim-neorocks/rocks.nvim">
    <img src="./rocks-header.svg" alt="rocks.nvim">
  </a>
  <p align="center">
    <br />
    <a href="./doc/rocks.txt"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/nvim-neorocks/rocks.nvim/issues/new?assignees=&labels=bug">Report Bug</a>
    ·
    <a href="https://github.com/nvim-neorocks/rocks.nvim/issues/new?assignees=&labels=enhancement">Request Feature</a>
    ·
    <a href="https://github.com/nvim-neorocks/rocks.nvim/discussions/new?category=q-a">Ask Question</a>
  </p>
  <p>
    <strong>
      A modern approach to <a href="https://neovim.io/">Neovim</a> plugin management!
    </strong>
  </p>
  <p>🌒</p>
</div>
<!-- markdownlint-restore -->

## :star2: Features

- `Cargo`-like `rocks.toml` file for declaring all your plugins.
- Name-based installation
  (` "nvim-neorg/neorg" ` becomes `:Rocks install neorg` instead).
- Automatic dependency and build script management.
- True semver versioning!
- Minimal, non-intrusive UI.
- Async execution.
- Extensible, with a Lua API.
- Command completions for plugins on luarocks.org.

![demo](https://github.com/nvim-neorocks/rocks.nvim/assets/12857160/955c3ae7-c916-4a70-8fbd-4e28b7f0d77e)

## :pencil: Requirements

- An up-to-date `Neovim` nightly (>= 0.10) installation.
- The `git` command line utility.
- `wget` or `curl` (if running on a UNIX system) - required for the remote `:source` command to work.
- `netrw` enabled in your Neovim configuration - enabled by default but some configurations manually disable the plugin.

> [!IMPORTANT]
> If you are running on Windows or an esoteric architecture, `rocks.nvim` will
> attempt to compile its dependencies instead of pulling a prebuilt binary. For
> the process to succeed you must have a **C++17 parser** and **Rust
> toolchain** installed on your system.

## :hammer: Installation

### :zap: Installation script (recommended)

The days of bootstrapping and editing your configuration are over.
`rocks.nvim` can be installed directly through an interactive installer within Neovim.

You just have to run the following command inside your editor
and the installer will do the rest!

```vim
:source https://raw.githubusercontent.com/nvim-neorocks/rocks.nvim/master/installer.lua
```

If you already have plugins installed, we suggest running the installer
without loading RC files, as some plugins may interfere with the script:

```sh
nvim -u NORC -c "source https://raw.githubusercontent.com/nvim-neorocks/rocks.nvim/master/installer.lua"
```

> [!IMPORTANT]
>
> For security reasons, we recommend that you read `:help :source`
> and the installer code before running it so you know exactly what it does.

## :books: Usage

### Installing rocks

You can install rocks with the `:Rocks install {rock} {version?}` command.

Arguments:

- `rock`: The luarocks package.
- `version`: Optional. Used to pin a rock to a specific version.

> [!NOTE]
>
> - The command provides fuzzy completions for rocks and versions on luarocks.org.
> - Installs the latest version if `version` is omitted.
> - This plugin keeps track of installed plugins in a `rocks.toml` file,
>   which you can commit to version control.

### Updating rocks

Running the `:Rocks update` command will attempt to update every available rock
if it is not pinned.

### Syncing rocks

The `:Rocks sync` command synchronizes the installed rocks with the `rocks.toml`.

> [!NOTE]
>
> - Installs missing rocks.
> - Ensures that the correct versions are installed.
> - Uninstalls unneeded rocks.

### Uninstalling rocks

To uninstall a rock and any of its dependencies,
that are no longer needed, run the `:Rocks prune {rock}` command.

> [!NOTE]
>
> - The command provides fuzzy completions for rocks that can safely
>   be pruned without breaking dependencies.

### Editing `rocks.toml`

The `:Rocks edit` command opens the `rocks.toml` file for manual editing.
Make sure to run `:Rocks sync` when you are done.

### Lazy loading plugins

By default, `rocks.nvim` will source all plugins at startup.
To prevent it from sourcing a plugin, you can specify `opt = true`
in the `rocks.toml` file.

For example:

```toml
[plugins]
neorg = { version = "1.0.0", opt = true }
```

or

```toml
[plugins.neorg]
version = "1.0.0"
opt = true
```

You can then load the plugin with the `:Rocks[!] packadd {rock}` command.

> [!NOTE]
>
> A note on loading rocks:
>
> Luarocks packages are installed differently than you are used to
> from Git repositories.
>
> Specifically, `luarocks` installs a rock's Lua API to the [`package.path`](https://neovim.io/doc/user/luaref.html#package.path)
> and the [`package.cpath`](https://neovim.io/doc/user/luaref.html#package.cpath).
> It does not have to be added to Neovim's runtime path
> (e.g. using `:Rocks packadd`), for it to become available.
> This does not impact Neovim's startup time.
>
> Runtime directories ([`:h runtimepath`](https://neovim.io/doc/user/options.html#'runtimepath')),
> on the other hand, are installed to a separate location.
> Plugins that utilise these directories may impact startup time
> (if it has `ftdetect` or `plugin` scripts), so you may or may
> not benefit from loading them lazily.

## :stethoscope: Troubleshooting

The `:Rocks log` command opens a log file for the current session,
which contains the `luarocks` stderr output, among other logs.

## :package: Extending `rocks.nvim`

This plugin provides a Lua API for extensibility.
See [`:h rocks.api`](./doc/rocks.txt) for details.

Following are some examples:

- [`rocks-git.nvim`](https://github.com/nvim-neorocks/rocks-git.nvim):
  Adds the ability to install plugins from git.
- [`rocks-config.nvim`](https://github.com/nvim-neorocks/rocks-config.nvim):
  Adds an API for safely loading plugin configurations.

To extend `rocks.nvim`, simply install a module with `:Rocks install`,
and you're good to go!

## :book: License

`rocks.nvim` is licensed under [GPLv3](./LICENSE).

## :green_heart: Contributing

Contributions are more than welcome!
See [CONTRIBUTING.md](./CONTRIBUTING.md) for a guide.
