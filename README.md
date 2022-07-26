# Introduction

This is the developer-focused documentation portal for the Fuse platform. More high-level documentation for Fuse is available [here](https://docs.fuse.io).&#x20;

Fuse is a decentralized blockchain-powered platform and technology stack whose goal is to enable genuine mass adoption of crypto payments and decentralized finance (DeFi).&#x20;

Its main components are the Fuse Network [blockchain](https://docs.fuse.io/general/fuse-network-blockchain), the mobile-centric [infrastructure](https://docs.fuse.io/general/fuse-infrastructure) for seamless creation of token communities and a set of reference decentralized finance (DeFi) [tools](./#fuse-services).

## Fuse Network

The EVM-compatible Fuse Network blockchain is the foundation of the Fuse platform. The information on this portal will help you:

* Learn how to [run various network nodes](https://developers.fuse.io/fuse-dev-docs/network/how-to-run-network-nodes)
* Learn how to [become a validator](https://developers.fuse.io/fuse-dev-docs/network/how-to-become-a-validator)
* Learn about [Fuse Consensus](https://developers.fuse.io/fuse-dev-docs/network/how-to-become-a-validator) and how to participate in it
* Learn about [network upgrades](https://developers.fuse.io/fuse-dev-docs/network/network-upgrades) and how to implement them

## Fuse API

Fuse provide a bundle of API's to access and perform community-centric payments on the Fuse Network. Most of the API do require an economy set up on Fuse Studio.

* [Token API](legacy-studio-api-deprecated/token-api.md) - fetching economy tokens
* [Economy API](legacy-studio-api-deprecated/economy-api.md) - accessing and manipulating the economy details
* [Wallet API](legacy-studio-api-deprecated/wallet-api.md) - accessing and deploying user wallets
* [Jobs API](legacy-studio-api-deprecated/jobs-api.md) - task execution API
* [Admin API ](legacy-studio-api-deprecated/jobs-api.md)- performing community payments.
* [Trade API](legacy-studio-api-deprecated/trade-api.md) - trading tokens and executing swaps

## Fuse Services

Fuse offers application developers several backend services that expose APIs that can be used by anyone seeking to build on Fuse. Although some functionalities do require a dedicated API key or access token.

### Fuse Studio

Fuse Studio is the platform for creating, building and managing economies. The Fuse Studio playground [interface](https://studio.fuse.io) enables the creation and management of token communities without coding but for more sophisticated use cases [Fuse API](./#fuse-api) is available.

### Trading Service

Voltage Finance is the first Fuse-native decentralized exchange (DEX). The Fuse team makes available an auxiliary [service](https://developers.fuse.io/fuse-dev-docs/fuse-studio/fuseswap-service) to query prices and stats on it.

### The Graph

Fuse's integration with The Graph enables the indexing of smart contract transactions on Fuse Network through the creation of [subgraphs](https://thegraph.academy/developers/defining-a-subgraph/). The Fuse team maintains a set of [Fuse subgraphs](https://developers.fuse.io/fuse-dev-docs/fuse-studio/subgraphs) that can also be used by external developers.&#x20;

### Earn SDK

[Earn SDK](https://developers.fuse.io/fuse-dev-docs/fuse-studio/earn-sdk) is a client-server SDK for building applications that can interact with various earning functionalities on Fuse.



## Important Smart Contracts

Certain smart contracts on Fuse Network and other EVM-compatible chains may be useful for application developers building on top of Fuse. These include:

* The [contracts](https://developers.fuse.io/fuse-dev-docs/important-smart-contracts/fuse-token) for the Fuse Token on other chains
* The [smart contracts](https://developers.fuse.io/fuse-dev-docs/important-smart-contracts/bridges) for Fuse bridges
* The [FuseDollar contracts](https://developers.fuse.io/fuse-dev-docs/important-smart-contracts/fuse-dollar)

## Fuse Wallet

The Fuse team has developed an open-cource, easily forkable and customizable mobile crypto wallet that developers can use to create wallets to serve as frontends for the token communities created via the Studio.

[Learn](https://developers.fuse.io/fuse-dev-docs/fuse-wallet/getting-started) how to run the wallet and customize it by forking.

