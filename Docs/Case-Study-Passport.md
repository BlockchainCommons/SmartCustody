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

### Resilience against SPOC

Minimizing Single Point of Compromise (SPOC) protects data from theft: on the Passport, it's managed through codes and PINs.

**Pros:**

* The physical device is protected by a PIN.
* A Secure Element stores the private keys.
* Passport protects backups with a set of six [Bytewords](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2020-012-bytewords.md).
* Passport proactively supports the use of multisigs.

### Resilience against SPOF

Minimizing Single Point of Failure (SPOF) protects data from loss: on the Passport, the most innovative feature is its backup system.

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

**Cons:**

* Some interoperability is managed through a variety of other means, such as JSON-encoded xpubs, base64-encoded PSBTs, and textual descriptions of accounts, much of which is not self-describing.

## Adversaries

Passport offers specific defenses against the following [#Smartcustody](https://www.smartcustody.com/) adversaries. Other adversaries such as Censorship, Correlation, and Transaction Error fall into the purview of the Software App used.

**Bitrot.**

There is theoretical protection against Bitrot, as a user can choose to find his BIP-39 words and record them, but this is not strongly suggested. Instead, Passport largely depends on the MicroSD backups, which require a functioning Passport for them to be useful.

**Disaster.**

Though the Passport doesn't advertise it, its core methodology of backing up to two different MicroSDs could be potent protection against Disaster if they were stored in widely separated locations.

**Institutional Theft.**

With private keys held on the Passport, the possibilities of institutional theft are minimized (though the Software App used could remain an attack vector).

**Key Fragility.**

The main defense against key fragility is the backup MicroSDs, though they could still be lost if their backup words are lost.

**Network Attack.**

The use of an airgapped device to hold all seeds largely eliminates the possibility of network attack.

**Physical Theft.**

Passport protects against physical theft mainly by its PIN and the limit on the number of guesses — though at 21, that number of guesses is relatively high.

**Supply-Chain Attack.**

A blue light constantly displays to show you that your Keystone has not been tampered with (although of course the blue light could be tampered with). There is also the typical security sealing of the device.

_Death/Incapacitation remains one of the largest outstanding adversaries, as use of the Passport ultimately depends on personally known codes. Coercion and Blackmail also remain potential issues with the Passport, though these are adversaries that are often more theoretical than practical._

## Interoperability

Tranfer of data between Passport and various software wallet seems to varied.

* `ur:bytes` are used in some cases to allow the use of animated PSBTs.
* `ur:crypto-psbt` is recognized for the input of PSBTs.

### Future Development Suggestions

Interoperability could be improved by full usage of URs, whose self-describing data is resistant to Bitrot and can be used by a variety of applications.

* Bare `ur:bytes` should not be used if a UR type exists, as `ur:bytes` lose the advantages of being self-described and thus easily portable.
* Seeds should be easily exportable in a digital form, preferably as `ur:crypto-seed`, encoded as a QR.
* Seeds should also be exportable as shards, to minimize SPOFs, preferably as `ur:crypto:sskr`, either encoded as a QR or as ByteWords.
* Keys should be requestable from a software wallet, preferably using the `ur:crypto-request` methodology.
* PSBTs should be as `ur:crypto-psbt` for bother sending and receipt and ideally should be transferred as part of a `ur:crypto-request`/`ur:crypto-response` protocol.


