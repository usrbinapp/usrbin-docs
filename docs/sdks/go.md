# Go SDK

## Installing

```
go get github.com/usrbinsdk/usrbin/go
```

## Initializing

Somewhere, in your code:

```
	usrbinsdk, err := usrbin.New(
		version,
		usrbin.UsingGitHubUpdateChecker("github.com/<org>/<repo>"),
	)
```


## Supported options

### `UsingGitHubUpdateChecker`

When provided, this will be the source used for checking for updates. Usrbin will query the latest release tag on this repo, and (assuming it's semver compliant), compare it with the current version. If the latest release is newer, the usrbin SDK will return information about this release to your code.

### `UsingHomebrewFormula`

When provided, this will link your integration to a homebrew formula. This is necessary for usrbin to detect if your binary was installed on the machine using brew. Without this, usrbin will overwrite versions of your binary that were installed by Homebrew.
