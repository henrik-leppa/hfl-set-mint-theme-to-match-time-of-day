HFL Set Mint Theme To Match Time Of Day 1.0.0
=============================================

[ Encoding: UTF-8; Syntax: GitHub Flavored Markdown ]:#

Sets the Mint theme (dark or light) based on the current time of day, written by
Henrik Franciscus Leppä (HFL).


[MIT License][]
---------------


[Changelog][]
-------------


Prerequisites
-------------

- Linux Mint
  - (However, this script can be modified to change the theme of any system that
    has the `gsettings` command.)
- `at` command
  - (Only for continuous mode)

**Note:** The script will check for the required commands itself, so you do not
have to.


Usage
-----

```sh
hfl-set-mint-theme-to-match-time-of-day
```
or:
```sh
hfl-set-mint-theme-to-match-time-of-day --continuous [ <at_queue>=s ]
```
or:
```sh
hfl-set-mint-theme-to-match-time-of-day (--help | -H | -h | -?)
```
or:
```sh
hfl-set-mint-theme-to-match-time-of-day (--version | -V | -v)
```

### Options

- `--version, -V, -v`
  - Print version and copyright information.
- `--help, -H, -h, -?`
  - Print the usage message.
- `--continuous`
  - Sets up a recursive `at` job that runs the command when the time of day
    changes. `<at_queue>` specifies which `at` queue to use; if not given,
    defaults to 's'. This queue needs to be used exclusively for this script.

### Notes

- To make this program run continuously from startup, add it to the "Startup
  Applications" with the `--continuous` flag and a delay shorter than the delay
  of any application with visual elements, such as windows or tray icons.
- Theme does not update to some applications and system utilities without
  restarting the program or logging out and logging back in.
- When run in continuous mode, this script logs output and errors to:
  ```sh
  ~/hfl-set-mint-theme-to-match-time-of-day.log
  ```
- This script use `at` instead of `cron` because `gsettings` does not work with
  `cron`.


Testing
-------

Automated tests are done using [shUnit2][] and [ShellCheck][].

### Steps

1. Install ShellCheck 0.7.0.
2. Run:
   ```sh
   ./test
   ```


[Changelog]: ./CHANGELOG.md
[MIT License]: ./LICENSE.md
[ShellCheck]: https://github.com/koalaman/shellcheck
[shUnit2]: https://github.com/kward/shunit2
