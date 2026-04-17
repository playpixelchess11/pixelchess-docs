# Wager & Payouts

## Wager Options

| Amount | USD Equivalent | Label |
|--------|---------------|-------|
| 0.005 ETH | ~$10 | Micro |
| 0.01 ETH | ~$20 | Light |
| 0.025 ETH | ~$50 | Standard |
| 0.05 ETH | ~$100 | High Stakes |

Both players must stake the **exact same amount**. When you join a game, the wager is matched automatically from the game creator's stake.

## Payout Structure

| Outcome | Payout |
|---------|--------|
| You win | 1.9× your wager |
| You lose | 0 (wager forfeited) |
| Draw / Stalemate | Full refund after timeout |

### Example

Player A stakes **0.01 ETH**, Player B joins and matches **0.01 ETH**.

- Total pot: 0.02 ETH
- House fee (5%): 0.001 ETH
- Winner receives: **0.019 ETH**

## House Fee

A **5% fee** is deducted from the total pot on payout. This goes to the PixelChess treasury to maintain the platform.

## How Payouts Work

PixelChess uses a **loser-submits** model:

1. Game ends (checkmate or resign)
2. The losing player calls `submitLoss()` on the smart contract
3. The contract automatically transfers the payout to the winner
4. No manual claiming needed on the winner's side

## Timeout & Refunds

| Scenario | Timeout | Refund |
|----------|---------|--------|
| No opponent joins | 30 minutes | Full refund to creator |
| Game started but no result | 2 hours | Full refund to both players |

If a timeout occurs, either player can call `refundTimeout()` on the contract to recover their ETH.
