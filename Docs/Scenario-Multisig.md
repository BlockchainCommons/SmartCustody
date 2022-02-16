# Multisig Self-Custody Scenario

#### _Best practices for protecting Your personal digital assets using a multi-sig_

**THIS IS IN PROCESS AND SHOULD NOT BE CONSIDERED READY FOR USAGE.**

## Introduction to the Multisig Scenario

Digital assets held personally ("self-custody") face two major dangers: single point of failure (SPOF) and single point of compromise (SPOC), which is to say losing those assets either those loss or theft. Traditional self-custody solutions focus on decreasing SPOF with methodologies like seed backup, but in doing so tend to increase the possibility of SPOC. This is generally in tune with the adversaries that the average self-custodian would be facing. However, now that multisig is sufficiently deployed to allow ease-of-use, it can simultaneously decrease both SPOF and SPOC at a relatively small cost to convenience and complexity. 

This scenario explains how to do so. It does so by using a transaction coordinator on a computer, to manage the receipt and spending of funds while holding no keys, alongside two second-generation signing devices[^1] that hold those keys. SSKR shares are then used to divide up a third, recoveyr, key.

### About The Base Scenario

The base scenario presumes an audience with all of the following characteristics:

* A holder with a significant amount of digital assets (>10% of net worth);
    - with full and legal custody of the assets and no fiduciary responsibility to others;
    - and 100% of those assets shared with a spouse, if present, in estate planning.
* A holder who might be trading those assets actively or might be holding them long temr.
* A holder who lives in the first world, and thus is less concerned about issues like government attack, kidnapping, or privacy violations.
* A holder who has sufficient computer skills to comfortably install and run apps.

This scenario advocates the basic procedure to address XXX major types of adversaries, while the optional procedures can help protect against XXX further adversaries. Additional categories of "Non-Theft Crimes", "Loss by Government" and "Privacy-Related" adversaries are not strongly considered in this scenario. See **Adversaries**.

For simplicity, this document focuses on Bitcoin; adapting it to other cryptocurrencies may require choosing different signing devices.

{pagebreak}

## Procedures

The following procedure will help ensure the safety of a simple self-custody cold-storage scenario for managing digital assets. It is important that you initiate it when you have a large block of time: usually at least two hours when you will not be interrupted and when you will not be distracted. You don't want to make mistakes, and to avoid that it's best to do everything in one go.

### Adversaries

This process in this basic scenario has been optimized to avoid risks from XX adversaries listed below — simplified by not addressing the risks of all possible adversaries (over 25+). In particular, these adversaries were the ones selected as most likely to impact a self-custodian in the first world. Adversaries related to "Non-Theft Crimes", "Loss by Government" and "Privacy-Related" are not strongly considered in this scenario.

Some additional processes for this scenario are offered as options—but be careful to avoid [Process Fatigue](#adversary-process-fatigue).

[adversary list]

[notable absences]

See **Adversaries** for a more extensive list and discussion.

{pagebreak}

### Requirements

The following items are necessary for this procedure, and should be purchased in advance of your setting up this scenario.

* [  ] Small Home Safe (For example: [https://www.amazon.com/AmazonBasics-Security-Safe-0-5-Cubic-Feet/dp/B00UG9HB1Q/](https://www.amazon.com/AmazonBasics-Security-Safe-0-5-Cubic-Feet/dp/B00UG9HB1Q/) )
* [  ] Safety Deposit Box at Bank or other institution
* [  ] Existing Laptop or Desktop Computer capable of running [Sparrow Wallet(https://sparrowwallet.com/).
* [  ] 1 Package Waterproof Laser Paper (TerraSlate, made of 1-PET [https://www.amazon.com/TerraSlate-Paper-Waterproof-Printer-Sheets/dp/B00NWVGOF4](https://www.amazon.com/TerraSlate-Paper-Waterproof-Printer-Sheets/dp/B00NWVGOF4) or Rite in the Rain All-Weather Copier Paper, made of coated recyclable wood [https://www.amazon.com/Rite-Rain-All-Weather-Copier-8511/dp/B0016H1RYE/](https://www.amazon.com/Rite-Rain-All-Weather-Copier-8511/dp/B0016H1RYE/) or equivalent)

Three devices are required to hold seeds: two live devices and one backup/temporary device. We suggest the following:

* [  ] [Foundation Devices Passport](https://foundationdevices.com/passport/details/)
* [  ] iPhone or iPod to run [Gordian Seed Tool](https://apps.apple.com/us/app/gordian-seed-tool/id1545088229) for active seed.
* [  ] Separate[^2] iPhone or iPod to temporarily create and shard seed using [Gordian Seed Tool](https://apps.apple.com/us/app/gordian-seed-tool/id1545088229).

The three devices selected are all second-generation signing device technology[^3][^4]. See the footnotes for discussions of why we choose these specifically[^5]. 

### Case Studies

Further discussions of why specific transaction coordinators or signing devices are desirable, or not, may be found in our [#SmartCustody Case Studies](https://github.com/BlockchainCommons/SmartCustody/blob/master/Docs/Case-Studies-Overview.md).

**Signing Devices:**

* [Blockchain Commons Seed Tool](https://github.com/BlockchainCommons/SmartCustody/blob/master/Docs/Case-Study-SeedTool.md)
* [Foundation Devices Passport](https://github.com/BlockchainCommons/SmartCustody/blob/master/Docs/Case-Study-Passport.md)
* Keystone Pro (TBD)

**Transaction Coordinators:**

* [Sparrow Bitcoin Wallet](https://github.com/BlockchainCommons/SmartCustody/blob/master/Docs/Case-Study-Sparrow.md)

  _**Alternative Signing Devices** (described later) offer procedures for using different hardware that our suggestions._

  _**Optional Steps** (described later) may require  purchases of additional items._

{pagebreak}

### Final State

Your material should be divided among four places: your home; secure storage in your home; offsite primary storage; and offsite secondary storage. The following shows the layout of materials that you'll keep in each if you use the default scenario with Sparrow as transaction coordinator and a Foundation Devices Passport and Gordon Seed Tool (GST) as signing devices, with a third, recovery key sharded.

| Home | Home Storage | Primary Storage | Secondary Storage | iCloud |
| :--- | :--- | :--- | :--- | :--- | 
|  | Backup SSKR Share #1 | Backup SSKR Share #2 | Backup SSKR Share #3 |
| Sparrow Computer |
| GST iPhone | | | | GST Backup |
|  | Passport | Passport MicroSD #1 | Passport MicroSD #2 |
| | Passport Backup Password | Passport PIN | iPhone PIN<br>Apple Account & Password<br>Apple Recovery Code|
| | Instructions for heirs | Duplicates of instructions for heirs |

Obviously this state will vary if alternative signing devices are chosen.

{pagebreak}

## The Basic Procedure

#### **Step A: Setup Storage Locales**

You will require two to three storage locales: Home Storage Locale, Primary Storage Locale, and Secondary Storage Locale[^6]. They will be used to store seeds and devices[^7]. 

1. [  ] Install Home Safe[^8][^9]
   1. Ideally, it should be physically secured by mounting it to floor or wall joists, or even more securely, directly to a foundation
   1. You will store an SSKR share in your Home Storage Locale, usually along with your Secondary Signing Device (by default: a Passport), if it's in regular usage.
2. [  ] Choose Primary Storage Locale
   1. Ideally, this should be a bank safety deposit box. But, if you don't have one, choose the most secure location you can think of outside of your house.
   1. You will store an SSKR share in your Primary Store Locale, might store your Secondary Signing Device (by default: a Passport) if it's not in regular usage, and possibly other backup material
3. [  ] Choose Secondary Storage Locale
   1. This may be a somewhat less secure locale that your Home Storage Locale and your Primary Storage Locale.
   1. Options include your work, your parent's house, a trusted friend's house.
   1. You will only store backups at your Secondary Storage Locale: an SSKR share and possibly other backup material

#### **Step B: Prepare Computer**

Because your computer never holds seeds, you don't need to do the same extensive work securing it as you might have with previous generations of signing devices. However, it's best to use a computer that you're careful with. If you have a computer that's not used much, and especially one that's not used for web browsing, that's a good choice[^10].

#### **Step C: Create Multisig**

#### **Step D: Create Backup Seed on Gordian Seed Tool**

[iCloud turned off; airplane mode]

[write SSKR to same MicroSD?]

#### **Step E: Verify Backup Seed**

#### **Step F: Create Active Seed on Passport**

#### **Step G: Create Active Seed on Gordian Seed Tool**

#### **Step H: Create Test Transaction**

#### **Step I: Transfer Funds**

#### **Step J: Prepare Instructions for Heirs and/or Executor**

#### **Step K: Check Primary Storage (Spring)**

write new backup for passport (to exercise card)

#### **Step L: Check Secondary Storage (Fall)**

---

[^1]: **What about the Wallets?** The term "wallet" has generally been horribly overloaded in the digital-asset space. Worse, the language discourages thinking about functional partition of different elements — such as partitioning key signing from transaction creation. This scenario thus avoids the term wallet, replacing its traditional usage with "transaction coordinator" and "signing device". The transaction coordinator is the software that creates transactions, manages signing, and sends the transaction. It's typically internet connected. The software used in this scenario is typically called the "Sparrow wallet", or a "software wallet", but it doesn't hold any keys in this example: it's a pure coordinator. Signing devices sign transactions that they're given, usually because they hold keys. The majority of signing devices, such as Ledger, Trezor, Keystone, and Passport have typically been called "hardware wallets".

[^2]: **Separating Keys.** This multisig scenario suggests the use of three keys, any two of which can be combined to use funds. A basic rule of thumb is to _never_ place seeds on the same device or network, because doing so turns it into a SPOC where a compromise of that network or device could then compromise your multisig, and thus your assets. Thus, though this scenario suggests the use of Gordian Seed Tool to create two different seeds, one active and one as a backup, they should _not_ be done on the same device. For the permanent key, we suggest use of your personal iPhone or else a brand-new iPod Touch, to make it optimally accessible and also optimally protected. For your recovery key, we suggest you use an older iPod Touch or even borrow a trusted partner's iPhone; you'll be deleting that key after you create it. In a pinch, you _could_ use the same iPhone or iPod Touch for both creating a recovery key and holding an active key, provided you were careful about deleting the recovery key, per the scenario instructions. However, if you're holding any notable funds, it's better to invest some money at the start to do this right: using the same device for two seeds, even chronologically separated, creates a SPOC.

[^3]: **Signing Device Generations.** First-generation signing devices tended to focus on support for single-sig addresses and tended to be direct-connected devices. The original [Ledger](https://www.ledger.com/) and [Trezor](https://trezor.io/) both fit into that category. The [Coldcard](https://coldcard.com/) was transitional, offering some of the first options to connect across airgaps, with a MicroSD slot, while still maintaining the port-connection paradigm. Second-generation signing devices are fully airgapped, with no ability to directly connect them to other devices. They transmit data via QR codes or MicroSD cards. the [Foundation Devices Passport](https://foundationdevices.com/passport/details/) and the [Keystone Pro](https://keyst.one/) are both second-generation signing devices. 

[^4]: **Why Airgaps?** Optimal safety of a seed means ensuring that the device holding the key can't be corrupted and that the seed (or even hints about the seed) can't slip off the device. Any type of live connection can be dangerous, because even if a stream is purely intended for data, a buffer overflow or other error might send return data back across the connection without intervention of the users. Airgaps not only ensure data is in the maximally constrained form, thanks to use of a QR code or a MicroSD data file, but they also ensure that the user can see any data that's being sent back in return, and OK that sending or not. Of course, this also depends on airgapped devices being very precise and complete in revealing what data they receive and what data they send.

[^5]: **Why Passport and Seed Tool?** We choose Passport and Gordian Seed Tool as second-generation signing devices that have fully integrated backup mechanisms: Passport to MicroSD, Seed Tool to iCloud. We've thus combined the protection against SPOC implicit in an airgapped design  with the protection against SPOF supported by a backup that the user doesn't have to think (much) about.

[^6]: **Locale Security.** Obviously, the more secure locations are, the better. Optimal setup would be to have a robust Home Safe and two safety deposit boxes in banks in two widely separated locales. However, we expect most people will choose their locales as home, bank, and work; or else as home, work, and family/friend home. The most important factor for the overall security of your scenario may not be physical security of the locale, but instead geographical separation, ensuring that no single disaster such as an earthquake or wildfire and no single event such as a war or civil unrest, could easily compromise two locales.

[^7]: **Why Isn't Security the Biggest Factor?** No single locale should have enough information to access your funds in an unlocked way. Your home is the biggest danger because it holds two keys, but they should both be locked, either by PIN or biometrics. Each other locale holds at most one and a third keys, the full key locked.

[^8]: **Safe Usage.** Note that most home safes do not offer enough [Disaster](#adversary-disaster) resistance to sufficiently protect your digital assets. At best they are rated to protect paper against fire. The primary goal of a home safe is to protect any Signing Device kept at home that is not in active use and to store one share of your SSKR, so that neither can easily be lost or stolen. Stealing would likely not compromise your funds, but it would put you on the path to losing control of those funds if disaster struck another locale.

[^9]: **Safe Optional.** The use of a safe is somewhat optional: you will have enough seeds at home to compromise your funds, but they should each be locked by PINs or biometrics, making such compromise unlikely. It's recommended, and it's better to have it, but don't give up on this procedure just because you don't have a home safe. 

[^10]: **Computer Choices.** Everything's a balance. If you can choose a computer that doesn't get much use, that's more secure, but you also want to make sure that it's a computer that will stay up to date with security updates. If the computer is no longer being supported with security updates, that's a bad choice. The biggest danger if your computer is compromised is that your transaction coordinator may be compromised and it will send you incorrect PSBTs for signing. So _always_ look carefully at any PSBTs that you're signing, and be even more careful if your computer is less secure through other usage.
