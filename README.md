# MoneyNotes Plugin

A Minecraft server plugin that allows players to withdraw money into physical notes and pay other players, with a configurable 10% tax to prevent economy inflation.

## Features

- **Physical Money Notes**: Withdraw money from your balance into tradeable paper items
- **Taxed Payments**: Send money to other players with automatic tax deduction
- **Anti-Inflation**: 10% tax on all transactions is removed from the economy entirely
- **Stackable Notes**: Notes of the same value stack in inventory
- **Easy Redemption**: Right-click notes to instantly add money to your balance (no tax on redemption)
- **Fully Configurable**: Adjust tax rates, messages, and note appearance

## Requirements

- **Server Software**: Paper 1.21+ (or Spigot/Bukkit 1.21+)
- **Java**: 21 or higher
- **Dependencies**: 
  - Vault (required)
  - Any economy plugin that works with Vault (EssentialsX, CMI, etc.)

## Installation

1. Make sure you have **Vault** and an **economy plugin** (like EssentialsX) installed
2. Download `MoneyNotes.jar`
3. Place it in your server's `/plugins` folder
4. Restart your server
5. Configure the plugin by editing `/plugins/MoneyNotes/config.yml`
6. Reload with `/reload` or restart the server

## Commands

| Command | Aliases | Description | Permission |
|---------|---------|-------------|------------|
| `/withdraw <amount>` | `/wd` | Withdraw money into a physical note (10% tax) | `moneynotes.withdraw` |
| `/paymoney <player> <amount>` | `/pm` | Pay another player money (10% tax) | `moneynotes.pay` |

## How It Works

### Withdrawing Money
```
/withdraw 100
```
- Player needs **$110** in their balance
- Player loses **$110** total
- Player receives a physical **$100 note** (glowing paper item)
- **$10 tax** is deleted from the economy

### Paying Another Player
```
/paymoney Steve 100
```
- Sender needs **$110** in their balance
- Sender loses **$110** total
- Recipient receives **$100**
- **$10 tax** is deleted from the economy

### Redeeming Notes
- **Right-click** any money note in your hand
- Receive the **full amount** shown on the note (no tax)
- Note is removed from your inventory

## Configuration

Edit `/plugins/MoneyNotes/config.yml`:

```yaml
# Tax rate (percentage)
tax-rate: 10.0

# Minimum amounts
minimum-withdraw: 1.0
minimum-pay: 1.0

# Customize all messages with color codes
messages:
  prefix: "&8[&6MoneyNotes&8]&r "
  # ... (see config.yml for all options)

# Note appearance
note-item:
  material: PAPER
  name: "&6&lMoney Note"
  enchanted: true  # Glowing effect
```

## Permissions

| Permission | Description | Default |
|------------|-------------|---------|
| `moneynotes.withdraw` | Use /withdraw command | `true` |
| `moneynotes.pay` | Use /paymoney command | `true` |
| `moneynotes.admin` | Admin permissions | `op` |

## Examples

**Withdraw $500:**
```
/withdraw 500
```
Output: "You withdrew $500.00 and paid $50.00 in tax. Note created!"
(You need $550 in balance)

**Pay another player $1000:**
```
/paymoney Alex 1000
```
Output: "You paid Alex $1000.00 and paid $100.00 in tax."
(You need $1100 in balance, Alex receives $1000)

**Redeem a note:**
- Hold the money note
- Right-click
- Receive the full amount instantly

## Economy Impact

The 10% tax acts as a **money sink** to combat inflation:
- Every transaction removes money from circulation
- Encourages careful spending
- Balances new money generation from gameplay
- Keeps your economy healthy long-term

## Building from Source

If you want to compile the plugin yourself:

1. Make sure you have Maven installed
2. Clone or download the source code
3. Navigate to the plugin directory
4. Run: `mvn clean package`
5. The compiled JAR will be in the `target/` folder

## Support

If you encounter any issues:
1. Check that Vault and your economy plugin are properly installed
2. Verify you're running Paper/Spigot 1.21+
3. Check the console for error messages
4. Make sure players have the correct permissions

## License

This plugin is provided as-is for use on Minecraft servers.

---

**Created for Tycoon servers and economy-focused gameplay!**
