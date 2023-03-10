# Security

## Privacy of information

When integrating the usrbin SDK, you control what (if any) data is transmitted out of your CLI. The usrbin SDK does not include any server or data collection elements. We don't collect or have the capabilities to store information from users of your CLI.

## Integrity of updates

An important topic to discuss is how we verify the integrity of an update before installing it. When there's a published checksum for the update, the SDK will verify the checksum of the downloaded file matches.

For more information about checksum verification, see the [updaters](../updaters) page.
