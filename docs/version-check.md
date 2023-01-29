# Version check

The version check method is the core of the usrbin.app SDK. This is where you can check for new versions, and even perform an in-place upgrade, in some scenarios.



```
% my-cli version

my-cli version v0.40.5
Update available: v0.41.0
To automatically update, run "my-cli version upgrade"
```

```
% my-cli version upgrade

Downloading my-cli v0.41.0... ok
Validating binary integrity... ok
Performing in-place upgrade... ok

Upgrade complete!
```
