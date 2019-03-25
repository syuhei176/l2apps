# l2apps

About Application specific scalings in L2.
These are very rough idea, there might be some flaws.

## Introduction

Thinking about smart contract in L2 that do not lose the expressive power of L1 beyond existing L2 solutions.
L2apps require transactions on chain as little as possible and inherit L1's security guarantee.

## Examples

### Atomic Swap with No Online Requirement in L2

* The atomic swap in Plasma require exchanging "confirmation signature" after the transaction submitted. So users need to be online.
* If users have full node, we can skip confirmation signature process by following way
  * Alice and Bob swap their coins. Alice has coinA and Bob has coinB.
  * Bob is malicious party, coinB has invalid history. It means the real owner of coinB is not Bob.
  * In current Plasma, Alice loses without confirmation signature, Bob get coinA but Alice get nothing.
  * So we add new exit-game method. If we show invalid behavior by "invalid history challenge" or "double spending", Alice can remove the atomic swap transaction from block. The last valid transaction in coinB is before "atomic swap"

### Commit & Reveal

* Commit and reveal in state channel(or channel on Plasma) is available.
* Is commit and reveal with more users available?
* Commit phase can be easily compressed. This is Plasma construction.
* Reveal phase are partially mergeable.
  * But user should be able to reveal on chain at any time.

### Lending

* Alice lend ETH to Bob. Bob's collateral is NFT.
* Bob can get NFT when he return ETH.
* Problem of lending in Plasma is that Bob can't get NFT without Alice's signature.
* Maybe it's available very small plasma construction by "Atomic Swap with No Online Requirement in L2"
