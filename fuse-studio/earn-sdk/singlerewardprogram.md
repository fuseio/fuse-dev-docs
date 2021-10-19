# SingleRewardProgram

Create a new SingleRewardProgram which represents a single reward contract on the fuse network. The instance provides basic functionality for interacting with the contract.

e.g with web3.js

```typescript
import Web3 from 'web3'
import { SingleRewardProgram } from '@fuseio/earn-sdk'

const stakingAddress = '0x'
const web3Provider = new Web3('https://rpc.fuse.io')
const rewardProgram = new SingleRewardProgram(stakingAddress, web3Provider)
```

### Hierarchy

*   `RewardProgram`

    ↳ **`SingleRewardProgram`**

### Table of contents

#### Constructors

* [constructor](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/SingleRewardProgram.md#constructor)

#### Properties

* [stakingAddress](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/SingleRewardProgram.md#stakingaddress)
* [web3](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/SingleRewardProgram.md#web3)

#### Methods

* [deposit](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/SingleRewardProgram.md#deposit)
* [getStakerInfo](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/SingleRewardProgram.md#getstakerinfo)
* [getStakingTimes](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/SingleRewardProgram.md#getstakingtimes)
* [getStats](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/SingleRewardProgram.md#getstats)
* [getStatsData](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/SingleRewardProgram.md#getstatsdata)
* [withdraw](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/SingleRewardProgram.md#withdraw)
* [withdrawReward](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/SingleRewardProgram.md#withdrawreward)

### Constructors

#### constructor

• **new SingleRewardProgram**(`stakingAddress`, `provider`)

**Parameters**

| Name             | Type     |
| ---------------- | -------- |
| `stakingAddress` | `string` |
| `provider`       | `any`    |

**Overrides**

RewardProgram.constructor

**Defined in**

[rewards/SingleRewardProgram.ts:36](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/SingleRewardProgram.ts#L36)

### Properties

#### stakingAddress

• `Readonly` **stakingAddress**: `string`

**Inherited from**

RewardProgram.stakingAddress

#### web3

• `Protected` `Readonly` **web3**: `default`

**Inherited from**

RewardProgram.web3

**Defined in**

[rewards/RewardProgam.ts:4](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/RewardProgam.ts#L4)

### Methods

#### deposit

▸ **deposit**(`amount`, `account`): `Promise`<`any`>

Deposit the provided amount of the staking token into the staking contract

```typescript
rewardProgram.deposit(
  '1000000000000000000',
  '0x'
)
```

**Parameters**

| Name      | Type     | Description                             |
| --------- | -------- | --------------------------------------- |
| `amount`  | `string` | the number of staking tokens to deposit |
| `account` | `string` | the account sending the transaction     |

**Returns**

`Promise`<`any`>

**Overrides**

RewardProgram.deposit

**Defined in**

[rewards/SingleRewardProgram.ts:52](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/SingleRewardProgram.ts#L52)

#### getStakerInfo

▸ **getStakerInfo**(`account`): `Promise`<`any`>

Get reward information for the provided address and rewardToken

```typescript
rewardProgram.getStakerInfo(
  '0x',
  '0x00'
)
```

**Parameters**

| Name      | Type     | Description                                 |
| --------- | -------- | ------------------------------------------- |
| `account` | `string` | address to fetch the reward information for |

**Returns**

`Promise`<`any`>

**Overrides**

RewardProgram.getStakerInfo

**Defined in**

[rewards/SingleRewardProgram.ts:118](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/SingleRewardProgram.ts#L118)

#### getStakingTimes

▸ **getStakingTimes**(): `Promise`<`StakingTimes`>

Gets the start, duration and end of staking

**Returns**

`Promise`<`StakingTimes`>

**Overrides**

RewardProgram.getStakingTimes

**Defined in**

[rewards/SingleRewardProgram.ts:143](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/SingleRewardProgram.ts#L143)

#### getStats

▸ **getStats**(`account`, `pairAddress`, `networkId`, `rewards?`): `Promise`<`any`>

Gets global reward stats for rewardProgram

```typescript
rewardProgram.getStats(
  '0x',
  '0x',
  122,
  ['0x']
)
```

**Parameters**

| Name          | Type        | Description                              |
| ------------- | ----------- | ---------------------------------------- |
| `account`     | `string`    | the account to get stats for             |
| `pairAddress` | `string`    | the address of the staking token         |
| `networkId`   | `number`    | the networkId where contract is deployed |
| `rewards?`    | `string`\[] | array of rewards offerred                |

**Returns**

`Promise`<`any`>

**Overrides**

RewardProgram.getStats

**Defined in**

[rewards/SingleRewardProgram.ts:180](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/SingleRewardProgram.ts#L180)

#### getStatsData

▸ `Private` **getStatsData**(`account`): `Promise`<`any`>

**Parameters**

| Name      | Type     |
| --------- | -------- |
| `account` | `string` |

**Returns**

`Promise`<`any`>

**Defined in**

[rewards/SingleRewardProgram.ts:129](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/SingleRewardProgram.ts#L129)

#### withdraw

▸ **withdraw**(`amount`, `account`): `Promise`<`any`>

Withdraw the provided amount of the staking token from the staking contract

```typescript
rewardProgram.withdraw(
  '1000000000000000000',
  '0x'
)
```

**Parameters**

| Name      | Type     | Description                              |
| --------- | -------- | ---------------------------------------- |
| `amount`  | `string` | the number of staking tokens to withdraw |
| `account` | `string` | the account sending the transaction      |

**Returns**

`Promise`<`any`>

**Overrides**

RewardProgram.withdraw

**Defined in**

[rewards/SingleRewardProgram.ts:75](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/SingleRewardProgram.ts#L75)

#### withdrawReward

▸ **withdrawReward**(`account`): `Promise`<`any`>

Withdraw the rewards accured

```typescript
rewardProgram.withdrawReward(
  '0x'
)
```

**Parameters**

| Name      | Type     | Description                         |
| --------- | -------- | ----------------------------------- |
| `account` | `string` | the account sending the transaction |

**Returns**

`Promise`<`any`>

**Overrides**

RewardProgram.withdrawReward

**Defined in**

[rewards/SingleRewardProgram.ts:96](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/SingleRewardProgram.ts#L96)
