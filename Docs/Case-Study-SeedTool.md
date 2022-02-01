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
