# MultiRewardProgram

Create a new MultiRewardProgram which represents a multi reward contract on the fuse network. The instance provides basic functionality for interacting with the contract.

e.g with web3.js

```typescript
import Web3 from 'web3'
import { MultiRewardProgram } from '@fuseio/earn-sdk'

const stakingAddress = '0x'
const web3Provider = new Web3('https://rpc.fuse.io')
const rewardProgram = new MultiRewardProgram(stakingAddress, web3Provider)
```

### Hierarchy

*   `RewardProgram`

    ↳ **`MultiRewardProgram`**

### Table of contents

#### Constructors

* [constructor](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/MultiRewardProgram.md#constructor)

#### Properties

* [stakingAddress](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/MultiRewardProgram.md#stakingaddress)
* [web3](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/MultiRewardProgram.md#web3)

#### Methods

* [deposit](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/MultiRewardProgram.md#deposit)
* [getRewardRate](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/MultiRewardProgram.md#getrewardrate)
* [getRewardsInfo](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/MultiRewardProgram.md#getrewardsinfo)
* [getStakerInfo](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/MultiRewardProgram.md#getstakerinfo)
* [getStakingTimes](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/MultiRewardProgram.md#getstakingtimes)
* [getStats](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/MultiRewardProgram.md#getstats)
* [withdraw](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/MultiRewardProgram.md#withdraw)
* [withdrawReward](https://app.gitbook.com/s/-Ldmf-muel7HZszBB8qU/technical-docs/earn-sdk/MultiRewardProgram.md#withdrawreward)

### Constructors

#### constructor

• **new MultiRewardProgram**(`stakingAddress`, `provider`)

**Parameters**

| Name             | Type     |
| ---------------- | -------- |
| `stakingAddress` | `string` |
| `provider`       | `any`    |

**Overrides**

RewardProgram.constructor

**Defined in**

[rewards/MultiRewardProgram.ts:26](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/MultiRewardProgram.ts#L26)

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

[rewards/MultiRewardProgram.ts:42](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/MultiRewardProgram.ts#L42)

#### getRewardRate

▸ `Private` **getRewardRate**(`reward`): `Promise`<`any`>

**Parameters**

| Name     | Type     |
| -------- | -------- |
| `reward` | `string` |

**Returns**

`Promise`<`any`>

**Defined in**

[rewards/MultiRewardProgram.ts:217](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/MultiRewardProgram.ts#L217)

#### getRewardsInfo

▸ `Private` **getRewardsInfo**(`account`, `networkId`, `globalTotalStake`, `globalTotalStakeUSD`, `rewards?`): `Promise`<`any`>

**Parameters**

| Name                  | Type     | Default value |
| --------------------- | -------- | ------------- |
| `account`             | `string` | `undefined`   |
| `networkId`           | `number` | `undefined`   |
| `globalTotalStake`    | `string` | `undefined`   |
| `globalTotalStakeUSD` | `number` | `undefined`   |
| `rewards`             | `any`\[] | `[]`          |

**Returns**

`Promise`<`any`>

**Defined in**

[rewards/MultiRewardProgram.ts:230](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/MultiRewardProgram.ts#L230)

#### getStakerInfo

▸ **getStakerInfo**(`account`, `rewardsToken?`): `Promise`<`any`>

Get reward information for the provided address and rewardToken

```typescript
rewardProgram.getStakerInfo(
  '0x',
  '0x00'
)
```

**Parameters**

| Name            | Type     | Description                                 |
| --------------- | -------- | ------------------------------------------- |
| `account`       | `string` | address to fetch the reward information for |
| `rewardsToken?` | `string` | rewardToken to fetch reward information for |

**Returns**

`Promise`<`any`>

**Overrides**

RewardProgram.getStakerInfo

**Defined in**

[rewards/MultiRewardProgram.ts:109](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/MultiRewardProgram.ts#L109)

#### getStakingTimes

▸ **getStakingTimes**(`rewardsToken?`): `Promise`<`any`>

Gets the start, duration and end of staking

**Parameters**

| Name            | Type     | Description                            |
| --------------- | -------- | -------------------------------------- |
| `rewardsToken?` | `string` | the reward to get time information for |

**Returns**

`Promise`<`any`>

**Overrides**

RewardProgram.getStakingTimes

**Defined in**

[rewards/MultiRewardProgram.ts:198](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/MultiRewardProgram.ts#L198)

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

| Name          | Type     | Default value | Description                              |
| ------------- | -------- | ------------- | ---------------------------------------- |
| `account`     | `string` | `undefined`   | the account to get stats for             |
| `pairAddress` | `string` | `undefined`   | the address of the staking token         |
| `networkId`   | `number` | `undefined`   | the networkId where contract is deployed |
| `rewards`     | `any`\[] | `[]`          | array of rewards offerred                |

**Returns**

`Promise`<`any`>

**Overrides**

RewardProgram.getStats

**Defined in**

[rewards/MultiRewardProgram.ts:149](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/MultiRewardProgram.ts#L149)

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

[rewards/MultiRewardProgram.ts:65](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/MultiRewardProgram.ts#L65)

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

[rewards/MultiRewardProgram.ts:86](https://github.com/fuseio/earn-sdk/blob/fe50e4d/src/rewards/MultiRewardProgram.ts#L86)
