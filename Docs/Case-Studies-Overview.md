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

Each Case Study measures how the device advances the four Gordian Principles (or fails to do so).

### Gordian Architecture

Blockchain Commons has advanced an [architectural model](https://github.com/BlockchainCommons/Gordian#overview-gordian-architectural-model) that we support as a best practice to advance the Gordian Principles. It supports the Gordian Principles by suggesting a partitioned architecture where data and services are isolated from each other, only connected by airgaps or torgaps. One of the preferred architectures for wallet design has seed holders physically isolated from the network, using QR codes transmitted by cameras to grant a networked transaction coordinators pubkeys to create a wallet and then signing PSBTs using that same method. We consider this the second generation of wallet design, succeeding the first generation of connected hardware wallets such as Ledger and Trezor.

The airgapped wallets studied here can work in this configuration, while the software wallets can act as networked transaction coordinators for the airgapped wallets.

## SmartCustody Adversaries

Blockchain Commons' [#SmartCustody model](https://github.com/BlockchainCommons/SmartCustody/blob/master/README.md) is a risk-modeling system where users assess vulnerabilities in their custody scenario, map those vulnerabilities to adversaries, then assess which adversaries. Each adversary is an anthropomorphized threat that typically could cause a loss of funds (or other damage).

The case studies to date suggest that the following adversaries are defeated (or at least impaired) by the various wallets. The wallets to the left are airgapped wallets being used as seed holders, those to the right are software wallets being used as transaction coordinators. Adversaries that are irrelevent to a role are not noted.

<table>
  <tr>
    <td></td>
    <td colspan=3><i>Seed Holders</i></td>
    <td></td>
    <td><i>Coordinators</i></td>
  </tr>
  <tr>
    <td>Adversary</td>
    <td><b>Keystone</b></td>
    <td><b>Passport</b></td>
    <td><b>Seed Tool</b></td>
    <td><b>+</b></td>
    <td><b>Sparrow (T.C.)</b></td>
  </tr>
  <tr>
    <td><b>Bitrot</b></td>
    <td></td>
    <td><b><font color="DarkGreen">Yes</font></b></td>
    <td><b><font color="DarkGreen">Yes</font></b></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td><b>Censorship</b></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><b><font color="DarkGreen">Yes</font></b></td>
  </tr>    
  <tr>
    <td><b>Convenience</b></td>
    <td></td>
    <td><b><font color="Maroon">No</font></b></td>
    <td><b><font color="Army Green">Partial</font></b></td>
    <td></td>
    <td><b><font color="Army Green">Partial</font></b></td>
  </tr>    
  <tr>
    <td><b>Correlation</b></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><b><font color="DarkGreen">Yes</font></b></td>
  </tr>    
  <tr>
  <tr>
    <td><b>Disaster</b></td>
    <td></td>
    <td><b><font color="Army Green">Partial</font></b></td>
    <td><b><font color="Maroon">No</font></b></td>
    <td></td>
    <td></td>
  </tr>    
  <tr>
    <td><b>Institutional Theft</b></td>
    <td></td>
    <td><b><font color="DarkGreen">Yes</font></b></td>
    <td><b><font color="DarkGreen">Yes</font></b></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td><b>Key Fragility</b></td>
    <td></td>
    <td><b><font color="DarkGreen">Yes</font></b></td>
    <td><b><font color="DarkGreen">Yes</font></b></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td><b>Network Attack</b></td>
    <td></td>
    <td><b><font color="DarkGreen">Yes</font></b></td>
    <td><b><font color="DarkGreen">Yes</font></b></td>
    <td></td>
    <td><b><font color="DarkGreen">Mostly</font></b></td>
  </tr>
  <tr>
    <td><b>Physical Theft</b></td>
    <td></td>
    <td><b><font color="DarkGreen">Yes</font></b></td>
    <td><b><font color="DarkGreen">Yes</font></b></td>
    <td></td>
    <td><b><font color="DarkGreen">Mostly</font></b></td>
  </tr>
  <tr>
    <td><b>Supply-Chain Attack</b></td>
    <td></td>
    <td><b><font color="DarkGreen">Yes</font></b></td>
    <td><b><font color="Maroon">No</font></b></td>
    <td></td>
    <td><b><font color="Maroon">No</font></b></td>
  </tr>
  <tr>
    <td><b>System Key Compromise</b></td>
    <td></td>
    <td><b><font color="Maroon">No</font></b></td>
    <td><b><font color="Army Green">Optional</font></b></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td><b>Transaction Error</b></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><b><font color="DarkGreen">Yes</font></b></td>
  </tr>
</table>

## More Case Studies

We would love to have more case studies to exemplify how second-generation wallets (and beyond) apply the Gordian Principles and foil the #SmartCustody Adversaries.

If you would like to write your own self-assessment of your product, please feel free to enter a PR. We _will_ edit any case studies supplied to us, and may request a copy of any hardware wallet if we need to verify or re-assess any points. Please try to produce a well-written, organized, and balanced case study, without superlatives, as we (hopefully) did when looking at our own Gordian Seed Tool.

If you would like to contract us to assess a wallet and produce a case study for publication here, contact us directly at team@blockchaincommons.com.

We may continue to proactively produce other case studies ourselves. Our prime criteria for doing so is whether a wallet has strong interoperability, primarily through adoption of URs, SSKR, and other Blockchain Commons specifications.
