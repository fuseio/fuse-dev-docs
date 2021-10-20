---
description: >-
  Fuse native bridge is used to relay the Fuse native token between Fuse and
  Ethereum networks
---

# Ethereum ↔ Fuse Native

Fuse native bridge between Ethereum and Fuse is used to relay the Fuse native token from Fuse to Ethereum network

## Architecture Overview

The Fuse bridged is based on POA's bridge implementation, it is used to transfer Fuse tokens between the Fuse chain and the Ethereum network.

Tokens sent to the respective bridge contract on one network (whether it's Fuse or Ethereum) are "locked" in the bridge, "unlocked" on the other network bridge and transferred to the sender. The bridge contracts are deployed on both networks, and bridge oracle processes run on each validators machine as part of the validator deployment stack.

Besides the transfer of Fuse tokens between the two networks, the bridge is also responsible for network core functionality events of relaying the block rewards to the Ethereum network.

**Mint block reward distributed on the Fuse chain on Ethereum**

Each cycle the total block reward distributed on Fuse chain is minted on Ethereum and locked on the bridge contract.

This works by listening to the \`RewardedOnCycle\` event emitted by the BlockReward contract on Fuse chain, waiting for all bridge validators on Fuse chain to sign it, and eventually sending a transaction to mint on Ethereum (by the last signing validator).

## Contracts

Home side of the bridge on the Fuse network: [0xd617774b9708F79187Dc7F03D3Bdce0a623F6988](https://explorer.fuse.io/address/0xd617774b9708F79187Dc7F03D3Bdce0a623F6988/transactions)

Foreign side of the bridge on the Ethereum network: [0x3014ca10b91cb3D0AD85fEf7A3Cb95BCAc9c0f79](https://explorer.fuse.io/address/0x3014ca10b91cb3D0AD85fEf7A3Cb95BCAc9c0f79/transactions)

Fuse token on the Ethereum network: [0x970B9bB2C0444F5E81e9d0eFb84C8ccdcdcAf84d](https://etherscan.io/token/0x970b9bb2c0444f5e81e9d0efb84c8ccdcdcaf84d)

## Source Code

{% embed url="https://github.com/fuseio/fuse-bridge/tree/master/native-to-erc20/contracts" %}

## How to use

On Fuse Network you send native Fuse token to the home bridge contract. Then you receive an equal amount of the Fuse token on the Ethereum network, sent from the foreign bridge contract

On Ethereum network you transfer the Fuse token to the foreign bridge contract. After a couple of confirmations, you will receive equal amount of the Fuse native token, sent from the home bridge contract.

####
