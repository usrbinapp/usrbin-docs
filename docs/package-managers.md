# Package managers

Package managers are alternate methods of distributing your CLI. Some users prefer to use a package manager to install your CLI. If you distribrute your CLI using a package manager as one installation method, usrbin will be compatible. When attempting to install an update or perform an in-place upgrade of your CLI, usrbin will always check if the CLI was installed using one of the supported package managers. If it was, usrbin will refuse to install the update, and instead show the user a command or recommendation on how to use the package manager to perform the upgrade.

## Homebrew

Usrbin supports detecting if the package was installed via homebrew. To enable this functionality, the integration will have to pass the Homebrew formula into the SDK:

```go
import "github.com/usrbinapp/usrbin-go"

func NewUsrbinSDK() (*usrbin.SDK, error) {
    
    currentVersion := "1.0.0"

	return usrbin.New(
		currentVersion,
		usrbin.UsingHomebrewFormula("<formula name>"),
	)
}
```


