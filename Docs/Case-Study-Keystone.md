# Keystone
### A #SmartCustody Case Study

The Keystone is an airgapped HD wallet/offline signer.

## Usage

The Keystone holds seeds and can interact with the Keystone Mobile App, which acts as a watch-only wallet. Transactions are prepared by the Mobile App, then sent to the Keystone via airgap for signing.

The normal process for using a Keystone is:

1. Create a wallet on Keystone or import using BIP-39 words or shards from Shamir's Secret Sharing.
2. Back up wallet by writing down BIP-39 words or shards from Shamir's Secret Sharing.
3. Bind Keystone to Mobile App by displaying QR code on Keystone and reading it on Mobile App. This presumably transfers an xpub to the Mobile App, encoded as `ur:bytes`.
4. Receive funds by reading address QR codes from Keystone or from Mobile App into remote wallet.
5. Send funds by creating a transaction on the Mobile App, then generating a QR for signing, which presumably is a PSBT, encoded as `ur:bytes`.
6. Read and sign the transaction on the Keystone, then send it back, now presumably as a fully signed PSBT, encoded as `ur:bytes`.

Additional wallets on Keystone may be created using the "Hidden Wallet" feature. Only one wallet is displayed at a time; switching to another requires a passphrase, with no indication given on the device that the additional wallet exists.

## Gordian Principles

As an airgapped wallet, the Keystone matches the general design of the [Gordian Architecture](https://github.com/BlockchainCommons/Gordian#overview-gordian-architectural-model).
It interacts with the more specific Gordian Principles as follows:

**Independence.**

* Keystone allows direct, personal control of all assets. The master seed resides on the Keystone; a watch-only wallet exists on the Mobile Device.
* Keystone does _not_ provide an options for choosing cryptocurrency servers to work with, potentially creating a path for censorship that might require removing the funds to another device.

**Independence.**

* As a closely held device, Keystone maximizes the privacy possibilities for private keys.
* The Keystone is only accessible through QR codes or a micro-SD card.
* Again, Keystone does _not_ provide options for choosing cryptocurrency servers, and so it's possible that data honeypots could be created: the user doesn't know.

**Resilience.**

* The physical device is protect by password and/or fingerprint.
* A Secure Element stores the private keys.
* The device is designed to self-destruct in the case of physical tampering (which can reduce the danger of single-point-of-compromise but increase the danger of single-point-of-failure).
* Master seeds can be backed up using written BIP-39 words. 
* Keystone suggests backing up the BIP-39 words to the steel Keystone Tablet.
* Master seeds can alternatively be backed up using Shamir's Secret Sharing and writing down the shards.
* Keystones does _not_ provide any multisig capabilities, so BIP-39 words can act as a single-point-of-compromise.
* Because there are _not_ multisig capabilities, loss of the Keystone device along with the backed up words can act as a point-of-failure.
 
**Openness.**

* Seeds can be transferred onto or off of the device using BIP-39 or Shamir's Secret Sharing.
* Interactivity is provided not just with the Mobile Device, but also Metamask and a few other specific online coordinators.
* Uniform Resources (URs) underlie QR codes, _but_ they are encoded as `ur:bytes` not more interoperable UR types such as `ur:hdkey` or `ur:psbt`

## Adversaries

## Specifications

## Hardware & Software
