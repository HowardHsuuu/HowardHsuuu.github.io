---
title: "OTSea Staking - lost 26k"
date: 2024-09-25T23:06:01+08:00
draft: false
tags: ["DeFi Security"]
---

## What happened

Staking contract, OTSeaStaking, hacked and lost 26k. Hacker exploited the contract's logic flaw, which allowed him/her to call "withdraw" many times and got a lot more tokens than he staked.

## The problem

In [line 396 of OTSeaStaking.sol](https://etherscan.io/address/0x5da151b95657e788076d04d56234bd93e409cb09#code#F21#L396), you can see that `deposit.amount` is not handled properly (not decreased); therefore, one can deposit once and withdraw multiple times.

## PoC

The PoC of this incident I wrote can be found [here](https://github.com/HowardHsuuu/DeFiHackLabs?tab=readme-ov-file#20240913-OTSeaStaking---Logic-Flaw)

## Reference
- [transaction hash](https://app.blocksec.com/explorer/tx/eth/0x90b4fcf583444d44efb8625e6f253cfcb786d2f4eda7198bdab67a54108cd5f4)
- https://nickfranklin.site/2024/09/13/otsea-staking-hacked/