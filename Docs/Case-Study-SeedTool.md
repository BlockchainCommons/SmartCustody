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

## Adversaries

Seed Tool offers specific defenses against the following [#Smartcustody](https://www.smartcustody.com/) adversaries. 

**Bitrot.**

Bitrot occurs when a software program or hardware device becomes outdated. There is some opportunity for Bitrot in Seed Tool, if the software is not updated and it no longer becomes possible to run it on newer devices. This is somewhat offset by the software being fully [open source](https://github.com/BlockchainCommons/GordianSeedTool-iOS) and moreso by Seed Tool offering the _opportunity_ for users to back up their data in a variety of ways.

**Convenience.**

With a touchscreen and a full graphical interface, Seed Tool offers a lot of convenience. This can itself be an adversary, because it means that users might not be using a fully airgapped device and are definitely using a device with a larger attack service than something that's exclusively a wallet. However, this level of convenience is meant to ward off users choosing something much more convenient (and less secure) such as keeping their seeds on a networked computer or at a centralized exchange.

**Institutional Theft.**

Gordian Seed Tool is well-protected, even from institutional theft at Apple, provided that the data is actually protected as described in Apple APIs and tech sheets.

**Key Fragility.**

The backup to iCloud provides strong protection against key fragility, one of the largest dangers for cryptocurrency loss. The user can also proactively back up their seeds in a variety of different ways.

**Network Attack.**

If Seed Tool is entirely airgapped by using a non-networked mobile device, this largely eliminates the possibility of network attack. If Seed Tool is run on a networked mobile device, the possibility of network attack still remains very low, due to the strong protections of the iPhone.

**Physical Theft.**

Seed Tool protects against physical theft with its 2FA, especially for any newer devices that uses biometrics as one of the factors.

**Systemic Key Compromise.**

Seed Tool offers random seed generation. But, if users feel uncomfortable with that, and the possibility of Systemic Key Compromise if an error were to be found in the algorithm, they can instead generate seeds with dice, cards, or coin flips.


Because Seed Tool is primarily a holder of seeds, it doesn't address the following adversaries, which are more likely to be found on the Wallet side of the equation: Censorship, Correlation, Transaction Error, User Error.

Seed Tool also doesn't currently resolve the following adversaries of note: Blackmail, Coercion, Death/Incapacitation, Social Engineering, Supply-Chain Attack.

## Interoperability

Seed Tool maximizes how you can get data into the app:

* Data can be read from files, images, photos, or the paste buffer.

Seed Tool supports input and output of URs, using either QRs, textual URs, or in some cases ByteWords.

* Seeds can be imported as `ur:crypto-seed`.
* Backups can be restored as `ur:crypto-sskr`, provided that sufficient shares are available.
* Specific keys can be exported using `ur:crypto-response` in response to a `ur:crypto-request` for a derivation.
* PSBTs can be signed in a `ur:crypto-response` in response to a `ur:crypto-request` of an unsigned or partially signed PSBT.
* Seeds can be output as `ur:crypto-seed`.
* Seeds can be backed up as `ur:crypto-sskr` shares.
* Accounts can be exported as `ur:crypto-account`.
* Pubkeys can be exported as `ur:crypto-hdkey`.
* Private keys can be exported as `ur-crypto-hdkey`.

Blockchain Commons considers URs the gold standard for interoperability because they are both standardized and self-describing.

Seed Tool also supports other popular data transfer methods for cryptocurrency:

* Seeds can be imported as BIP-39 words or hex bytes.
* Seeds can be exported as BIP-39 words or hex bytes.
* Master keys can be exported as output descriptors.
* Addresses can be exported. 

## Hardware & Software

Gordian Seed Tool runs on any modern MacOS or iOS device. iOS is by far the preferred platform due to security advantages of having a closely held device with a more limited attack surface.

The full source code for Gordian Seed Tool is available through [Git Hub](https://github.com/BlockchainCommons/GordianSeedTool-iOS).
