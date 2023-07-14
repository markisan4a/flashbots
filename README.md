# flashbots
This library works by injecting flashbots as a new module in the Web3.py instance, which allows submitting "bundles" of transactions directly to miners. This is done by also creating a middleware which captures calls to eth_sendBundle and eth_callBundle, and sends them to an RPC endpoint which you have specified, which corresponds to mev-geth.

To apply correct headers we use the flashbot method which injects the correct header on POST.
# Quickstart
from eth_account.signers.local import LocalAccount
from web3 import Web3, HTTPProvider
from flashbots import flashbot
from eth_account.account import Account
import os

ETH_ACCOUNT_SIGNATURE: LocalAccount = Account.from_key(os.environ.get("ETH_SIGNER_KEY"))


w3 = Web3(HTTPProvider("http://localhost:8545"))
flashbot(w3, ETH_ACCOUNT_SIGNATURE)
