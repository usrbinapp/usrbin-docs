# Roadmap

The following items are ideas that will probably land in future versions of usrbin:

## OCI Support

Currently, usrbin works with a `GitHubUpdateChecker`. It's built to be extensible and support other types of update sources. We want to look at OCI registries. While we haven't seen many people delivering their CLI using OCI, it seems like a great fit to support. With OCI, we can have better attestation by using content-addressable tags. Work currently happening in other projects will enable SBOMs to be retrieved along with the update, and provided to the user.

In general, there's some interesting security and provenance benefits we are interested in exploring by using OCI registries as a delivery source.

## Multiple file CLIs

Some CLIs have dependencies or additional files. Today, these aren't supported with usrbin. We do plan to address this and look at options to self-update multiple file CLIs.



