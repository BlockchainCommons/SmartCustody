# Gordian Seed Tool (Version 1.3.1)
### A #SmartCustody Self Case Study

The Godian Seed Tool reference app allows for the storage and seeds and their backup, transfer, or usage.

This Case Study should not be taken as a review, as it covers one of Blockchain Commons' own apps. Rather, it's intended as a pure Case Study, demonstrating how the Blockchain Commons app meets the goals of the Gordian architecture and thus acting as further reference for the design.

## Usage

The Gordian Seed Tool stores seeds, optimally on an airgapped mobile device, and then allows their usage.

There are generally three ways to put seeds into Seed Tool:

* Create a seed with Seed Tool's randomization.
* Create a seed on Seed Tool using dice, cards, or coin flips.
* Import a seed from another source.

There are a number of ways that seed can then be used:

* Export the seed to another location.
* Export a key to another location.
* Respond to a request for a key.
* Respond to a request to sign a PSBT.

The Gordian architecture generally depends on airgaps for security, so the following usage most closely meets that design:

1. Add a seed to Seed Tool via any means.
2. Backup Your seed with SSKR.
3. Export a watch-only pubkey to a software wallet.
4. Import PSBTs from the software wallet using `ur:crypto-request`.
5. Export Signed PSBTs to the software wallet using `ur:crypto-response`.

## Gordian Principles

Gordian Seed Tool was designed as a reference to all four of the [Gordian Principles](https://github.com/BlockchainCommons/Gordian#gordian-principles).

### Independence

Gordian Seed Tool maximizes Independence by giving total control of seeds and what you do with them.

**Pros:**

* Seed Tool gives total control of all assets, with the seeds residing within Seed Tool.
* Through extensive support of Openness, Seed Tool ensures that users have total choice over what wallets or other devices to use with Seed Tool.

**Neutral:**

* Total independence means total responsibility: users might decide which wallets or other devices to use on their own.

### Privacy

The use of Gordian Seed Tool keeps all private data close.

**Pros:** 

* As a closely held device, Seed Tool maximizes the privacy possibilities for private keys.
* When run on networkless mobile device (iPhone or iPod Touch), the privacy of Seed Tool is near total; this decreases if Seed Tool is used on a closely held mobile device and even moreso if it's run on a computer.

**Neutral:**

* Again, the user bears responsibility for what happens when information is transffered out of Seed Tool. They must decide which wallets will optimize privacy (and other desirable features).

### Resilience against SPOC

Minimizing Single Point of Compromise (SPOC) protects data from theft: with Seed Tool, Apple's internal security provides this protection.

**Pros:** 

* Seed Tool stores all at-rest data in encrypted form.
* Access to Seed Tool is always protect by 2FA: one factor occurs when you log into your Apple account on first usage and another when you verify your access each time you look at data, usually using a biometric code.
* Seeds backed up to iCloud are encrypted, with the encryption key stores in your keychain.
* Seed Tool remains functional even if network access is completely turned off, creating a cold-storage device.

**Neutral:**

* Trust in Seed Tool ultimately rests on trust in Apple.

**Cons:**

* Some backup and sharing mechanisms have the possibility to be SPOCs if used. An individual user must decide between ease-of-use (Convenience) and resilience based on the individual risks of their own setup. Notably:
   * The network-printing option could make network access into a SPOC.
   * Cut-and-paste sharing options could allow other apps to access the secure data on the clipboard.

### Resilience against SPOF

Minimizing Single Point of Failure (SPOF) protects data from loss: with Seed Tool, this is automated via iCloud and also available via other means.

**Pros:**

* Data is all backed up to iCloud, unless turned off by the user, and thus can be recovered by all devices logged into that account.
* Users are given the capability to back up data in a variety of other ways, including printing SSKR shares, but they must decide to do so.

**Neutral:**

* Users can use seeds (and their keys) in any way that they want. If they use them to form multisigs, they will have additional protection from SPOF, but this is ultimately a decision up to the user.

**Cons:**

* iClouds backups can be lost if all physical devices or lost and Apple account information is lost.

### Openness

Seed Tool is the reference app for UR specifications, and so offers extensive interoperability.

**Pros:**

* Data can be imported via a variety of means, including URs.
* Data can be exported via a variety of means, including URs.

