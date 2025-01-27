---
head:
  - - meta
    - property: og:title
      content: call
  - - meta
    - name: description
      content: An Action for executing a new message call.
  - - meta
    - property: og:description
      content: An Action for executing a new message call.

---

# call

Executes a new message call immediately without submitting a transaction to the network.

## Usage

```ts
import { getAccount } from 'viem' 
import { publicClient } from '.'

const account = getAccount('0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266')
 
const data = await publicClient.call({ // [!code focus:7]
  account,
  data: '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
  to: '0x70997970c51812dc3a010c7d01b50e0d17dc79c8',
})
```

## Returns

`0x${string}`

The call data.

## Parameters

### account

- **Type:** `Account`

The Account sender. [Read more](/docs/clients/wallet).

```ts
import { getAccount } from 'viem' 

const data = await publicClient.call({
  account: getAccount('0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266'), // [!code focus)]
  data: '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
  to: '0x70997970c51812dc3a010c7d01b50e0d17dc79c8',
})
```

### data

- **Type:** `0x${string}`

A contract hashed method call with encoded args.

```ts
const data = await publicClient.call({
  account,
  data: '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2', // [!code focus]
  to: '0x70997970c51812dc3a010c7d01b50e0d17dc79c8',
})
```

### to

- **Type:** [`Address`](/docs/glossary/types#address)

The contract address or recipient.

```ts
const data = await publicClient.call({
  account,
  data: '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
  to: '0x70997970c51812dc3a010c7d01b50e0d17dc79c8', // [!code focus]
})
```

### accessList (optional)

- **Type:** [`AccessList`](/docs/glossary/types#accesslist)

The access list.

```ts
const data = await publicClient.call({
  account,
  accessList: [ // [!code focus:6]
    {
      address: '0x1',
      import { getAccount } from 'viem' 
      storageKeys: ['0x1'],
    },
  ],
  data: '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
  to: '0x70997970c51812dc3a010c7d01b50e0d17dc79c8',
})
```

### gas (optional)

- **Type:** `bigint`

The gas provided for transaction execution.

```ts
const data = await publicClient.call({
  account,
  data: '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
  gas: 1_000_000n, // [!code focus]
  to: '0x70997970c51812dc3a010c7d01b50e0d17dc79c8',
})
```

### gasPrice (optional)

- **Type:** `bigint`

The price (in wei) to pay per gas. Only applies to [Legacy Transactions](/docs/glossary/terms#legacy-transaction).

```ts
const data = await publicClient.call({
  account,
  data: '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
  gasPrice: parseGwei('20'), // [!code focus]
  to: '0x70997970c51812dc3a010c7d01b50e0d17dc79c8',
})
```

### maxFeePerGas (optional)

- **Type:** `bigint`

Total fee per gas (in wei), inclusive of `maxPriorityFeePerGas`. Only applies to [EIP-1559 Transactions](/docs/glossary/terms#eip-1559-transaction).

```ts
const data = await publicClient.call({
  account,
  data: '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
  maxFeePerGas: parseGwei('20'), // [!code focus]
  to: '0x70997970c51812dc3a010c7d01b50e0d17dc79c8',
})
```

### maxPriorityFeePerGas (optional)

- **Type:** `bigint`

Max priority fee per gas (in wei). Only applies to [EIP-1559 Transactions](/docs/glossary/terms#eip-1559-transaction).

```ts
const data = await publicClient.call({
  account,
  data: '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
  maxFeePerGas: parseGwei('20'),
  maxPriorityFeePerGas: parseGwei('2'), // [!code focus]
  to: '0x70997970c51812dc3a010c7d01b50e0d17dc79c8',
})
```

### nonce (optional)

- **Type:** `bigint`

Unique number identifying this transaction.

```ts
const data = await publicClient.call({
  account,
  data: '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
  nonce: 420n, // [!code focus]
  to: '0x70997970c51812dc3a010c7d01b50e0d17dc79c8',
})
```

### value (optional)

- **Type:** `bigint`

Value (in wei) sent with this transaction.

```ts
const data = await publicClient.call({
  account,
  data: '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
  to: '0x70997970c51812dc3a010c7d01b50e0d17dc79c8',
  value: parseEther('1'), // [!code focus]
})
```

### blockNumber (optional)

- **Type:** `number`

The block number to perform the call against.

```ts
const data = await publicClient.call({
  blockNumber: 15121123n, // [!code focus]
  account,
  data: '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
  to: '0x70997970c51812dc3a010c7d01b50e0d17dc79c8',
})
```

### blockTag (optional)

- **Type:** `'latest' | 'earliest' | 'pending' | 'safe' | 'finalized'`
- **Default:** `'latest'`

The block tag to perform the call against.

```ts
const data = await publicClient.call({
  blockTag: 'safe', // [!code focus]
  account,
  data: '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
  to: '0x70997970c51812dc3a010c7d01b50e0d17dc79c8',
})
```

## JSON-RPC Methods

[`eth_call`](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth_call)