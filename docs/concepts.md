# Concepts

Usrbin is an SDK to keep a single binary CLI up to date. Unlike package managers, usrbin makes it very easy for you to include a version check and self-updating capabilities right in your own CLI.

It works for single binary executables that are built using a language that usrbin has an SDK for (currently only go).


## Comparing to package managers

A common question is "why not just ship with brew?". It's a great question because brew (and most package managers) do provide a way for the user to upgrade to the latest version. The difference between usrbin and package managers is that with usrbin, your users can learn about updates and even install the updates to your CLI from your CLI. 

When a CLI is installed using a package manager such as brew, usrbin will detect that and suggest the right package manager commands to update the CLI. usrbin will not overwrite versions installed by a package manager.


## Example

Our favorite example is `gcloud`. When running `gcloud version`, if there's a newer version available, the CLI itself tells you. And it tells you how to update:

```
% gcloud version
Google Cloud SDK 391.0.0
bq 2.0.75
core 2022.06.17
gsutil 5.10
Updates are available for some Google Cloud CLI components.  To install them,
please run:
  $ gcloud components update
```


Another example is `wrangler`:

```
% wrangler publish
 ⛅️ wrangler 2.1.5 (update available 2.8.1)
```

With usrbin, it's easy to add this same functionality into your CLI.


