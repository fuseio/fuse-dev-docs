---
description: REST API documentation
---

# Fuse Studio

REST API for accessing and managing communities (or economies) on the Fuse Studio platform. Please attach the API key for all your request, you can get an API key by creating an economy on Fuse Studio. Important part of the API is the Admin module, it offers a simple API for minting and transferring tokens between economy members. Please contract the team to get access to the API. The backend base URL is [https://studio.fuse.io](https://studio.fuse.io). Learn more on [https://github.com/fuseio/fuse-studio](https://github.com/fuseio/fuse-studio)

## Accounts <a href="#user-content-accounts" id="user-content-accounts"></a>

### Fetch backend accounts <a href="#user-content-fetch-backend-accounts" id="user-content-fetch-backend-accounts"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Fetch backend accounts

```
GET api/v2/accounts/
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name     | Type       | Description |
| -------- | ---------- | ----------- |
| accounts | `Object[]` | list        |

### Create backend account <a href="#user-content-create-backend-account" id="user-content-create-backend-account"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Create backend account

```
POST api/v2/accounts/
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name        | Type     | Description                                         |
| ----------- | -------- | --------------------------------------------------- |
| role        | `String` | Account role                                        |
| bridgeType  | `String` | Account bridgeType                                  |
| description | `String` | Account description                                 |
| appName     | `String` | wallet application if the account uses a wallet app |

#### Param Examples

`json` - Request-Example:

```
{
   "role": "wallet",
   "bridgeType": "home"
   "description": "Wallet account"
 }
```

#### Success 200

| Name    | Type     | Description                   |
| ------- | -------- | ----------------------------- |
| created | `Object` | account and the jwt if needed |

### Unlock backend account <a href="#user-content-unlock-backend-account" id="user-content-unlock-backend-account"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Unlock backend account by accout address and bridge type

```
POST api/v2/accounts/
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name           | Type     | Description        |
| -------------- | -------- | ------------------ |
| accountAddress | `String` | Account address    |
| bridgeType     | `String` | Account bridgeType |

#### Param Examples

`json` - Request-Example:

```
{
   "accountAddress": "0x123",
   "bridgeType": "home"
 }
```

#### Success 200

| Name     | Type     | Description                                        |
| -------- | -------- | -------------------------------------------------- |
| Unlocked | `Object` | account object if an account was actually unlocked |

## Admin <a href="#user-content-admin" id="user-content-admin"></a>

### Burn tokens <a href="#user-content-burn-tokens" id="user-content-burn-tokens"></a>

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

## Jobs <a href="#user-content-jobs" id="user-content-jobs"></a>

### Fetch job by correlationId <a href="#user-content-fetch-job-by-correlationid" id="user-content-fetch-job-by-correlationid"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Fetches agenda job by job's correlationId

```
GET api/v2/jobs/correlationId/:correlationId
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type     | Description |
| ---- | -------- | ----------- |
| data | `Object` | Job object  |

### Fetch job by id <a href="#user-content-fetch-job-by-id" id="user-content-fetch-job-by-id"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Fetch job by id

```
GET api/v2/jobs/:jobId
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type     | Description |
| ---- | -------- | ----------- |
| data | `Object` | Job object  |

### Retry failed job by id <a href="#user-content-retry-failed-job-by-id" id="user-content-retry-failed-job-by-id"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Retry failed job by id

```
GET api/v2/jobs/retry/:jobId
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type     | Description |
| ---- | -------- | ----------- |
| data | `Object` | Job object  |

### Retry failed job by query <a href="#user-content-retry-failed-job-by-query" id="user-content-retry-failed-job-by-query"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Retry failed job by id

```
GET api/v2/jobs/retry
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type     | Description |
| ---- | -------- | ----------- |
| data | `Object` | Job object  |

## Login <a href="#user-content-login" id="user-content-login"></a>

### Login using firebase ID token <a href="#user-content-login-using-firebase-id-token" id="user-content-login-using-firebase-id-token"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Login using firebase ID token

```
POST api/v2/login/
```

#### Parameter Parameters

| Name           | Type     | Description          |
| -------------- | -------- | -------------------- |
| accountAddress | `String` | User account address |
| token          | `String` | Firebase ID token    |

#### Success 200

| Name  | Type     | Description |
| ----- | -------- | ----------- |
| token | `String` | JWT token   |

### Request a verification code <a href="#user-content-request-a-verification-code" id="user-content-request-a-verification-code"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Request a verification code to user's phone number

```
POST api/v2/login/request
```

#### Parameter Parameters

| Name        | Type     | Description       |
| ----------- | -------- | ----------------- |
| phoneNumber | `String` | User phone number |

#### Success 200

| Name     | Type     | Description          |
| -------- | -------- | -------------------- |
| response | `String` | Response status - ok |

### Verify user phone number <a href="#user-content-verify-user-phone-number" id="user-content-verify-user-phone-number"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Verify user phone number by SMS verification code

```
POST api/v2/login/verify
```

#### Parameter Parameters

| Name           | Type     | Description                            |
| -------------- | -------- | -------------------------------------- |
| phoneNumber    | `String` | User phone number                      |
| accountAddress | `String` | User account address                   |
| code           | `String` | SMS code recieved to user phone number |

#### Success 200

| Name  | Type     | Description |
| ----- | -------- | ----------- |
| token | `String` | JWT token   |

## Wallet <a href="#user-content-wallet" id="user-content-wallet"></a>

### Create wallet contract for user <a href="#user-content-create-wallet-contract-for-user" id="user-content-create-wallet-contract-for-user"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Creates wallet contract for the user

```
POST api/v2/wallets/
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name    | Type     | Description |
| ------- | -------- | ----------- |
| Started | `Object` | job data    |

### Create wallet contract for user on Ethereum <a href="#user-content-create-wallet-contract-for-user-on-ethereum" id="user-content-create-wallet-contract-for-user-on-ethereum"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

\[Deprecated!] Creates wallet contract for the user on Ethereum

```
POST api/v2/wallets/foreign
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name    | Type     | Description |
| ------- | -------- | ----------- |
| Started | `Object` | job data    |

### Fetch all wallets by phone number <a href="#user-content-fetch-all-wallets-by-phone-number" id="user-content-fetch-all-wallets-by-phone-number"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Fetches all wallets created by phone number

```
GET api/v2/wallets/all/:phoneNumber
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type     | Description             |
| ---- | -------- | ----------------------- |
| data | `Object` | Array of Wallet objects |

### Get token transfer events by address on fuse <a href="#user-content-get-token-transfer-events-by-address-on-fuse" id="user-content-get-token-transfer-events-by-address-on-fuse"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Get token transfer events by address on fuse

```
GET api/v2/wallets/transfers/tokentx/:walletAddress
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name         | Type     | Description                          |
| ------------ | -------- | ------------------------------------ |
| tokenAddress | `String` | Address of the token                 |
| startblock   | `String` | The block number to start fetch from |

#### Success 200

| Name | Type     | Description              |
| ---- | -------- | ------------------------ |
| data | `Object` | Array of transfer events |

### Fetch user wallet <a href="#user-content-fetch-user-wallet" id="user-content-fetch-user-wallet"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Fetches user's wallet address

```
GET api/v2/wallets/
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type     | Description        |
| ---- | -------- | ------------------ |
| data | `Object` | User wallet object |

### Fetch latest wallet by phone number <a href="#user-content-fetch-latest-wallet-by-phone-number" id="user-content-fetch-latest-wallet-by-phone-number"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Fetches latest wallet created by phone number

```
GET api/v2/wallets/:phoneNumber
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type     | Description   |
| ---- | -------- | ------------- |
| data | `Object` | Wallet object |

### Notify server on client wallet backup <a href="#user-content-notify-server-on-client-wallet-backup" id="user-content-notify-server-on-client-wallet-backup"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Notify the server that the client has backed up his wallet

```
POST api/v2/wallets/backup
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name             | Type     | Description       |
| ---------------- | -------- | ----------------- |
| communityAddress | `String` | community address |

#### Success 200

| Name    | Type     | Description |
| ------- | -------- | ----------- |
| Started | `Object` | job data    |

### Create wallet for phone number <a href="#user-content-create-wallet-for-phone-number" id="user-content-create-wallet-for-phone-number"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Creates wallet contract for phone number, owned by the server until claimed by the user

```
POST api/v2/wallets/invite/:phoneNumber
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name             | Type     | Description       |
| ---------------- | -------- | ----------------- |
| communityAddress | `String` | community address |

#### Success 200

| Name    | Type     | Description |
| ------- | -------- | ----------- |
| Started | `Object` | job data    |

### Check if wallet exists by wallet address <a href="#user-content-check-if-wallet-exists-by-wallet-address" id="user-content-check-if-wallet-exists-by-wallet-address"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Checks if wallet exists by wallet address

```
GET api/v2/wallets/exists/:walletAddress
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type      | Description                            |
| ---- | --------- | -------------------------------------- |
| data | `Boolean` | True if wallet exists, false otherwide |

## WalletLogin <a href="#user-content-walletlogin" id="user-content-walletlogin"></a>

### Request a verification code <a href="#user-content-request-a-verification-code" id="user-content-request-a-verification-code"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Request a verification code to user's phone number

```
POST api/v2/login/wallet/sms/request
```

#### Parameter Parameters

| Name        | Type     | Description       |
| ----------- | -------- | ----------------- |
| phoneNumber | `String` | User phone number |

#### Success 200

| Name     | Type     | Description          |
| -------- | -------- | -------------------- |
| response | `String` | Response status - ok |

### Login using firebase ID token <a href="#user-content-login-using-firebase-id-token" id="user-content-login-using-firebase-id-token"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Login using firebase ID token

```
POST api/v2/login/wallet/firebase/verify
```

#### Parameter Parameters

| Name           | Type     | Description                                           |
| -------------- | -------- | ----------------------------------------------------- |
| accountAddress | `String` | User account address                                  |
| token          | `String` | Firebase ID token                                     |
| identifier     | `String` | Phone device identifier                               |
| appName        | `String` | firebase app name the user is connecting to. optional |

#### Success 200

| Name  | Type     | Description |
| ----- | -------- | ----------- |
| token | `String` | JWT token   |

### Verify user phone number <a href="#user-content-verify-user-phone-number" id="user-content-verify-user-phone-number"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Verify user phone number by SMS verification code

```
POST api/v2/login/wallet/sms/verify
```

#### Parameter Parameters

| Name           | Type     | Description                            |
| -------------- | -------- | -------------------------------------- |
| phoneNumber    | `String` | User phone number                      |
| accountAddress | `String` | User account address                   |
| code           | `String` | SMS code recieved to user phone number |

#### Success 200

| Name  | Type     | Description |
| ----- | -------- | ----------- |
| token | `String` | JWT token   |
