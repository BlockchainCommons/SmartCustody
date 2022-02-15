# Multisig Self-Custody Scenario

#### _Best practices for protecting Your personal digital assets using a multi-sig_

## Introduction to the Multisig Scenario

Digital assets held personally ("self-custody") face two major dangers: single point of failure (SPOF) and single point of compromise (SPOC), which is to say losing those assets either those loss or theft. Traditional self-custody solutions focus on decreasing SPOF with methodologies like seed backup, but in doing so tend to increase the possibility of SPOC. This is generally in tune with the adversaries that the average self-custodian would be facing. However, now that multisig is sufficiently deployed to allow ease-of-use, it can simultaneously decrease both SPOF and SPOC at a relatively small cost to convenience and complexity. This scenario explains how to do so.

### About The Base Scenario

The base scenario presumes an audience with all of the following characteristics:

* A holder with a significant amount of digital assets (>10% of net worth);
    - with full and legal custody of the assets and no fiduciary responsibility to others;
    - and 100% of those assets shared with a spouse, if present, in estate planning.
* A holder who might be trading those assets actively or might be holding them long temr.
* A holder who lives in the first world, and thus is less concerned about issues like government attack, kidnapping, or privacy violations.
* A holder who has sufficient computer skills to comfortably install and run apps.

This scenario advocates the basic procedure to address XXX major types of adversaries, while the optional procedures can help protect against XXX further adversaries. Additional categories of "Non-Theft Crimes", "Loss by Government" and "Privacy-Related" adversaries are not strongly considered in this scenario. See **Adversaries**.

For simplicity, this document focuses on Bitcoin, but is easily adaptable to other digital assets supported by our suggested hardware wallet.

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

The following items are necessary for this procedure, and should be purchased in advance of your setting up this scenario.[^1].

* [  ] Small Home Safe (For example: [https://www.amazon.com/AmazonBasics-Security-Safe-0-5-Cubic-Feet/dp/B00UG9HB1Q/](https://www.amazon.com/AmazonBasics-Security-Safe-0-5-Cubic-Feet/dp/B00UG9HB1Q/) ) [^safe]
* [  ] Safety Deposit Box at Bank or other institution
* [  ] Existing Laptop or Desktop Computer capable of running [Sparrow Wallet(https://sparrowwallet.com/).
* [  ] 1 Package Waterproof Laser Paper (TerraSlate, made of 1-PET [https://www.amazon.com/TerraSlate-Paper-Waterproof-Printer-Sheets/dp/B00NWVGOF4](https://www.amazon.com/TerraSlate-Paper-Waterproof-Printer-Sheets/dp/B00NWVGOF4) or Rite in the Rain All-Weather Copier Paper, made of coated recyclable wood [https://www.amazon.com/Rite-Rain-All-Weather-Copier-8511/dp/B0016H1RYE/](https://www.amazon.com/Rite-Rain-All-Weather-Copier-8511/dp/B0016H1RYE/) or equivalent)

Three devices are required to hold seeds: two live devices and one temporary device. We suggest the following:

* [  ] [Foundation Devices Passport](https://foundationdevices.com/passport/details/)
* [  ] iPhone or iPod to run [Gordian Seed Tool](https://apps.apple.com/us/app/gordian-seed-tool/id1545088229) for active seed.
* [  ] Separate[^1] iPhone or iPod to temporarily create and shard seed using [Gordian Seed Tool](https://apps.apple.com/us/app/gordian-seed-tool/id1545088229).

The two live devices are both selected because they are second-generation wallet technology[^2]. Also see the footnotes for discussions of why we choose these specifically[^4]. 
Please see our footnotes on the Ledger[^3] and the CryptoTag[^4] for discussions of why we choose that hardware over other alternatives.

  _**Optional Steps** (described later) may require  purchases of additional items._

{pagebreak}

### Final State

[revise]
This procedure will secure your Bitcoin private keys by keeping the more sensitive information in a safety deposit box and the less sensitive information in a home safe, as follows:

| Home Safe | Safe Deposit Box |
| :--- | :--- |
| Ledger Device #1 | Ledger Device #2 |
|  | Ledger PIN |
|  | Paper 24-word seed |
|  | CryptoTag 24-word seed |
| Instructions for heirs and xpub and cold storage addresses | Duplicates of instructions for heirs and xpub and cold storage addresses |

{pagebreak}

## The Basic Procedure

#### **Step A: Setup Safes**

[^1] **Separating Keys.** This multisig scenario suggests the use of three keys, any two of which can be combined to use funds. A basic rule of thumb is to _never_ place seeds on the same device or network, because doing so turns it into a SPOC where a compromise of that network or device could then compromise your multisig, and thus your assets. Thus, though this scenario suggests the use of Gordian Seed Tool to create two different seeds, one active and one as a backup, they should _not_ be done on the same device. For the permanent key, we suggest use of your personal iPhone or else a brand-new iPod Touch, to make it optimally accessible and also optimally protected. For your backup key, we suggest you use an older iPod Touch or even borrow a trusted partner's iPhone; you'll be deleting that key after you create it. In a pinch, you _could_ use the same iPhone or iPod Touch for both creating a backup key and holding an active key, provided you were careful about deleting the backup key, per the scenario instructions. However, if you're holding any notable funds, it's better to invest some money at the start to do this right: using the same device for two seeds, even chronologically separated, creates a SPOC.
