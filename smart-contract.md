# Smart Contract

## Overview

PixelChess uses a single smart contract deployed on **Base Mainnet** to handle all wager logic. No funds are ever held by the team — everything is managed on-chain.

**Contract Address:** `0xCa16bb6c3cedA37C2f99eAfD661066621330E8d1`\
**Network:** Base Mainnet (Chain ID: 8453)\
**Explorer:** [View on Basescan](https://basescan.org/address/0xCa16bb6c3cedA37C2f99eAfD661066621330E8d1#code)

## Key Functions

### `createGame()`
Called by the game creator to open a game slot and lock their wager.

```
Input:  ETH value (0.005–0.05 ETH)
Output: bytes32 gameId
```

### `joinGame(bytes32 gameId)`
Called by the opponent to join an open game and match the wager.

```
Input:  gameId, ETH value (must match creator's wager exactly)
```

### `submitLoss(bytes32 gameId)`
Called by the losing player after the game ends. Automatically pays the winner.

```
Input:  gameId
Effect: transfers payout (1.9×) to the winner
```

### `refundTimeout(bytes32 gameId)`
Called by either player to recover ETH if a game times out.

```
- No opponent joins within 30 min → creator refunded
- Game started but no result within 2 hrs → both refunded
```

## Game States

```
OPEN     → Created, waiting for opponent (30 min window)
ACTIVE   → Both players joined, game in progress (2 hr window)
ENDED    → submitLoss called, winner paid out
REFUNDED → refundTimeout called, ETH returned
```

## Security

- **No admin control over player funds** — owner cannot touch active game funds
- **No self-join** — you cannot join your own game
- **Exact wager matching** — contract rejects mismatched amounts
- **Timeout protection** — funds always recoverable after expiry

## Parameters

| Parameter | Value |
|-----------|-------|
| Minimum bet | 0.005 ETH |
| Maximum bet | 0.05 ETH |
| House fee | 5% |
| Win multiplier | 1.9× |
| Join timeout | 30 minutes |
| Game timeout | 2 hours |
