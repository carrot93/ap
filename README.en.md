# ap --`auto-pager`

ap is a shell utility that allows the output of other shell commands to automatically enter interactive page-flipping mode.

ap consists of two parts, a binary program written in Go that captures the output of commands and supports page-flipping, and a set of shell scripts that create a wrapper with the same name for a user-specified list of commands.

The usage of the commands after wrap is the same as before, and should not change the user's habits or cause any problems.

Read this in other languages:[English](README.en.md),[Simplified Chinese](README.md),[traditional Chinese](README.zh-TW.md),[Arabic](README.ar.md),[French](README.fr.md),[Hindi](README.hi.md)

ap is a shell tool that enables the output of other shell commands to automatically enter the interactive page-turning mode.

ap consists of two parts, a binary program written in Go language, responsible for capturing the output of the command and supporting page turning,
and a set of shell scripts responsible for creating wrappers of the same name for user-specified command listings.

The usage of the command after wrap is the same as before, and the user's operating habits should not be changed, and it will not cause trouble to the user.

## Install

    go install github.com/flw-cn/ap@master

## configuration

-   `bash`(#bash)
-   `fish`(#`fish`)
-   `zsh`(#`zsh`)

### bash

At your`~/.bashrc`Add the following to it:

```sh
eval "$(ap --bash)"
```

ap wraps a batch of commands by default. If you are not satisfied, you can re-customize through environment variables:

```sh
AUTO_PAGER_CMDS=(go cargo make)
eval "$(ap --bash)"
```

Or just add new commands on top of the default list:

```sh
AUTO_PAGER_CMDS_EXTRA=(ps last)
eval "$(ap --bash)"
```

In addition, ap can also be used with[grc](https://github.com/garabik/grc)Working together, grc can be installed using Homebrew under macOS:

```sh
brew install grc
```

ap + grc wraps a batch of commands by default. If you are not satisfied, you can re-customize through environment variables:

```sh
AUTO_PAGER_CMDS_WITH_GRC=(ps last dig diff)
eval "$(ap --bash)"
```

Or just add new commands on top of the default list:

```sh
AUTO_PAGER_CMDS_WITH_GRC_EXTRA=(ps last)
eval "$(ap --bash)"
```

Additionally, the environment variable`$AUTO_PAGER_MIN_HEIGHT`You can control the minimum number of rows to start paging with:

```sh
AUTO_PAGER_MIN_HEIGHT=30        # 输出超过 30 行时才开始分页
eval "$(ap --bash)"
```

If configured as a negative number, it represents a percentage of the height of the terminal window:

```sh
AUTO_PAGER_MIN_HEIGHT='-50'     # 输出超过终端窗口高度的 50% 时才开始分页
eval "$(ap --bash)"
```

if not specified`AUTO_PAGER_MIN_HEIGHT`,The default is`-80`,Right now`80%`。

### `fish`

At your`~/.config/fish/config.fish`Add the following to it:

```sh
ap --fish | source
```

ap wraps a batch of commands by default. If you are not satisfied, you can re-customize through environment variables:

```sh
set AUTO_PAGER_CMDS go cargo make
ap --fish | source
```

Or just add new commands on top of the default list:

```sh
set AUTO_PAGER_CMDS_EXTRA ps last
ap --fish | source
```

In addition, ap can also be used with[grc](https://github.com/garabik/grc)Working together, grc can be installed using Homebrew under macOS:

```sh
brew install grc
```

ap + grc wraps a batch of commands by default. If you are not satisfied, you can re-customize through environment variables:

```sh
set AUTO_PAGER_CMDS_WITH_GRC ps last dig diff
ap --fish | source
```

Or just add new commands on top of the default list:

```sh
set AUTO_PAGER_CMDS_WITH_GRC_EXTRA ps last
ap --fish | source
```

Additionally, the environment variable`$AUTO_PAGER_MIN_HEIGHT`You can control the minimum number of rows to start paging with:

```sh
set AUTO_PAGER_MIN_HEIGHT 30        # 输出超过 30 行时才开始分页
ap --fish | source
```

If configured as a negative number, it represents a percentage of the height of the terminal window:

```sh
set AUTO_PAGER_MIN_HEIGHT -50     # 输出超过终端窗口高度的 50% 时才开始分页
ap --fish | source
```

if not specified`AUTO_PAGER_MIN_HEIGHT`,The default is`-80`,Right now`80%`。

### `zsh`

At your`~/.zshrc`Add the following to it:

```sh
eval "$(ap --zsh)"
```

ap wraps a batch of commands by default. If you are not satisfied, you can re-customize through environment variables:

```sh
AUTO_PAGER_CMDS=(go cargo make)
eval "$(ap --zsh)"
```

Or just add new commands on top of the default list:

```sh
AUTO_PAGER_CMDS_EXTRA=(ps last)
eval "$(ap --zsh)"
```

In addition, ap can also be used with[grc](https://github.com/garabik/grc)Working together, grc can be installed using Homebrew under macOS:

```sh
brew install grc
```

ap + grc wraps a batch of commands by default. If you are not satisfied, you can re-customize through environment variables:

```sh
AUTO_PAGER_CMDS_WITH_GRC=(ps last dig diff)
eval "$(ap --zsh)"
```

Or just add new commands on top of the default list:

```sh
AUTO_PAGER_CMDS_WITH_GRC_EXTRA=(ps last)
eval "$(ap --zsh)"
```

Additionally, the environment variable`$AUTO_PAGER_MIN_HEIGHT`You can control the minimum number of rows to start paging with:

```sh
AUTO_PAGER_MIN_HEIGHT=30        # 输出超过 30 行时才开始分页
eval "$(ap --zsh)"
```

If configured as a negative number, it represents a percentage of the height of the terminal window:

```sh
AUTO_PAGER_MIN_HEIGHT='-50'     # 输出超过终端窗口高度的 50% 时才开始分页
eval "$(ap --zsh)"
```

if not specified`AUTO_PAGER_MIN_HEIGHT`,The default is`-80`,Right now`80%`。

## use

Commands that have been ap wrapped just need to be used as usual.
If there is too much output, the environment variable will be called automatically`$PAGER`The specified pager performs pagination.

if your`$PAGER`Variables are special and cannot be adapted to ap, you can also use environment variables`$AP_PAGER`Set pager individually for ap.

if`$AP_PAGER`and`$PAGER`Neither is specified, then the`less -Fr`。

The following conditions will not start the pager:

-   When the output content is too small, see`$AUTO_PAGER_MIN_HEIGHT`。
-   When ap detects that the command output contains`ESC [?1049h`sequence, the command is judged to be a full-screen application at this time.
-   When the command has not completed execution. The pager will not start until the command execution is complete.
    -   `ping`and`tcpdump`Such commands need to be pressed first`Ctrl-C`Paging does not start until the command is terminated.
    -   `python`and`gdb`Such commands need to wait for the command to exit before starting paging.

## common problem

-   Will it affect the colored output of the command?
    -   Won't.
-   Does a command that detects a terminal and provides different output for terminal and non-terminal modes change its output?
    -   Won't.
-   How do I diagnose if I suspect that ap is affecting the output of a command?
    -   you can use it`command foo`to execute`foo`, so that ap is not called.
-   If I habitually add after the ap command`| less`, will something go wrong?
    -   Won't.
-   Can an ap command also redirect its output?
    -   Can.
-   Will autocompletion of ap'd commands be broken?
    -   Won't.
-   ap support like`python`、`gdb`Such an interactive application?
    -   support. However, since these applications output some control characters, the content you see after pagination may be a bit messy.
-   ap support like`htop`、`vim`Such a full screen application?
    -   How to put it, it can't go wrong anyway, but I can't figure out what is the practical point of pairing ap with them.
