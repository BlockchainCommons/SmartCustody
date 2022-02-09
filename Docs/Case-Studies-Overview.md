# #SmartCustody Case Studies

The following case studies discuss how a variety of hardware and software wallets address Blockchain Commons' principles for self-sovereign wallet design and how they respond to a variety of adversaries identified by #SmartCustody risk-modeling.

**Airgapped Wallets:**

* Blockchain Commons Seed Tool (TBD)
* Foundation Devices Passport (TBD)
* Keystone Pro (TBD)

**Software Wallets:**

* Sparrow Bitcoin Wallet (TBD)

## Gordian Principles

The [Gordian Principles](https://github.com/BlockchainCommons/Gordian#gordian-principles) are independence, privacy, resilience, and openness. They together outline a self-sovereign methodology for the management of cryptocurrency, where a user stays in control of their digital assets and can easily transfer them, but simultaneously has good protections from the loss of funds that can otherwise arise from personal oversight of funds. 

Each Case Study measures how the device advances the four Gordian Principles or succumbs to their dangers.

### Gordian Architecture

Blockchain Commons has advanced an [architectural model](https://github.com/BlockchainCommons/Gordian#overview-gordian-architectural-model) that we support as a best practice to advance the Gordian Principles. It supports the Gordian Principles by suggesting a partitioned architecture where data and services are isolated from each other, only connected by airgaps or torgaps. One of the preferred architectures for wallet design has seed holders physically isolated from the network, using QR codes transmitted by cameras to grant a networked transaction coordinators pubkeys to create a wallet and then signing PSBTs using that same method. We consider this the second generation of wallet design, succeeding the first generation of connected hardware wallets such as Ledger and Trezor.

The airgapped wallets studied here can work in this configuration, while the software wallets can act as networked transaction coordinators for the airgapped wallets.

## SmartCustody Adversaries

Blockchain Commons' [#SmartCustody model](https://github.com/BlockchainCommons/SmartCustody/blob/master/README.md) is a risk-modeling system where users assess vulnerabilities in their custody scenario, map those vulnerabilities to adversaries, then assess which adversaries. Each adversary is an anthropomorphized threat that typically could cause a loss of funds (or other damage).

The case studies to date suggest that the following adversaries are defeated (or at least impaired) by the following airgapped & connected wallets:

<table>
  <tr>
    <td></td>
    <td>Keystone</td>
    <td>Passport</td>
    <td>Seed Tool</td>
  </tr>
  <tr>
    <td><b>Bitrot</b></td>
    <td></td>
    <td style="background: green"><b>Yes</b></td>
    <td style="background: green"><b>Yes</b></td>
  </tr>
  <tr>
    <td><b>Convenience</b></td>
    <td></td>
    <td style="background: red"><b>No</b></td>
    <td style="background: aquamarine"><b>Partial</b></td>
  </tr>    
</table>

## More Case Studies

[would love to have more]
[we can edit/respond to ones, even self-ones]

