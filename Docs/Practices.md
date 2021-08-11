# SmartCustody Practice

## Separate Seeds & Keys

Seeds should be solely used to derive keys, not used as keys themselves.

The reason for not using seeds as keys is to avoid collision and reuse with other keys derived from that seed. As most people can only afford the time to properly backup one seed,  asking them to store lots of seeds is risky. Fortunately there are lots of options to help backup BIP39 mnemonics and derive keys from them safely.

At a bare minimum, you should derive a key from the seed by using a `pbdkf` function with a constant. Some good, reviewed code for this is available in [bc-crypto-base](https://github.com/BlockchainCommons/bc-crypto-base). Alternatively, use a well-vetted BIP32 library such as [libwally-core](https://github.com/ElementsProject/libwally-core) and register a BIP32 derivation path with a cointype for your usage: BIP32 has the advantage of supporting the ability in the future to have simple revocation or rotation case keys, as you can use key index 0 by default, and rotate to key index 1+ later.
