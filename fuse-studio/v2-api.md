# Fuse Studio

## Studio Backend API v2.0.0

The Fuse Studio V2 REST API for accessing the data and the services of the Fuse network in a simple way. You can use this API to query and interact with the objects of the Fuse network such as: Communities, Tokens, Bridges and Entities. The backend base URL is [https://studio.fuse.io](https://studio.fuse.io/). Learn more on [https://github.com/fuseio/fuse-studio](https://github.com/fuseio/fuse-studio)

>

##  Accounts

###  Fetch backend accounts

[Back to top]()

Fetch backend accounts

```text
GET api/v2/accounts/
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| accounts | `Object[]` | list |

###  Create backend account

[Back to top]()

Create backend account

```text
POST api/v2/accounts/
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| role | `String` | Account role |
| bridgeType | `String` | Account bridgeType |
| description | `String` | Account description |
| appName | `String` | wallet application if the account uses a wallet app |

#### Param Examples

`json` - Request-Example:

```text
{
   "role": "wallet",
   "bridgeType": "home"
   "description": "Wallet account"
 }
```

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| created | `Object` | account and the jwt if needed |

##  Admin

###  Burn tokens

[Back to top]()

Start async job of burning tokens

```text
POST /api/v2/admin/tokens/burn
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| tokenAddress | `String` | Token address to burn \(body parameter\) |
| networkType | `String` | Token's network \(must be Fuse\) |
| amount | `String` | Token amount to burn |
| from | `String` | account to burn from \(optional\) |

#### Examples

Burn 1.1 tokens on Fuse network

```text
POST /api/v2/admin/tokens/burn
body: { tokenAddress: '0xbAa75ecD3Ea911c78A23D7cD16961Eadc5867d2b', networkType: 'fuse', amount: '1.1' }
```

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| Started | `String` | job data |

###  Get burn events

[Back to top]()

Get burn events created by admin

```text
POST /api/v2/admin/tokens/burnEvents
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| fromWallet | `String` |  |
| startTime | `String` |  |
| endTime | `String` |  |
| networkType | `String` | Token's network \(must be Fuse\) |

#### Examples

GET /api/v2/admin/tokens/burnEvents

```text
GET /api/v2/admin/tokens/burnEvents
body: { fromWallet: '0x755c33BE69dD2baB7286E7a2010fc8591AF15a1e', networkType: 'fuse' }
```

###  Create token

[Back to top]()

Start async job of creating a token

```text
POST /api/v2/admin/tokens/create
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| name | `String` | Token name |
| symbol | `String` | Token symbol |
| initialSupply | `String` | Token initial supply \(in ETH\) |
| uri | `String` | Token URI \(metadata\) |
| expiryTimestamp | `String` | Token expiry timestamp after which cannot transfer \(Unix epoch time - in seconds\) |
| spendabilityIds | `String` | Token spendability ids \(comma-seperated list\) |
| networkType | `String` | Token's network \(must be Fuse\) |

#### Examples

Create a token on Fuse network

```text
POST /api/v2/admin/tokens/create
body: { name: 'MyCoolToken', symbol: 'MCT', initialSupply: '100', uri: 'ipfs://hash', expiryTimestamp: 1585036857, spendabilityIds: 'a,b,c', networkType: 'fuse' }
```

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| Started | `String` | job data |

###  Create foreign wallet for the matching home

[Back to top]()

Start async job of creating a wallet on the foreign network

```text
POST /api/v2/admin/wallets/create/foreign
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| wallerAddress | `String` | address create a wallet for, should be an existing wallet on home network \(body parameter\) |

#### Examples

Create wallet for the provided wallet address

```text
POST /api/v2/admin/wallets/create/foreign
body: { wallerAddress: '0x92c358fcF6d270F97458C57583FCeabC086c3a26' }
```

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| Started | `String` | job data |

###  Create wallet for phone number

[Back to top]()

Start async job of creating a wallet for phone number \(owned by the community admin\)

```text
POST /api/v2/admin/wallets/create
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| phoneNumber | `String` | phone number to create a wallet for \(body parameter\) |

#### Examples

Create wallet for the provided phone number

```text
POST /api/v2/admin/wallets/create
body: { phoneNumber: '+972546123321' }
```

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| Started | `String` | job data |

###  Get expired by wallet/token/spendabilityId

[Back to top]()

Get expired balance for one/multiple wallets by token or spendabilityId

```text
POST /api/v2/admin/tokens/expired
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| walletAddress | `String` |  |
| tokenAddress | `String` |  |
| spendabilityId | `String` |  |
| networkType | `String` | Token's network \(must be Fuse\) |

#### Examples

GET /api/v2/admin/tokens/expired

```text
GET /api/v2/admin/tokens/expired
body: { walletAddress: '0x755c33BE69dD2baB7286E7a2010fc8591AF15a1e', tokenAddress: '0xbAa75ecD3Ea911c78A23D7cD16961Eadc5867d2b', networkType: 'fuse' }
```

###  Mint tokens

[Back to top]()

Start async job of minting tokens

```text
POST /api/v2/admin/tokens/mint
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| tokenAddress | `String` | Token address to mint \(body parameter\) |
| networkType | `String` | Token's network \(must be Fuse\) |
| amount | `String` | Token amount to mint |
| toAddress | `String` | account to transfer to |

#### Examples

Minting 1.1 tokens on Fuse network

```text
POST /api/v2/admin/tokens/mint
body: { tokenAddress: '0xbAa75ecD3Ea911c78A23D7cD16961Eadc5867d2b', networkType: 'fuse', amount: '1.1' }
```

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| Started | `String` | job data |

###  Transfer tokens from account

[Back to top]()

Start async job of transferring tokens from account \(owned by community admin\)

```text
POST /api/v2/admin/tokens/transfer
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| tokenAddress | `String` | Token address to transfer \(body parameter\) |
| spendabilityIds | `String` | Token spendability ids \(comma-seperated list\) - if sent, no need for tokenAddress |
| spendabilityOrder | `String` | Token spendability order \(asc/desc\) - mandatory if using spendabilityIds |
| networkType | `String` | Token's network \(must be Fuse\) |
| amount | `String` | Token amount to transfer |
| from | `String` | account to transfer from |
| to | `String` | address to transfer to |

#### Examples

Transfer 1.1 tokens on Fuse network

```text
POST /api/v2/admin/tokens/transfer
body: { tokenAddress: '0xbAa75ecD3Ea911c78A23D7cD16961Eadc5867d2b', networkType: 'fuse', amount: '1.1', from: '0x755c33BE69dD2baB7286E7a2010fc8591AF15a1e', to: '0x5d651E34B6694A8778839441dA954Ece0EA733D8' }
```

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| Started | `String` | job data |

##  Contacts

###  Acknowledge contacts list sync with nonce

[Back to top]()

Acknowledge contacts list sync with nonce

```text
POST /api/v2/contacts/:nonce
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| response | `String` | Response status - ok |

###  Sync contacts list

[Back to top]()

Sync contacts list

```text
POST api/v2/contacts/
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| contacts | `String[]` | phone numbers list |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| new | `Object[]` | contacts list \(phoneNumber, account\) |
| nonce | `Number` |  |

##  Jobs

###  Fetch job by correlationId

[Back to top]()

Fetches agenda job by job's correlationId

```text
GET api/v2/jobs/correlationId/:correlationId
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| data | `Object` | Job object |

###  Fetch job by id

[Back to top]()

Fetch job by id

```text
GET api/v2/jobs/:jobId
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| data | `Object` | Job object |

##  Login

###  Login using firebase ID token

[Back to top]()

Login using firebase ID token

```text
POST api/v2/login/
```

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| accountAddress | `String` | User account address |
| token | `String` | Firebase ID token |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| token | `String` | JWT token |

###  Request a verification code

[Back to top]()

Request a verification code to user's phone number

```text
POST api/v2/login/request
```

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| phoneNumber | `String` | User phone number |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| response | `String` | Response status - ok |

###  Verify user phone number

[Back to top]()

Verify user phone number by SMS verification code

```text
POST api/v2/login/verify
```

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| phoneNumber | `String` | User phone number |
| accountAddress | `String` | User account address |
| code | `String` | SMS code recieved to user phone number |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| token | `String` | JWT token |

##  Wallet

###  Create wallet contract for user

[Back to top]()

Creates wallet contract for the user

```text
POST api/v2/wallets/
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| Started | `Object` | job data |

###  Create wallet contract for user on Ethereum

[Back to top]()

Creates wallet contract for the user on Ethereum

```text
POST api/v2/wallets/foreign
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| Started | `Object` | job data |

###  Fetch all wallets by phone number

[Back to top]()

Fetches all wallets created by phone number

```text
GET api/v2/wallets/all/:phoneNumber
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| data | `Object` | Array of Wallet objects |

###  Get token transfer events by address on fuse

[Back to top]()

Get token transfer events by address on fuse

```text
GET api/v2/wallets/transfers/tokentx/:walletAddress
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| tokenAddress | `String` | Address of the token |
| startblock | `String` | The block number to start fetch from |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| data | `Object` | Array of transfer events |

###  Fetch user wallet

[Back to top]()

Fetches user's wallet address

```text
GET api/v2/wallets/
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| data | `Object` | User wallet object |

###  Fetch latest wallet by phone number

[Back to top]()

Fetches latest wallet created by phone number

```text
GET api/v2/wallets/:phoneNumber
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| data | `Object` | Wallet object |

###  Notify server on client wallet backup

[Back to top]()

Notify the server that the client has backed up his wallet

```text
POST api/v2/wallets/backup
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| communityAddress | `String` | community address |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| Started | `Object` | job data |

###  Create wallet for phone number

[Back to top]()

Creates wallet contract for phone number, owned by the server until claimed by the user

```text
POST api/v2/wallets/invite/:phoneNumber
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| communityAddress | `String` | community address |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| Started | `Object` | job data |

###  Check if wallet exists by wallet address

[Back to top]()

Checks if wallet exists by wallet address

```text
GET api/v2/wallets/exists/:walletAddress
```

#### Headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| data | `Boolean` | True if wallet exists, false otherwide |

##  WalletLogin

###  Request a verification code

[Back to top]()

Request a verification code to user's phone number

```text
POST api/v2/login/wallet/sms/request
```

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| phoneNumber | `String` | User phone number |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| response | `String` | Response status - ok |

###  Login using firebase ID token

[Back to top]()

Login using firebase ID token

```text
POST api/v2/login/wallet/firebase/verify
```

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| accountAddress | `String` | User account address |
| token | `String` | Firebase ID token |
| identifier | `String` | Phone device identifier |
| appName | `String` | firebase app name the user is connecting to. optional |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| token | `String` | JWT token |

###  Verify user phone number

[Back to top]()

Verify user phone number by SMS verification code

```text
POST api/v2/login/wallet/sms/verify
```

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| phoneNumber | `String` | User phone number |
| accountAddress | `String` | User account address |
| code | `String` | SMS code recieved to user phone number |

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| token | `String` | JWT token |

