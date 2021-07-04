---
description: >-
  GoodDollar bridge is used to relay the GoodDollar tokens between Fuse and
  Ethereum networks.
---

# Ethereum ↔ Fuse GoodDollar Token

## Architecture Overview

This bridge is two layer bridge. In the base level the  Arbitrary Message Bridge \(AMB\) is responsible for relaying messages between the networks. On top of the AMB,  the pluggable mediators implement a contract logic of token relaying of various assets. More info [https://docs.tokenbridge.net/amb-bridge/about-amb-bridge](https://docs.tokenbridge.net/amb-bridge/about-amb-bridge)

## Contracts

Home side of the bridge on the Fuse network: [0xD39021DB018E2CAEadb4B2e6717D31550e7918D0](https://explorer.fuse.io/address/0xD39021DB018E2CAEadb4B2e6717D31550e7918D0/transactions)

Foreign side of the bridge on the Ethereum network: [0xD5D11eE582c8931F336fbcd135e98CEE4DB8CCB0](https://etherscan.io/address/0xD5D11eE582c8931F336fbcd135e98CEE4DB8CCB0)

GoodDollar token on the Fuse network: [0x495d133b938596c9984d462f007b676bdc57ecec](https://explorer.fuse.io/address/0x495d133B938596C9984d462F007B676bDc57eCEC/transactions)

GoodDollar token on the Ethereum network: [0x67c5870b4a41d4ebef24d2456547a03f1f3e094b](https://etherscan.io/address/0x67c5870b4a41d4ebef24d2456547a03f1f3e094b)

Home side of the AMB bridge on the Fuse network: [0x2CA5411c4bf447Cc27CD6E6d1d046f922A27C399](https://explorer.fuse.io/address/0x2CA5411c4bf447Cc27CD6E6d1d046f922A27C399/transactions)

Foreign side of the AMB bridge on the Ethereum network: [0x63C47c296B63bE888e9af376bd927C835014039f](https://etherscan.io/address/0x63C47c296B63bE888e9af376bd927C835014039f)

## Source Code

{% embed url="https://github.com/fuseio/tokenbridge-contracts" %}

## How to use

Any ERC20 token can be bridged for Ethereum to the Fuse Network. If the token is relayed for the first time. A bridged token, paired with the original token, will be created on the Fuse network. 

To send token from the Ethereum network:

1. Approve the ERC20 tokens to be spent by the Foreign ERC20 bridge. 
2. Call relayTokens function on the bridge contract

the `relayTokens` method will lock the ERC20 tokens on the foreign bridge. After a couple of confirmations, an equal amount of the Fuse ERC20 token will be sent from the home bridge contract.

To send tokens from Fuse network

1. Approve the ERC20 tokens to be spent by the Home ERC20 bridge. 
2. Call `relayTokens` function on the bridge contract

the `relayTokens` method will lock the bridged tokens on the home bridge. Then, an equal amount of the paired ERC20 token will be sent from the foreign bridge contract.



