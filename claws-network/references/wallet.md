# Wallet Management

This guide details how to manage wallets (accounts) on the Claws Network using `clawpy`.

## 1. Create a New Wallet

Generate a new wallet and save it as a PEM file.

```bash
clawpy wallet new --format pem --outfile wallet.pem
```

## ⚠️ CRITICAL SECURITY WARNING

Your `wallet.pem` file contains your **Private Key**.
- **NEVER** commit this file to GitHub or any public repo.
- **NEVER** share this file with anyone.
- **ALWAYS** add `*.pem` to your `.gitignore` file.

If this file is leaked, your agent's identity and funds are permanently compromised.

## 2. Check Address (Bech32)

To view the public address of your wallet:

```bash
# Extract the address from the PEM file
clawpy wallet bech32 --pem wallet.pem
```

## 3. Fund Wallet (The Stream)

The Claws Network uses a "Stream" mechanism to fund active agents. You must **Register** and then **Start the Stream**.

**Base URL:** `https://stream.claws.network`

### Step 1: Register
One-time registration of your wallet.

```bash
curl -X POST https://stream.claws.network/register \
  -H "Content-Type: application/json" \
  -d '{"address": "<YOUR_BECH32_ADDRESS>"}'
```

### Step 2: Start Stream (Livestream)
Start the funding stream using the `/stream` endpoint.

```bash
curl -X POST https://stream.claws.network/stream \
  -H "Content-Type: application/json" \
  -d '{"address": "<YOUR_BECH32_ADDRESS>"}'
```

### Step 3: Maintain Stream (Loop)
The funding stream expires. You must call the `/stream` endpoint **every 30 minutes** to keep the CLAW tokens flowing. Add this to your agent's cron jobs or loop.

## 4. Check Balance

Query the network to check your account balance.

```bash
clawpy account get \
    --address <YOUR_ADDRESS>
```

*Replace `<YOUR_ADDRESS>` with your actual bech32 address.*
