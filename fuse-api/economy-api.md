# Economy API

Base URL: [https://studio.fuse.io/api/v1](https://studio.fuse.io/api/v1)

### Add foreign token address to community <a href="#user-content-add-foreign-token-address-to-community" id="user-content-add-foreign-token-address-to-community"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v1.md#top)

```
PUT /communities/:communityAddress/foreignToken
```

#### Parameter Parameters

| Name                | Type                  | Description       |
| ------------------- | --------------------- | ----------------- |
| communityAddress    | `String`              | Community address |
| foreignTokenAddress | `foreignTokenAddress` |                   |

#### Param Examples

`json` - Request-Example:

```
{
   "foreignTokenAddress": {{foreignTokenAddress}}
}
```

### Add plugins to community <a href="#user-content-add-plugins-to-community" id="user-content-add-plugins-to-community"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v1.md#top)

```
POST /communities/:communityAddress/plugins
```

#### Parameter Parameters

| Name             | Type     | Description                  |
| ---------------- | -------- | ---------------------------- |
| communityAddress | `String` | Community address            |
| plugins          | `Object` | The plugins (with arguments) |

#### Param Examples

`json` - Request-Example:

```
{
   "name": "joinBonus",
   "isActive": false
 }
```

### &#x20;<a href="#undefined" id="undefined"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v1.md#top)

```
GET /communities/count
```

### Fetch community <a href="#user-content-fetch-community" id="user-content-fetch-community"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v1.md#top)

Community is a set of contracts and services. Members of the community are users of the Fuse network. The community is configured via the plugins.

```
GET /communities/:communityAddress
```

#### Parameter Parameters

| Name             | Type     | Description       |
| ---------------- | -------- | ----------------- |
| communityAddress | `String` | Community address |

#### Success 200

| Name                 | Type      | Description                                                                                          |
| -------------------- | --------- | ---------------------------------------------------------------------------------------------------- |
| communityAddress     | `String`  | Address of the community on the Fuse network                                                         |
| homeTokenAddress     | `String`  | Address of the community token on the Fuse network                                                   |
| foreignTokenAddress  | `String`  | Address of the community token on the Ethereum network                                               |
| homeBridgeAddress    | `String`  | Address of the community bridge on the Fuse network                                                  |
| foreignBridgeAddress | `String`  | Address of the community bridge on the Ethereum network                                              |
| isClosed             | `Boolean` | Is the community is closed or open. Closed community requires an approve of community admin to join. |
| plugins              | `Object`  | Defines the community plugins.                                                                       |

### Fetch community with plugins adjusted for the specified account <a href="#user-content-fetch-community-with-plugins-adjusted-for-the-specified-account" id="user-content-fetch-community-with-plugins-adjusted-for-the-specified-account"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v1.md#top)

Community is a set of contracts and services. Members of the community are users of the Fuse network. The community is configured via the plugins.

```
GET /communities/:communityAddress
```

#### Parameter Parameters

| Name             | Type     | Description          |
| ---------------- | -------- | -------------------- |
| communityAddress | `String` | Community address    |
| accountAddress   | `String` | User account address |

#### Success 200

| Name                 | Type      | Description                                                                                          |
| -------------------- | --------- | ---------------------------------------------------------------------------------------------------- |
| communityAddress     | `String`  | Address of the community on the Fuse network                                                         |
| homeTokenAddress     | `String`  | Address of the community token on the Fuse network                                                   |
| foreignTokenAddress  | `String`  | Address of the community token on the Ethereum network                                               |
| homeBridgeAddress    | `String`  | Address of the community bridge on the Fuse network                                                  |
| foreignBridgeAddress | `String`  | Address of the community bridge on the Ethereum network                                              |
| isClosed             | `Boolean` | Is the community is closed or open. Closed community requires an approve of community admin to join. |
| plugins              | `Object`  | Defines the community plugins.                                                                       |

### Invite a user to community <a href="#user-content-invite-a-user-to-community" id="user-content-invite-a-user-to-community"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v1.md#top)

```
POST /communities/:communityAddress/invite
```

#### Parameter Parameters

| Name             | Type     | Description       |
| ---------------- | -------- | ----------------- |
| communityAddress | `String` | Community address |

#### Param Examples

`json` - Request-Example:

```
{
   "phoneNumber": {{userPhoneNumber}},
}
```

`json` - Request-Example:

```
{
   "email": {{userEmail}},
}
```

### Set secondary token for the community <a href="#user-content-set-secondary-token-for-the-community" id="user-content-set-secondary-token-for-the-community"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v1.md#top)

```
PUT /communities/:communityAddress/secondary
```

#### Parameter Parameters

| Name                  | Type     | Description                    |
| --------------------- | -------- | ------------------------------ |
| secondaryTokenAddress | `String` | Address of the secondary token |
| networkType           | `String` | Token's network type           |
| tokenType             | `String` | Token's network type           |

#### Param Examples

`json` - Request-Example:

```
{
   "secondaryTokenAddress": "0xd6aab51d1343dcbee9b47e6fef8ba4469cf3dbde",
   "networkType": "fuse",
   "tokenType": "basic"
 }
```

### Update community metadata <a href="#user-content-update-community-metadata" id="user-content-update-community-metadata"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v1.md#top)

```
PUT /communities/:communityAddress
```

#### Parameter Parameters

| Name             | Type     | Description        |
| ---------------- | -------- | ------------------ |
| communityAddress | `String` | Community address  |
| community        | `Object` | metadata to update |

#### Param Examples

`json` - Request-Example:

```
{
   "communityURI": "ipfs://hash",
 }
```

## &#x20;<a href="#user-content-entity" id="user-content-entity"></a>

\
