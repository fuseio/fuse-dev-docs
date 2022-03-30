# Admin API

Base URL: [https://studio.fuse.io/](https://studio.fuse.io)

### Burn tokens

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Start async job of burning tokens

```
POST /api/v2/admin/tokens/burn
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name         | Type     | Description                            |
| ------------ | -------- | -------------------------------------- |
| tokenAddress | `String` | Token address to burn (body parameter) |
| networkType  | `String` | Token's network (must be Fuse)         |
| amount       | `String` | Token amount to burn                   |
| from         | `String` | account to burn from (optional)        |

#### Query Parameters

| Name   | Type     | Description                       |
| ------ | -------- | --------------------------------- |
| apiKey | `String` | API key is used to access the API |

#### Examples

Burn 1.1 tokens on Fuse network

```
POST /api/v2/admin/tokens/burn
body: { tokenAddress: '0xbAa75ecD3Ea911c78A23D7cD16961Eadc5867d2b', networkType: 'fuse', amount: '1.1' }
```

#### Success 200

| Name    | Type     | Description |
| ------- | -------- | ----------- |
| Started | `String` | job data    |

### Get burn events <a href="#user-content-get-burn-events" id="user-content-get-burn-events"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Get burn events created by admin

```
POST /api/v2/admin/tokens/burnEvents
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name        | Type     | Description                    |
| ----------- | -------- | ------------------------------ |
| fromWallet  | `String` |                                |
| startTime   | `String` |                                |
| endTime     | `String` |                                |
| networkType | `String` | Token's network (must be Fuse) |

#### Query Parameters

| Name   | Type     | Description                       |
| ------ | -------- | --------------------------------- |
| apiKey | `String` | API key is used to access the API |

#### Examples

GET /api/v2/admin/tokens/burnEvents

```
GET /api/v2/admin/tokens/burnEvents
body: { fromWallet: '0x755c33BE69dD2baB7286E7a2010fc8591AF15a1e', networkType: 'fuse' }
```

### Create token <a href="#user-content-create-token" id="user-content-create-token"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Start async job of creating a token

```
POST /api/v2/admin/tokens/create
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name            | Type     | Description                                                                       |
| --------------- | -------- | --------------------------------------------------------------------------------- |
| name            | `String` | Token name                                                                        |
| symbol          | `String` | Token symbol                                                                      |
| initialSupply   | `String` | Token initial supply (in ETH)                                                     |
| uri             | `String` | Token URI (metadata)                                                              |
| expiryTimestamp | `String` | Token expiry timestamp after which cannot transfer (Unix epoch time - in seconds) |
| spendabilityIds | `String` | Token spendability ids (comma-seperated list)                                     |
| networkType     | `String` | Token's network (must be Fuse)                                                    |

#### Query Parameters

| Name   | Type     | Description                       |
| ------ | -------- | --------------------------------- |
| apiKey | `String` | API key is used to access the API |

#### Examples

Create a token on Fuse network

```
POST /api/v2/admin/tokens/create
body: { name: 'MyCoolToken', symbol: 'MCT', initialSupply: '100', uri: 'ipfs://hash', expiryTimestamp: 1585036857, spendabilityIds: 'a,b,c', networkType: 'fuse' }
```

#### Success 200

| Name    | Type     | Description |
| ------- | -------- | ----------- |
| Started | `String` | job data    |

### Create wallet for phone number <a href="#user-content-create-wallet-for-phone-number" id="user-content-create-wallet-for-phone-number"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Start async job of creating a wallet for phone number (owned by the community admin)

```
POST /api/v2/admin/wallets/create
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name        | Type     | Description                                          |
| ----------- | -------- | ---------------------------------------------------- |
| phoneNumber | `String` | phone number to create a wallet for (body parameter) |

#### Query Parameters

| Name   | Type     | Description                       |
| ------ | -------- | --------------------------------- |
| apiKey | `String` | API key is used to access the API |

#### Examples

Create wallet for the provided phone number

```
POST /api/v2/admin/wallets/create
body: { phoneNumber: '+972546123321' }
```

#### Success 200

| Name    | Type     | Description |
| ------- | -------- | ----------- |
| Started | `String` | job data    |

### Get expired by wallet/token/spendabilityId <a href="#user-content-get-expired-by-wallet-token-spendabilityid" id="user-content-get-expired-by-wallet-token-spendabilityid"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Get expired balance for one/multiple wallets by token or spendabilityId

```
POST /api/v2/admin/tokens/expired
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name           | Type     | Description                    |
| -------------- | -------- | ------------------------------ |
| walletAddress  | `String` |                                |
| tokenAddress   | `String` |                                |
| spendabilityId | `String` |                                |
| networkType    | `String` | Token's network (must be Fuse) |

#### Query Parameters

| Name   | Type     | Description                       |
| ------ | -------- | --------------------------------- |
| apiKey | `String` | API key is used to access the API |

#### Examples

GET /api/v2/admin/tokens/expired

```
GET /api/v2/admin/tokens/expired
body: { walletAddress: '0x755c33BE69dD2baB7286E7a2010fc8591AF15a1e', tokenAddress: '0xbAa75ecD3Ea911c78A23D7cD16961Eadc5867d2b', networkType: 'fuse' }
```

### Get token jobs by address on fuse <a href="#user-content-get-token-jobs-by-address-on-fuse" id="user-content-get-token-jobs-by-address-on-fuse"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Get token transfer events by address on fuse

```
GET api/v2/admin/wallets/transfers/tokentx/:walletAddress
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name           | Type     | Description                          |
| -------------- | -------- | ------------------------------------ |
| tokenAddress   | `String` | Address of the token                 |
| fromBlockNumer | `String` | The block number to start fetch from |

#### Query Parameters

| Name   | Type     | Description                       |
| ------ | -------- | --------------------------------- |
| apiKey | `String` | API key is used to access the API |

#### Success 200

| Name | Type     | Description   |
| ---- | -------- | ------------- |
| data | `Object` | Array of jobs |

### Mint tokens <a href="#user-content-mint-tokens" id="user-content-mint-tokens"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Start async job of minting tokens

```
POST /api/v2/admin/tokens/mint
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name         | Type     | Description                            |
| ------------ | -------- | -------------------------------------- |
| tokenAddress | `String` | Token address to mint (body parameter) |
| networkType  | `String` | Token's network (must be Fuse)         |
| amount       | `String` | Token amount to mint                   |
| toAddress    | `String` | account to transfer to                 |

#### Query Parameters

| Name   | Type     | Description                       |
| ------ | -------- | --------------------------------- |
| apiKey | `String` | API key is used to access the API |

#### Examples

Minting 1.1 tokens on Fuse network

```
POST /api/v2/admin/tokens/mint
body: { tokenAddress: '0xbAa75ecD3Ea911c78A23D7cD16961Eadc5867d2b', networkType: 'fuse', amount: '1.1' }
```

#### Success 200

| Name    | Type     | Description |
| ------- | -------- | ----------- |
| Started | `String` | job data    |

### Transfer tokens from account <a href="#user-content-transfer-tokens-from-account" id="user-content-transfer-tokens-from-account"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Start async job of transferring tokens from account (owned by community admin)

```
POST /api/v2/admin/tokens/transfer
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name              | Type     | Description                                                                       |
| ----------------- | -------- | --------------------------------------------------------------------------------- |
| tokenAddress      | `String` | Token address to transfer (body parameter)                                        |
| spendabilityIds   | `String` | Token spendability ids (comma-seperated list) - if sent, no need for tokenAddress |
| spendabilityOrder | `String` | Token spendability order (asc/desc) - mandatory if using spendabilityIds          |
| networkType       | `String` | Token's network (must be Fuse)                                                    |
| amount            | `String` | Token amount to transfer                                                          |
| from              | `String` | account to transfer from                                                          |
| to                | `String` | address to transfer to                                                            |

#### Query Parameters

| Name   | Type     | Description                       |
| ------ | -------- | --------------------------------- |
| apiKey | `String` | API key is used to access the API |

#### Examples

Transfer 1.1 tokens on Fuse network

```
POST /api/v2/admin/tokens/transfer
body: { tokenAddress: '0xbAa75ecD3Ea911c78A23D7cD16961Eadc5867d2b', networkType: 'fuse', amount: '1.1', from: '0x755c33BE69dD2baB7286E7a2010fc8591AF15a1e', to: '0x5d651E34B6694A8778839441dA954Ece0EA733D8' }
```

#### Success 200

| Name    | Type     | Description |
| ------- | -------- | ----------- |
| Started | `String` | job data    |
