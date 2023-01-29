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


If you have a GITHUB_TOKEN exported, it will use it.
