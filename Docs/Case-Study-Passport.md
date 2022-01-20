# Passport (Firmware 1.0.2)
### A #SmartCustody Case Study

Foundation Devices' Passport is an airgapped HD wallet/offline signer.

## Usage

The Passport holds seeds and can interact with software, which acts as a watch-only wallet. Transactions are prepared by the chosen software app, then sent to the Passport via airgap for signing.

The normal process for using a Passport is:

1. Enter PIN for Passport.
2. Create a seed on Passport or import using BIP-39 words.
3. Back up Passport to two included MicroSD cards.
4. Pair Passport with Software Wallet by displaying QR code on Passport and reading it on Software App. This transfers account information (a hdpath and xpub) to the Mobile App, encoded as `ur:bytes`. This may be done to create a watch-only single sig wallet or to provide one key for a multisig wallet. 
6. Transfer funds into Software Wallet using its address mechanisms.
7. Send funds by creating a transaction on the Software App, then generating a PSBT for signing. Formats supported by Passport include `ur:crypto-psbt` encoded as a QR or PSBTs transferred by MicroSD.
8. Read and sign the transaction on the Passport, then send it back as a PSBT encoded in a QR. [might this change with 1.0.8? Test with Sparrow]

## Gordian Principles

As an airgapped wallet, the Keystone matches the general design of the [Gordian Architecture](https://github.com/BlockchainCommons/Gordian#overview-gordian-architectural-model).
It interacts with the more specific Gordian Principles as follows:

### Independence

**Pros:**

With personal control of seeds and personal choice of software wallets, Passport provides a high level of independence.

* Passport allows direct, personal control of all assets. The master seed resides on the Passport; Software Apps only receive xpubs, for use either as a watch-only wallet, or as one key in a multisig.

**Neutral:**

* Passport supports interaction with a number of Software Wallets, pushing questions of how the Bitcoin network is accessed to that software.

### Privacy

The use of the Passport and a Software App together keep a user's information close.

**Pros:** 

* As a closely held device, Passport maximizes the privacy possibilities for private keys.
* The Passport is only accessible through QR codes or a micro-SD card.

**Neutral:**

* Because Passport supports interaction with a number of Software Wallets, the question of whether honey points of information could be created on the servers those wallets connect to is left to them.

### Resilience: Minimizing Single Point of Compromise (SPOC)

Minimizing SPOC protects data from theft: on the Passport, it's managed through codes and PINs.

**Pros:**

* The physical device is protected by a PIN.
* A Secure Element stores the private keys.
* Passport protects backups with a set of six [Bytewords](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2020-012-bytewords.md).
* Passport proactively supports the use of multisigs.

### Resilience: Minimizing Single Point of Failure (SPOF)

Minimizing SPOF protects data from loss: on the Passport, the most innovative feature is its backup system.

**Pros:**

* Passport heavily encourages backups of the device to the two included MicroSD cards, to save seeds and other info in case of Passport loss.
* Passport proactively supports the use of multisigs, and backs up complete information on the multisig.

**Cons:**

* PINs can form a SPOF if lost.
* Backup Bytewords can form a SPOF if lost.

**Openness.**

Passport provides interoperability with a variety of software wallets, though not always using fully interoperable specifications.

**Pros:**

* Seeds can be transferred onto or off of the device using BIP-39.
* More than half-a-dozen wallets are interoperable with Paaport.
* Some interoperability is managed through Uniform Resources (URs) such as `ur:bytes` and `ur:psbt`.
* Software is [open source](https://docs.foundationdevices.com/en/open-source).
* 
**Cons:**

* Some interoperability is managed through a variety of other means, such as JSON-encoded xpubs, base64-encoded PSBTs, and textual descriptions of accounts, much of which is not self-describing.

**Neutral:**

* Software is [open source](https://github.com/KeystoneHQ).
* Security audit is [publicly available](https://github.com/KeystoneHQ/Keystone-developer-hub/blob/main/audit-report/cobo_audit_report_2020_09_en_1_0.pdf).
