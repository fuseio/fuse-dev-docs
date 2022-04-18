# Token API

Base URL: [https://studio.fuse.io/api/v1](https://studio.fuse.io/api/v1)

### Adding new token

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v1.md#top)

Tokens are compatible with the ERC20 standard, and they also can be burnable/mintable. Tokens are an important part of the community economy.

```
GET /tokens/:address
```

#### Parameter Parameters

| Name        | Type     | Description                               |
| ----------- | -------- | ----------------------------------------- |
| address     | `String` | Token address to add                      |
| networkType | `String` | The network of the token (body parameter) |

#### Examples

Adding DAI token on mainnet:

```
POST /tokens/0x6b175474e89094c44da98b954eedeac495271d0f
body: { networkType: mainnet }
```

#### Success 200

| Name           | Type     | Description                                                  |
| -------------- | -------- | ------------------------------------------------------------ |
| address        | `String` | Token's address                                              |
| name           | `String` | Token's name                                                 |
| symbol         | `String` | Token's symbol                                               |
| tokenURI       | `String` | IPFS URI points to token metadata                            |
| totalSupply    | `String` | Token's total supply                                         |
| owner          | `String` | Token's owner                                                |
| factoryAddress | `String` | Factory contract that created the token                      |
| blockNumber    | `String` | Block number of the token's creation                         |
| tokenType      | `String` | Token type: basic/mintableBurnable/imported                  |
| networkType    | `String` | Network type where the token is issued: mainnet/ropsten/fuse |

### Fetch token <a href="#user-content-fetch-token" id="user-content-fetch-token"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v1.md#top)

Tokens are compatible with the ERC20 standard, and they also can be burnable/mintable. Tokens are an important part of the community economy.

```
GET /tokens/:address
```

#### Parameter Parameters

| Name    | Type     | Description   |
| ------- | -------- | ------------- |
| address | `String` | Token address |

#### Success 200

| Name           | Type     | Description                                                  |
| -------------- | -------- | ------------------------------------------------------------ |
| address        | `String` | Token's address                                              |
| name           | `String` | Token's name                                                 |
| symbol         | `String` | Token's symbol                                               |
| tokenURI       | `String` | IPFS URI points to token metadata                            |
| totalSupply    | `String` | Token's total supply                                         |
| owner          | `String` | Token's owner                                                |
| factoryAddress | `String` | Factory contract that created the token                      |
| blockNumber    | `String` | Block number of the token's creation                         |
| tokenType      | `String` | Token type: basic/mintableBurnable/imported                  |
| networkType    | `String` | Network type where the token is issued: mainnet/ropsten/fuse |

### Fetch tokens <a href="#user-content-fetch-tokens" id="user-content-fetch-tokens"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v1.md#top)

```
GET /tokens
```

#### Parameter Parameters

| Name        | Type     | Description                |
| ----------- | -------- | -------------------------- |
| networkType | `String` | mainnet/ropsten/fuse       |
| page        | `Number` | Page number for pagination |

#### Success 200

| Name | Type       | Description                                            |
| ---- | ---------- | ------------------------------------------------------ |
| -    | `Object[]` | List of Tokens. See GetToken endpoint for token fields |

### Fetch tokens by owner <a href="#user-content-fetch-tokens-by-owner" id="user-content-fetch-tokens-by-owner"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v1.md#top)

```
GET /tokens/owner/:owner
```

#### Parameter Parameters

| Name        | Type     | Description                        |
| ----------- | -------- | ---------------------------------- |
| owner       | `String` | account address of the token owner |
| networkType | `String` | mainnet/ropsten/fuse               |

#### Success 200

| Name | Type       | Description                                            |
| ---- | ---------- | ------------------------------------------------------ |
| -    | `Object[]` | List of Tokens. See GetToken endpoint for token fields |
