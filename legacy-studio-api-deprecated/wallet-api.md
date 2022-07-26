# Wallet API

Wallet API is used to create and fetch wallets of the economy users. Wallet is a smart contract proxy wallet that is deployed on the Fuse network. It has an owner which is in charge of wallet, owner is controlling the wallet funds and can perform other various transactions by signing messages and sending them to the relayer.  See [Jobs API](jobs-api.md) to learn about relaying.

Choosing a owner you are deciding on the custody on the funds. Fuse API provides two modes for this:

* User is its own bank - native to crypto approach when the user holds the keys to his funds. As stated above, with the Fuse API the users holds the private key of the _owner of the wallet._
* Custody - Economy creator is the custodian of the funds. The wallet owner is an account generated by the Fuse Studio backend. It can be controlled by the economy creator via the [Admin API](admin-api.md). This is an easy way to start your economy and onboard users without the usual friction of a blockchain wallet.

It is also possible to mix the modes and migrate the users between the modes. For example a user can start with the custody mode and move to the crypto native mode once the economy manager is sure that users keys are stored in a secure way.

Base URL: [https://studio.fuse.io/](https://studio.fuse.io/)

### Create wallet contract for user

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