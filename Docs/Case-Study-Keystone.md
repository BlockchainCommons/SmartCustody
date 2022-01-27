# Keystone (Firmware M-5.2/B-2.5)
### A #SmartCustody Case Study

The Keystone is an airgapped HD wallet/offline signer.

## Usage

The Keystone is a device that holds your seeds and can interact with Software Wallets , which act as watch-only wallets. Transactions are prepared by the Software Wallet, then sent to the Keystone via airgap for signing. There are two major branches of firmware for the Keystone. The "M" firmware, which ships with the Keystone, allows for transactions with several different cryptocurrencies, while the "B" firmware is Bitcoin-only. Besides lowering the potential attack surface on the Keystone, the "B"itcoin-only firmware also provides more sophisticated multisig capabilities that are fundamental to #SmartCustody, and thus are the main focus of thie case study.

The default process for using a Keystone with "M"ulticoin firmware depends on the Keystone's Companion App:

1. Create a wallet on Keystone or import using BIP-39 words or Shamir's Secret Sharing with SLIP-39.
2. Back up wallet by writing down BIP-39 or SLIP-39 words.
3. Bind Keystone to Companion App by displaying QR code on Keystone and reading it on Companion App. This transfers account information (a hdpath and xpub) to the Companion App, encoded as `ur:bytes`.
4. Receive funds from remote wallet: QR codes can be read from Keystone or from Companion App.
5. Send funds by creating a transaction on the Companion App, then generating a QR for signing containing a PSBT encoded as `ur:bytes`.
6. Read and sign the transaction on the Keystone, then send it back as a PSBT encoded as `ur:bytes`.

[other hardware options]

["B"itcoin]

Additional wallets on Keystone may be created using the "Hidden Wallet" feature. Only one wallet is displayed at a time; switching to another requires a passphrase, with no indication given on the device that the additional wallet exists.

## Gordian Principles

As an airgapped wallet, the Keystone matches the general design of the [Gordian Architecture](https://github.com/BlockchainCommons/Gordian#overview-gordian-architectural-model).
It interacts with the more specific Gordian Principles as follows:

[TODO: Resort by Pro/Con]

**Independence.**

Keystone's independenced focuses on the ability to transact funds without outside intervention.

* Keystone allows direct, personal control of all assets. The master seed resides on the Keystone; a watch-only wallet exists on the Companion App.
* Keystone does _not_ provide an options for choosing cryptocurrency servers to work with, potentially creating a path for censorship that might require using another device with your seed for spending.

**Privacy.**

The use of the Keystone and the Companion App together keep a user's information close.

* As a closely held device, Keystone maximizes the privacy possibilities for private keys.
* The Keystone is only accessible through QR codes or a micro-SD card.
* Again, Keystone does _not_ provide options for choosing cryptocurrency servers, and so it's possible that data honeypots could be created: the user doesn't know.

**Resilience.**

Keystone's resilience depends on users properly managing their backups, with the biggest advance being the inclusion of Shamir's Secret Sharing.

* The physical device is protect by password and/or fingerprint.
* A Secure Element stores the private keys.
* The device is designed to self-destruct in the case of physical tampering (which can reduce the danger of single-point-of-compromise but increase the danger of single-point-of-failure).
* Master seeds can be backed up using written BIP-39 words. 
* Keystone suggests backing up the BIP-39 words to the steel Keystone Tablet.
* Master seeds can alternatively be backed up using Shamir's Secret Sharing and writing down the shards.
* Keystone used with Companion App does _not_ provide any native multisig capabilities (though it's possible using the Keystone with certain other devices), so BIP-39 words can act as a single-point-of-compromise.
* Because there are _not_ native multisig capabilities, loss of the Keystone device along with the backed up words can act as a point-of-failure.
 
**Openness.**

Keystone provides open information on their software and on their hardware audit. Interoperability is more limited, but there is full ability to move seeds on or off device.

* Seeds can be transferred onto or off of the device using BIP-39 or Shamir's Secret Sharing.
* Interactivity is provided not just with the Companion App, but also Metamask and a few other specific online coordinators.
* Uniform Resources (URs) underlie QR codes, _but_ they are encoded as `ur:bytes` not more interoperable UR types such as `ur:hdkey` or `ur:psbt`
* The transferred data is _not_ self-describing.
* SLIP-39 can cause interoperability problems because it does _not_ [round trip with BIP-39](https://github.com/BlockchainCommons/lethekit/issues/38).
* Software is [open source](https://github.com/KeystoneHQ).
* Security audit is [publicly available](https://github.com/KeystoneHQ/Keystone-developer-hub/blob/main/audit-report/cobo_audit_report_2020_09_en_1_0.pdf).

## Adversaries

The Keystone offers specific defenses against the following [#Smartcustody](https://www.smartcustody.com/) adversaries:

**Bitrot.**

Provided that a sure correctly stores their Recovery Phrase, they can transfer their seeds to another device if either Keystone or the Companion App grows obsolete. A Recovery Phrase Check allows users to occasionally ensure that phrase remains valid. 

However, there is no way to regenerate the BIP-39 words or Shamir shards after initial creation, so if they are later lost, and the user does not move the funds to a new seed, the danger of Bitrot can resurface.

There also are real dangers from the alternate passphrases, which could easily be lost if there was a need to transfer devices, since they are not visible.

**Coercion.**

The Passphrase Wallet feature, which allows for the creation of additional wallets that are only visible if a user types in the correct passphrase, is an interesting methodology to try and prevent physical coercion. The idea of public wallets and secret wallets has long been a proposed solution to this adversary, and is fully enacted on the Keystone.

**Convenience.**

The Keystone provides sufficient convenience that users might be discouraged from using more "convenient", lower security methodologies, such as conducting transactions on a directly connected devices. The QR codes allow quick transfers across airgaps and the Keystone's high-quality touchscreen means that they don't have to fumble with the low-resolution LED screens and push buttons of the last generation of hardware wallets, which may have been sufficient to deter their usage.

**Disaster.**

Shamir's Secret Sharing allows a strong defense against disaster, if shards are in widely separated areas, but it requires both the use of Shamir's Secret Sharing, over the simpler BIP-39 methodology, and their separation.

**Institutional Theft.**

With private keys held on the Keystone, with all transaction creation done on the Companion App, and with source opened, the possibilities of institutional theft are minimized. (As always, the manufacturer must still be trusted.)

**Key Fragility.**

Key fragility is one of the biggest threats to individual cryptocurrency holders, and Shamir's Secret Sharing is a first step toward minimizing that.

**Network Attack.**

The use of an airgapped device to hold all seeds largely eliminates the possibility of network attack.

**Physical Theft.**

By depending on fingerprints and passwords, and by destroying information is there are too many bad password guesses or if the device is physically tampered with, Keystone makes physical theft largely irrelevent as a single-point-of-compromise. However, it still can be a single-point-of-failure if BIP-39 words or Shamir shards were not correctly held and protected.

**Supply-Chain Attack.**

A Keystone authenticates itself with the Keystone website on first usage. That, with its self-destruction in the case of physical tampering, minimizes the possibility of a supple-chain attack.

**Transaction Error.**

Like most modern wallets, the Companion App takes care of most of the transaction details, such as scanning in addresses through QRs and determining fees. This greatly reduces the possibility of transaction errors.

_Death/Incapacitation remains one of the largest outstanding adversaries, though use of Shamir's Secret Sharing can resolve that. Though Keystone advertises a true random number generator, and backs that up by releasing its code, they also provide documentation on generating seeds with dice, which can remove the possibility of Systemic Key Compromise. Censorship and Correlation may or may not be possible depending on the design of the integration of cryptography servers. They may also be triggered by the use of a centralized pricing server._

## Interoperability

Transfer of information between the Keystone and Companion App primarily occurs through QR codes.

* Authentication information is transferred from the web to the Keystone using JSON encoded in a QR.
* Account information of hdkey and xpub is transferred from Keystone to Companion App using `ur:bytes` encoded in a QR.
* Transaction information of a PSBT is transferred between Keystone and Companion App using `ur:bytes` encoded in a QR.

General interoperability with other devices is not possible because `ur:hdkey`, `ur:psbt`, `ur:request`, `ur:response`, and other specific UR types are not used.

[add suggestsions/best practices]

## Hardware & Software

Keystone uses a proprietary Secure Element to hold private keys. It is described as "bank grade" and "EAL 5+" (semiformally designed and tested). 

[software]

## Final Notes

The first generation of #SmartCustody primarily depended on good procedures for storing recovery words, which Keystone supports through its BIP-39 output and its Keystone Tablet.

A second generation of #SmartCustody focuses on Shamir's Secret Sharing, which Keystone also supports. Support comes through use of SLIP-39, which has some [round-tripping issues](https://github.com/BlockchainCommons/lethekit/issues/38), not Blockchain Commons' own [SSKR](https://github.com/BlockchainCommons/bc-sskr).

A third generation of #SmartCostudy focuses on multisig, and though Keystone could act as a holder of a single key when used in conjunction with certain third-party transaction coordinators, there's no native implementation in the Companion App. (A standard Gordian architecture would be easily implemented in their native architecture, with a two-of-three multisig, where one key is held in the Keystone, one in the Companion App, and one offline.)

#SmartCustody also focuses on interoperability (openness) as a crucial element because a fully interoperable device gives a user more options for how to use it to meet their particular needs and reduces the threat of dangers such as Bitrot because private data is not locked into a single device. There is some interoperability for Keystone, allowing its use with specific other devices, which provides increased independence to the user, but it's thus far limited. Uses of self-describing URs, such as `ur:psbt` and `ur:hdkey` could dramatically increase this interoperability, rather than use of `ur:bytes`, which offers some of the encoding benefits of URs (primarily the sequencing that allows for animated QRs) but not the benefits of self-describing data.
