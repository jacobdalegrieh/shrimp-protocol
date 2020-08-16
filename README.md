# (Emoji  Shrimp Protocol  Emoji)
## The Protocol

Shrimp is an experimental protocol building upon the most exciting innovations in programmable money and governance. Built primarily from the fork of YAM, but without the rebases, bugs and governance treasury:

At its core, YAM is an elastic supply cryptocurrency, which expands and contracts its supply in response to market conditions, initially targeting 1 USD per YAM. This stability mechanism includes one key addition to existing elastic supply models such as Ampleforth: a portion of each supply expansion is used to buy yCurve (a high-yield USD-denominated stablecoin) and add it to the Yam treasury, which is controlled via Yam community governance.

We have built Yam to be a minimally viable monetary experiment, and at launch there will be zero value in the YAM token. After deployment, it is entirely dependent upon YAM holders to determine its value and future development. We have employed a fork of the Compound governance module, which will ensure all updates to the Yam protocol happen entirely on-chain through community voting.

## Audits

As with YAM there has been none. Contributors have given their best efforts to ensure the security of these contracts, but make no guarantees. It has been spot checked by just a few pairs of eyes. It is a probability - not just a possibility - that there are bugs. That said, minimal changes were made to the staking/distribution contracts that have seen hundreds of millions flow through them in YAM through their own derivatives and the same now for Shrimp where you can stake with/distribute DICE, COMP, CREAM, YFI to name a few. The reserve contract is excessively simple as well. We prioritized staked assets' security first and foremost.

The original devs encourage governance to fund a bug bounty/security audit

The token itself is largely based on COMP which have undergone audits - but we made non-trivial changes.

Unlike YAM there is no longer a rebaser therefore we don't have to worry about the bugs that we're apparent with YAM

If you feel uncomfortable with these disclousures, don't stake or hold SHRIMP. If the community votes to fund an audit, or the community is gifted an audit, there is no assumption that the original devs will be around to implement fixes, and is entirely at their discretion.

## The Token
The core SHRIMP token uses WETH as the reserve currency, which is roughly a $1 peg. Tokens cannot be minted.

## Distribution
Rather than allocating a portion of the supply to the founding team, SHRIMP is being distributed in the spirit of YAM and YFI: no premine, no founder shares, no VC interests — simply equal-opportunity staking distribution to attract a broad and vision-aligned community to steward the future of the protocol and token.

The initial distribution of SHRIMP will be evenly distributed across six staking pools: WETH, YFI, COMP, DICE, CREAM and WETH/SHRIMP Uniswap v2 LP tokens. These pools were chosen intentionally to reach a broad swath of the overall DeFi community, as well as specific communities with a proven commitment to active governance and an understanding of complex tokenomics.


# Development
### Building
This repo uses truffle. Ensure that you have truffle installed. Given the composability aspect of this

Then, to build the contracts run:
```
$ truffle compile
```



To run tests, run against a single test package, i.e.:
```
$ sh startBlockchain.sh
$ truffle migrate --network distribution
$ python scripts/clean.py
$ cd jsLib
$ jest deployment
$ jest token
$ jest distribution
```
The need to run one-by-one seems to be a limitation of jest + ganache.

The distribution tests require specific tokens. These are acquired by using the ganache unlock_account function. If you receive fails, the owner likely decreased their ownership of that token. Just replace any instances of that address with another holder of the token.

Note: some governance tests require a different ganache setup. You will encounter a warning (but not a failed test) if the wrong type of ganache is setup. To run the correct one:
```
$ sh startBlockchainMining.sh
$ truffle migrate --network distribution
$ python scripts/clean.py
$ cd jsLib
$ jest governance
```


#### Attributions
Much of this code base is modified from existing works, including:

[YAM] (https://yam.finance) - The original farming token

[Compound](https://compound.finance) - Jumping off point for token code and governance

[YEarn](https://yearn.finance)/[YFI](https://ygov.finance) - Initial fair distribution implementation
