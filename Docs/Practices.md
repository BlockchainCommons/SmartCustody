# SmartCustody Practice

Following are a lit of best practices, both how users can maintain the resilience of their digital assets and how developers can aid them in doing so with UX and other practices.

## User Practices

### Label Your Seedstores

Best practice is to keep your seeds or keys is disconnected devices separate from your networked transaction coordinator. However, if you do so, you must know where to go to access your keys when you want to send a transaction. Make sure that you take advantage of any labeling capability within your network coordinator to very precisely note where each keystore is. Don't be afraid of writing something as precise as "Trezor T" or "Ledger Nano S".

Yes, you may feel that this makes you vulnerable, but practically you are much more likely to lose money accidentally than as a result of theft, unless you have a very large cryptourrency account (and maybe even then). Beyond that, it's likely that all of your devices are pretty by passwords and/or biometrics, so that even if someone knew what devices to use, they couldn't.

At the least, write them down somewhere and store it ... but it's better to have them in your transaction coordinator to maximize its accessibility to you.

### Keep Your Cords

If your hardware wallets have special cords (anything but USB-A or USB-C), keep those cords with the wallets. Do this even if means that you have to buy extra cords. Having to search for cords when you want to use a wallet will just discourage you from maintaining the #SmartCustody of your assets.

## Developer Practices

### Separate Seeds & Keys

Seeds should be solely used to derive keys, not used as keys themselves.

The reason for not using seeds as keys is to avoid collision and reuse with other keys derived from that seed. As most people can only afford the time to properly backup one seed,  asking them to store lots of seeds is risky. Fortunately there are lots of options to help backup BIP39 mnemonics and derive keys from them safely.

At a bare minimum, you should derive a key from the seed by using a `pbdkf` function with a constant. Some good, reviewed code for this is available in [bc-crypto-base](https://github.com/BlockchainCommons/bc-crypto-base). Alternatively, use a well-vetted BIP32 library such as [libwally-core](https://github.com/ElementsProject/libwally-core) and register a BIP32 derivation path with a cointype for your usage: BIP32 has the advantage of supporting the ability in the future to have simple revocation or rotation case keys, as you can use key index 0 by default, and rotate to key index 1+ later.
