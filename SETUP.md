# Quick Setup Guide for MoneyNotes Plugin

## Compilation Instructions

Since you'll need to compile this plugin, here are two methods:

### Method 1: Using Maven (Recommended)

1. **Install Maven** (if you don't have it):
   - Download from: https://maven.apache.org/download.cgi
   - Or use package manager: `apt install maven` (Linux) or `brew install maven` (Mac)

2. **Compile the plugin**:
   ```bash
   cd MoneyNotes
   mvn clean package
   ```

3. **Get your plugin**:
   - The compiled JAR will be in `target/MoneyNotes-1.0.0.jar`
   - Copy this file to your server's `/plugins` folder

### Method 2: Using an Online Compiler

If you can't install Maven locally, use an online service:

1. Go to: https://www.compilejava.net/ or similar
2. Upload the project folder
3. Or use GitHub Actions (free) to auto-compile

### Method 3: Pre-compiled JAR

Alternatively, I can provide you with a pre-compiled JAR file if you have a way to compile it on your system or ask someone to compile it for you.

## File Structure

The plugin consists of these key files:

```
MoneyNotes/
├── pom.xml                          (Maven build file)
├── plugin.yml                       (Plugin metadata)
├── config.yml                       (Default configuration)
├── README.md                        (Documentation)
└── src/main/java/com/moneynotes/
    ├── MoneyNotesPlugin.java       (Main plugin class)
    ├── ConfigManager.java          (Config handling)
    ├── NoteManager.java            (Note creation/validation)
    ├── WithdrawCommand.java        (/withdraw command)
    ├── PayCommand.java             (/paymoney command)
    └── NoteListener.java           (Right-click redemption)
```

## First-Time Setup on Your Server

1. **Install dependencies first**:
   - Vault: https://www.spigotmc.org/resources/vault.34315/
   - EssentialsX (or another economy plugin): https://essentialsx.net/downloads.html

2. **Add MoneyNotes**:
   - Put `MoneyNotes.jar` in `/plugins` folder
   - Start/restart your server

3. **Configure** (optional):
   - Edit `/plugins/MoneyNotes/config.yml`
   - Change tax rate, messages, etc.
   - Reload: `/reload confirm`

4. **Test it**:
   ```
   /withdraw 100
   /paymoney <player> 50
   ```

## Quick Test Commands

```bash
# Give yourself money first (using EssentialsX)
/eco give <yourname> 10000

# Test withdrawal
/withdraw 100

# Test payment
/paymoney <friend> 50

# Test redemption
# (Right-click the note you received)
```

## Troubleshooting

**"Vault economy not found!"**
- Install Vault plugin
- Install an economy plugin (EssentialsX recommended)
- Restart server

**Commands not working**
- Check permissions: `moneynotes.withdraw` and `moneynotes.pay`
- Make sure you have money in your balance

**Notes not stacking**
- They should stack automatically if values match
- If not, check for any conflicting plugins

## Changing the Tax Rate

Edit `/plugins/MoneyNotes/config.yml`:

```yaml
tax-rate: 10.0  # Change this to any percentage (5.0 = 5%, 15.0 = 15%, etc.)
```

Then reload: `/reload confirm`

## Need Help?

- Check server console for errors
- Verify Vault and economy plugin are running: `/plugins`
- Make sure you're on Paper/Spigot 1.21+
- Check permissions are granted

---

**Ready to combat inflation and create a healthy economy!**
