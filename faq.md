# FAQ

## General

**What is PixelChess?**\
PixelChess is a pixel-art chess game on Base where you wager real ETH against other players. Both players stake ETH before the game — winner takes 1.9×.

**Do I need an account?**\
No. Just connect your MetaMask wallet. No email, no sign-up.

**What network does PixelChess use?**\
Base Mainnet. Make sure your wallet is connected to Base and you have ETH on Base (not Ethereum mainnet).

**How do I get ETH on Base?**\
Bridge ETH from Ethereum mainnet to Base using [bridge.base.org](https://bridge.base.org), or buy directly on Base via Coinbase.

---

## Gameplay

**Who moves first?**\
The player who created the game plays as White and moves first. The player who joined plays as Black.

**What happens if my opponent disconnects?**\
The game will stall. After 2 hours, you can call `refundTimeout()` on the contract to recover your ETH.

**Can I resign?**\
Yes. Click the **RESIGN** button during the game. This automatically submits your loss on-chain and pays your opponent.

**What happens on a draw or stalemate?**\
Neither player wins. Both can recover their ETH after the 2-hour game timeout via `refundTimeout()`.

---

## Wager & Payments

**When do I pay?**\
You pay when you click Find Match or Join a game. ETH is locked in the smart contract immediately.

**When do I get paid?**\
When the losing player submits their loss on-chain. This happens automatically via the game interface.

**What if the loser refuses to submit?**\
After 2 hours, the winner can call `refundTimeout()` to recover their ETH. The contract always protects your funds.

**Is there a house fee?**\
Yes, 5% is deducted from the total pot. This goes to the PixelChess treasury.

---

## Technical

**Is PixelChess open source?**\
The smart contract is verified on Basescan and fully readable.

**Can PixelChess take my funds?**\
No. The contract owner has no access to funds in active games. Only the players can trigger payouts or refunds.

**What wallet do I need?**\
Any EVM-compatible wallet that supports Base Mainnet. MetaMask is recommended.
