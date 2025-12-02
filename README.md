# Laptop

A script to set up a macOS environment for web development.

This is a personal fork focused on CLI tools only. Shell configuration is managed separately via [chezmoi](https://chezmoi.io/).

The script is idempotent: It can run multiple times on the same machine safely.
It installs, upgrades, or skips packages based on what is already installed.

## Requirements

- macOS Sonoma (14.4) or higher
- Apple Silicon or Intel

## Install

Download, review, then execute the script:

```bash
curl --remote-name https://raw.githubusercontent.com/jacobpatton/laptop/master/mac
less mac
bash mac 2>&1 | tee ~/laptop.log
```

Choose additional packages when prompted:

```text
Do you want to install Web's dependencies? [y|N]
```

## What it sets up

### Default

Source Code versioning:

- [git] distributed revision control system
- [Git Large File Storage] an open-source Git extension for versioning large files
- [Github CLI] GitHub's official command line tool

[git]: https://git-scm.com
[github cli]: https://github.com/cli/cli
[git large file storage]: https://git-lfs.github.com/

Utilities:

- [1password-cli] CLI for 1Password
- [coreutils] GNU File, Shell, and Text utilities
- [fzf] fuzzy finder
- [gpg] GNU Pretty Good Privacy (PGP) package
- [GPG Suite] GPG GUI tools
- [Homebrew] for managing operating system libraries
- [libyaml] YAML Parser
- [poppler] PDF utilities
- [the_silver_searcher] fast code search (ag)
- [tmux] terminal multiplexer
- [reattach-to-user-namespace] tmux clipboard fix
- [universal-ctags] for code navigation
- [watchman] file watcher
- [Zsh] as your shell
- [chezmoi] dotfile management (auto-bootstraps from GitHub)

Databases:

- [PostgreSQL] relational database
- [pgvector] vector similarity search for PostgreSQL
- [Redis] key-value store

Version Control:

- [Jujutsu] Git-compatible VCS with better UX

Build Dependencies:

- [Rust] required for some Ruby gems (tiktoken_ruby)

[1password-cli]: https://developer.1password.com/docs/cli/
[chezmoi]: https://chezmoi.io/
[coreutils]: https://www.gnu.org/software/coreutils
[fzf]: https://github.com/junegunn/fzf
[gpg suite]: https://gpgtools.org/
[poppler]: https://poppler.freedesktop.org/
[postgresql]: https://www.postgresql.org/
[pgvector]: https://github.com/pgvector/pgvector
[redis]: https://redis.io/
[jujutsu]: https://github.com/martinvonz/jj
[rust]: https://www.rust-lang.org/
[the_silver_searcher]: https://github.com/ggreer/the_silver_searcher
[tmux]: https://github.com/tmux/tmux
[reattach-to-user-namespace]: https://github.com/ChrisJohnsen/tmux-MacOSX-pasteboard
[watchman]: https://facebook.github.io/watchman/
[gpg]: https://gnupg.org/
[homebrew]: https://brew.sh/
[libyaml]: https://github.com/yaml/libyaml
[universal-ctags]: https://ctags.io/
[zsh]: https://www.zsh.org/

Browser:

- [Ungoogled Chromium] privacy-focused Chromium without Google integration

[ungoogled chromium]: https://ungoogled-software.github.io/ungoogled-chromium-binaries/

Terminal:

- [WezTerm] GPU-accelerated terminal emulator

[wezterm]: https://wezfurlong.org/wezterm/

Automation:

- [Hammerspoon] macOS automation with Lua scripting
- [Karabiner-Elements] keyboard customization
- [Espanso] cross-platform text expander

[hammerspoon]: https://www.hammerspoon.org/
[karabiner-elements]: https://karabiner-elements.pqrs.org/
[espanso]: https://espanso.org/

Productivity:

- [Rectangle] window management
- [Alfred] launcher and productivity app
- [BetterTouchTool] trackpad/keyboard customization
- [Keyboard Maestro] macro automation (manual install: [v10.2](https://files.stairways.com/keyboardmaestro-102.zip))
- [Freedom] distraction blocker

[rectangle]: https://rectangleapp.com/
[alfred]: https://www.alfredapp.com/
[bettertouchtool]: https://folivora.ai/
[keyboard maestro]: https://www.keyboardmaestro.com/
[freedom]: https://freedom.to/

Utilities:

- [Parachute] virtual desktops/spaces manager (manual install: [Mac App Store](https://apps.apple.com/app/parachute/id1436650069))
- [CleanShot X] screenshot and screen recording
- [Tailscale] mesh VPN
- [SoundSource] audio routing and control
- [Ice] menu bar management

[cleanshot x]: https://cleanshot.com/
[tailscale]: https://tailscale.com/
[soundsource]: https://rogueamoeba.com/soundsource/
[ice]: https://icemenubar.app/

### Web

Tools:

- [ImageMagick] for cropping and resizing images
- [Yarn] JavaScript package manager
- [libpq] PostgreSQL client library

[imagemagick]: https://www.imagemagick.org/
[yarn]: https://yarnpkg.com/
[libpq]: https://www.postgresql.org/docs/current/libpq.html

Command Line Interfaces:

- [AWS CLI] official Amazon AWS command-line interface
- [Heroku CLI] for interacting with the Heroku API
- [Phrase CLI] for interacting with the Phrase API

[heroku cli]: https://toolbelt.heroku.com/
[aws cli]: https://aws.amazon.com/cli/
[phrase cli]: https://phrase.com/cli/

Languages via [mise]:

- [Go] programming language to build simple/reliable/efficient software
- [Nodejs] JavaScript runtime environment
- [Ruby] dynamic, open-source programming language with a focus on simplicity and productivity

[mise]: https://mise.jdx.dev/
[go]: https://golang.org
[nodejs]: https://nodejs.org/
[ruby]: https://www.ruby-lang.org/en/

## Customize in `~/.laptop.local`

Your `~/.laptop.local` is run at the end of the Laptop script.
Put your customizations there.
For example:

```sh
#!/bin/sh

cask "dropbox"
cask "firefox"

brew "tree"
```

Write your customizations such that they can be run safely more than once.
See the `mac` script for examples.

## Debugging

Your last Laptop run will be saved to `~/laptop.log`.
Read through it to see if you can debug the issue yourself.

## Contributing

Edit the `mac` file.
Document in the `README.md` file.
Follow shell style guidelines by using [ShellCheck].

```sh
brew install shellcheck
```

[shellcheck]: https://www.shellcheck.net/about.html

## License

It is free software,
and may be redistributed under the terms specified in the [LICENSE] file.

[license]: LICENSE

## Credits

Inspired by [thoughtbot/laptop](https://github.com/thoughtbot/laptop) and [nimblehq/laptop](https://github.com/nimblehq/laptop).
