# Go SDK

The usrbin Go SDK is designed to be integrated quickly into any single-binary CLI that's written in Go.

## Prerequisites

- The CLI must be written in Go
- The CLI must be compiled into a single binary
- The CLI releases must be published to a GitHub release page
- The versions must be [semver](https://semver.org) compliant.

## Preparing

What do you need do before starting? You have to bring a plan -- where do you want it integrated? If you are stuck thinking, here's some inspiration:

### `version` and `version upgrade`

```
% my-ctl version
my-ctl version v1.0.1
There's an update available. The latest version is v1.0.2.

$ my-ctl version upgrade
Downloading my-ctl v1.0.2.
Performing in-place upgrade.
Upgrade complete.
```

## Installing

```
go get github.com/usrbinsdk/usrbin/go
```

## Initializing

Somewhere, in your code (probably in the version CLI handler)

```
usrbinsdk, err := usrbin.New(
	version,
	usrbin.UsingGitHubUpdateChecker("github.com/<org>/<repo>"),
)
```

### Supported options

#### `UsingGitHubUpdateChecker`

When provided, this will be the source used for checking for updates. Usrbin will query the latest release tag on this repo, and (assuming it's semver compliant), compare it with the current version. If the latest release is newer, the usrbin SDK will return information about this release to your code.

#### `UsingHomebrewFormula`

When provided, this will link your integration to a homebrew formula. This is necessary for usrbin to detect if your binary was installed on the machine using brew. Without this, usrbin will overwrite versions of your binary that were installed by Homebrew.

## Functions

The following functions are exported from the Go SDK.

### `GetUpdateInfo`

The `GetUpdateInfo` function will return the information about any available update, if one exists. It returns `nil` if there is no update available, or an error if something unexpected happened or the SDK wasn't able to check.

Example:

```
func PrintVersion() {
    currentVersion := "v1.0.0"

    usrbinsdk, err := usrbin.New(
	    currentVersion,
	    usrbin.UsingGitHubUpdateChecker("github.com/my-org/my-repo"),
    )

    updateInfo, err = usrbinsdk.GetUpdateInfo()
    if err != nil {
        fmt.Printf("Error getting update info: %s", err)
    }
    
    fmt.Printf("Current version: %s\n", currentVersion)
    if userInfo != nil {
        fmt.Printf("Update available. Version %s is available to install.\n", updateInfo.LatestVersion)
    }
}
```

### `CanSupportUpgrade`

The `CanSupportUpgrade` function returns a `bool`, indicating if the current system and installation will support
in-place upgrades by usrbin. This will return `false` when the current installation is suspected of being managed 
by a supported [package manager](../package-managers)

### `ExternalUpgradeCommand`

The `ExternalUpgradeCommand` will return a string with the best guess at the package manager command that should 
be executed to upgrade, when the current installation is managed by a package manager.

### `Upgrade`

The `Upgrade` command performs an in-place upgrade of the CLI. The current process will be replaced with the latest version.

