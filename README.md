# a fork of `asdf-zig` for supporting custom versions

## why

The official `asdf-zig` can only support what versions are listed at `https://ziglang.org/download/index.json`, which are all versions either official or cutting-edge master. But as we know `zig` is evolving fast, sometime I need to stick with a specific version for a while, like `0.12.0-dev.2139+e025ad7b4`. This is easy job if just download it and make it available to my path. But if there are multiple projects using different custom zig version, manual changing will be tedious.

So I start to miss `asdf`, the one shop for managing many different new language runtimes, and luckily there is `asdf-zig`, but unluckily it supports no custom versions.

So I just make my fork and adjust it a bit for my usage.

## how it works

essentially my fork replaces the official `asdf-zig`. To install it, need to remove the old one, just

```bash
asdf plugin remove asdf-zig
asdf plugin add zig https://github.com/liyu1981/asdf-zig.git
```

will replace your version with mine :)

then create a custom version file like below in `~/.asdf/custom/zig`

```bash
mkdir -p ~/.asdf/custom/zig
echo "{\"0.12.0-dev.2139+e025ad7b4\": {}}" > ~/.asdf/custom/zig/versions.json
```

and after that you will find your custom version is available in `asdf` commands. See this demo video for how I use it in life

<img src="https://github.com/liyu1981/asdf-zig/blob/asdf-zig-custom-version/demo_video/asdf-zig-custom.gif?raw=true" alt="demo gif for asdf-zig with custom versions" width="480px" />

## what's the format for `~/.asdf/custom/zig/versions.json`

currently it is just naive :)

```json
{
  "0.12.0-dev.2139+e025ad7b4": {},
  "0.12.0-dev.1828+225fe6ddb": {},
  "<more zig dev versions>": {}
}
```

you get the idea, only the `key` part is relevant, the `value` part is not, so I just keep a simple '{}' to fool the underlying json parser (from original `asdf-zig`).

I hope this helps!

# original `asdf-zig` README.md

# asdf-zig

[Zig](https://ziglang.org) plugin for asdf version manager

## Build History

[![Build history](https://buildstats.info/github/chart/asdf-community/asdf-zig?branch=master)](https://github.com/asdf-community/asdf-zig/actions)

## Installation

```bash
asdf plugin-add zig https://github.com/asdf-community/asdf-zig.git
```

## Usage

Check [asdf](https://github.com/asdf-vm/asdf) readme for instructions on how to
install & manage versions.

## License

Licensed under the
[Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0).
