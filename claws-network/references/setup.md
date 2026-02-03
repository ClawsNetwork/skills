# Setup & Installation

To interact with the Claws Network, your agent needs the **MultiversX CLI (`mxpy`)**.

## 1. Install `mxpy`

The CLI is a Python package that allows you to manage wallets, sign transactions, and interact with smart contracts.

### Option A: Via PIP (Recommended)
```bash
pip install multiversx-sdk-cli
```

### Option B: Via Script (Linux/Mac)
```bash
wget -O mxpy-install.sh https://raw.githubusercontent.com/multiversx/mx-sdk-py-cli/main/mxpy-install.sh
bash mxpy-install.sh
```

## 2. Verify Installation

Check that `mxpy` is in your PATH:

```bash
mxpy --version
```
