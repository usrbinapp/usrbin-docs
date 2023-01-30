# Intro to usrbin.app

Usrbin is an SDK that adds version checking and in-place upgrades to CLIs and other executables. This intro document covers what usrbin offers today.

## Upgrade checks

Most CLIs today have a `version` command (or a `--version` flag). This command will print the version, which is normally injected into the source code at build time in CI. It's great to show the user which version of the CLI they are running, but this is often needed to determine if there's an upgrade available. What if the `version` command also was able to tell the user that there's a new version available?

Usrbin uses [updaters](./updaters) to check the Releases in your public GitHub repo, and look for the latest release. If the [semver](https://semver.org) tag is greater than the version that the user is running, the usrbin SDK will return the latest version information to your CLI. You can display this, or do whatever you'd like with this information to help the user know that there's an upgrade available.

## In place upgrade

Determining if there's an upgrade available is only part of the problem. Usrbin can also perform an in-place upgrade for you CLI. That means that you can have an `upgrade` (or `version upgrade`, or whatever you'd like) command that will download and verify the latest version of your CLI and perform an in-place upgrade of the CLI. You don't need to ship a second utility or any shenanigans to figure out how to replace the currently running executable -- usrbin handles that all.

Usrbin is aware of popular [package managers](./package-managers). If your CLI was installed from one of the known package managers, usrbin won't attempt to upgrade it. Instead, usrbin will print a command showing the user how to use the package manager to upgrade.

## Current status

Currently, usrbin is still pretty early. We have support for single binary CLIs, written in Go, distributed via GitHub releases. If you are interested in usrbin, but don't distribute your CLI in that format, please [open an issue](https://github.com/usrbinapp/usrbin) in our repo so we know!

To get started, you can [read about the concepts](./concepts/), or if you already understand them, head over to the [installation](./install/) page.
