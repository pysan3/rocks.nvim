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

> [!NOTE]
> The following plugin is perfectly usable,
> but its user interfaces are a **work in progress**.
>
> They will be fledged out soon! :)

## :star2: Features

- `Cargo`-like `rocks.toml` file for declaring all your plugins.
- Name-based installation
  (` "nvim-neorg/neorg" ` becomes `:Rocks install neorg` instead).
- Automatic dependency and build script management.
- True semver versioning!
- (WIP) Automatic running of test suites.

## :pencil: Requirements

- An up-to-date `Neovim` nightly (>= 0.10) installation.
- The `git` command line utility.
- `wget` or `curl` (if running on a UNIX system) - required for the remote `:source` command to work.

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
:source https://raw.githubusercontent.com/nvim-neorocks/rocks.nvim/installer/installer.lua
```

> [!IMPORTANT]
>
> For security reasons, we recommend that you read `:help :source`
> and the installer code before running it so you know exactly what it does.

## :books: Usage

TODO...

## :book: License

rocks.nvim is licensed under GPLv3.
