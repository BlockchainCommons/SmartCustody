# Passport (Firmware 1.0.8)
### A #SmartCustody Case Study

Foundation Devices' Passport is an airgapped HD wallet/offline signer.

## Overview

Foundation Devices is a second-generation hardware wallet that holds seeds and connects to software wallets through either QR codes or data transferred on a MicroSD card. It dependes on a chosen software wallet for transactions, simply signing acceptable PSBTs when it's passed them and allowing the software wallet to do transmission.

* **Web Site:** https://foundationdevices.com/passport/details/
* **GitHub:** https://github.com/Foundation-Devices

## Usage

<img src="https://raw.githubusercontent.com/BlockchainCommons/SmartCustody/master/Images/casestudy/cs-passport-1.jpg" width=350 align="right">

The Passport holds seeds, whose xpubs it shares with a chosen Software Wallet, which will act as a watch-only wallet. Transactions are then prepared by the Software Wallet and sent to the Passport via airgap (or MicroSD) for signing.

The normal process for using a Passport is:

1. Enter PIN for Passport.
2. Create a seed on Passport or import using BIP-39 words.
3. Back up Passport to two included MicroSD cards.
4. Pair Passport with Software Wallet by displaying QR code on Passport and reading it on Software App. This transfers account information (a hdpath and xpub) to the Mobile App, encoded as `ur:bytes`. This may be done to create a watch-only single sig wallet or to provide one key for a multisig wallet. 
6. Receive funds in the Software Wallet using its address mechanisms.
7. Send funds by creating a transaction on the Software App, then generating a PSBT for signing. Formats supported by Passport include `ur:crypto-psbt` encoded as a QR or PSBTs transferred by MicroSD.
8. Read and sign the transaction on the Passport, then send it back as a `ur:crypto-psbt` encoded in a QR.

## Gordian Principles

As an airgapped wallet, the Passport matches the general design of the [Gordian Architecture](https://github.com/BlockchainCommons/Gordian#overview-gordian-architectural-model).
It interacts with the more specific Gordian Principles as follows:

### Independence

**Pros:**

With personal control of seeds and personal choice of Software Wallet, Passport provides a high level of independence.

* Passport allows direct, personal control of all assets. The master seed resides on the Passport; Software Wallets only receive xpubs, for use either as a watch-only wallet, or as one key in a multisig.
* Passport supports interaction with a number of Software Wallets, allowing the user to choose whichever one they want and pushing questions of how the Bitcoin network is accessed to that software.

### Privacy

The use of the Passport and a Software App together keep a user's information close.

**Pros:** 

* As a closely held device, Passport maximizes the privacy possibilities for private keys.
* The Passport is only accessible through QR codes or a micro-SD card.

**Neutral:**

* Because Passport supports interaction with a number of Software Wallets, the question of whether honey pots of information could be created on the servers those wallets connect to is left to them.

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
* Restoring from MicroSD backups is simple and automated, other than the need to enter Bytewords as a passcode.
* While supporting the use of multisigs, Passport backs up complete information on the multisig.

**Cons:**

* PINs can form a SPOF if lost.
* Backup Bytewords can form a SPOF if lost.

### Openness

Passport provides interoperability with a variety of software wallets, though not always using the most interoperable specifications.

**Pros:**

* Seeds can be transferred onto or off of the device using BIP-39.
* More than half-a-dozen wallets are interoperable with Passport.
* Some interoperability is managed through Uniform Resources (URs) such as `ur:bytes` and `ur:psbt`.
* Electronics, assembly, and software is [open source](https://docs.foundationdevices.com/en/open-source) and code in binary is [reproducible](https://walletscrutiny.com/hardware/passport/).

**Cons:**

* Some interoperability is managed through a variety of other means, such as JSON-encoded xpubs, base64-encoded PSBTs, and textual descriptions of accounts, much of which is not self-describing.

## Adversaries

Passport offers specific defenses against the following [#Smartcustody](https://www.smartcustody.com/) adversaries. Other adversaries such as Censorship, Correlation, and Transaction Error fall into the purview of the Software Wallet used.

### Bitrot

Protecting against Bitrot means ensuring that you don't lose funds due to obsolence of hardware or software. Following open standards for storage of seeds or private keys largely does this. Theoretically, a user can be totally protected if he finds his BIP-39 words and records them, but this is not strongly suggested. Instead, Passport largely depends on the MicroSD backups. The easiest way to restore these is directly to a functional Passport, but the 7zip backup files can restored elsewhere using the backup's ByteWords as the password, separating the six words with spaces. The result is a text file containing a variety of private key info, which could be restored anywhere. Provided that the user understands the procedure, this also entirely overcomes the Bitrot adversary.

### Disaster

Though the Passport doesn't advertise it, its core methodology of backing up to two different MicroSDs could be potent protection against Disaster if they were stored in widely separated locations.

### Institutional Theft

With private keys held on the Passport, the possibilities of institutional theft are minimized (though the Software Wallet used could used as an attack vector if the user doesn't carefully check the PSBTs that they're signing).

### Key Fragility

The main defense against key fragility is the backup MicroSDs, though they could still be lost if the backup words for those MicroSDs were lost.

### Network Attack

The use of an airgapped device to hold all seeds largely eliminates the possibility of network attack.

### Physical Theft

Passport protects against physical theft mainly by its PIN and the limit on the number of guesses — though at 21, that number of guesses is relatively high.

### Supply-Chain Attack

A blue light constantly displays to show you that your Passport has not been tampered with (although of course the blue light could be tampered with). There is also the typical security sealing of the device.

_Death/Incapacitation remains one of the largest outstanding adversaries, as use of the Passport ultimately depends on personally known codes. Coercion and Blackmail also remain potential issues with the Passport, though these are adversaries that are often more theoretical than practical._

## Interoperability

Transfer of data between the Passport and various Software Wallets seems to be varied.

* `ur:bytes` are used in some cases to allow the use of animated QRs.
* `ur:crypto-psbt` is recognized for the input of PSBTs.

Backups are maintained as .txt files that are 7zipped, with six Bytewords, space separated, used as the password.

### Future Development Suggestions

Interoperability could be improved by full usage of URs, whose self-describing and self-verifying data is resistant to Bitrot and can be used by a variety of applications.

* Bare `ur:bytes` should not be used if a UR type exists, as `ur:bytes` lose the advantages of being self-described and thus easily portable.

In addition, URs could be specifically used in the following manners:

* Seeds could be imported as `ur:crypto-seed`, encoded as a QR; or preferably using `ur:crypto-request`, encoded as a QR.
* Seeds could be easily exportable in a digital form, using `ur:crypto-seed`, encoded as a QR.
* Seeds could be exportable as shards, to minimize SPOFs, preferably as `ur:crypto-sskr`, either encoded as a QR or as ByteWords.
* PSBTs could be `ur:crypto-psbt` for both sending and receipt, but ideally should be transferred as part of a `ur:crypto-request`/`ur:crypto-response` protocol.

For more, see [registry of UR types](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2020-006-urtypes.md), [overview of crypto-request](https://github.com/BlockchainCommons/crypto-commons/blob/master/Docs/ur-99-request-response.md), and [usage of crypto-request instead of crypto-psbt](https://github.com/BlockchainCommons/crypto-commons/blob/master/Docs/crypto-request-or-crypto-psbt.md).

A new specification for backup formatting could be helpful. As noted, Passport uses 7zip password-protected by 6 ByteWords. Coldcard uses a similar methodology, but uses 12 different BIP-39 words for each backup. Blockchain Commons generally leans toward Passport's choice because of the careful selection of ByteWords to minimize confusion and even allow usage by non-English speakers, but hasn't deeply looked into the topic.

## Hardware & Software

Passport contains a	STM32h753 processor and a Microchip 608a secure element. Betrusted's [Avalanche Noise Source Design](https://betrusted.io/avalanche-noise) is implemented for their TRNG. [Firmware](https://github.com/Foundation-Devices/passport-firmware) is coded in C and MicroPython.

Firmware upgrades are possible using a MicroSD card.

## Final Notes

Passport implements much the same architecture that Blockchain Commons suggests in its reference implementation [Gordian Seed Tool](https://apps.apple.com/us/app/gordian-seed-tool/id1545088229), but with a independent hardware foundation, which offers a smaller attack surface than a full mobile device such as an iPhone. Nonetheless, it embodies the same architectural concept: using a closely held device to securely store seeds, utilizing that device to enable watch-only wallets, and passing PSBTs to the device for signing. It's an architecture that maximizes Independence and Privacy, two of the core Gordian ideals.

The Resilience of Passport, focused on its MicroSD backups, provides a pragmatic solution to the core issue of Key Fragility that users are likely to actually use because of its ease-of-use. However, it also creates some Key Fragility of its own due to the requirement of ByteWords to restore those backup. Passport's support for multisigs provides a possible answer to the problem of Key Fragility, but much like Passport's BIP-39 word backups it's entirely left up to the user rather than offered as a strong suggestion.

The Openness of Passport is seen through some support for the UR specification, but it also seems to make do as is necessary to integrate with a variety of other wallets. Again, this is a pragmatic solution, and one that likely offers the best integration today, but increased usage of URs could provide better interoperability with more wallets going forward and even future-proof the design.

## Disclaimer

Foundation Devices is a Sustaining Sponsor of Blockchain Commons. Their Passport device was chosen for this Case Study because of its adoption of UR specifications.
