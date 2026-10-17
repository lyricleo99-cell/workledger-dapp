# WorkLedger

SC6113-DEVELOPMENT OF DECENTRALIZED APPLICATIONS

Liu Yanrong — Single-member group project

Enterprise escrow DApp with three interacting Solidity contracts, four business roles and fourteen transaction types. Flask serves the REST API; SQL stores sessions, notes and events; MetaMask signs transactions.

## Source and deliverables

Download and extract `workledger-source.zip`. Start with `WorkLedger/00_FILE_INDEX.md` and `WorkLedger/README.md`. The archive includes Solidity, raw ABI, compiled artifacts, Flask, HTML/CSS/JavaScript, tests, screenshots, a 13-page report, 12-slide presentation, diagrams, user manual and local Git history.

## Verification

45 Python tests and 14 browser checks passed locally. Local tests use Ganache and an injected test-wallet adapter. Public Sepolia deployment is recorded separately; local tests are not public-network evidence.

## Render

Build command:
```sh
python -m zipfile -e workledger-source.zip . && pip install -r WorkLedger/requirements.txt
```
Start command:
```sh
gunicorn --chdir WorkLedger app:app --bind 0.0.0.0:$PORT --workers 1 --threads 4 --timeout 120
```
Use PostgreSQL through DATABASE_URL, a random SECRET_KEY and the exact PUBLIC_ORIGIN. Configure the three contract addresses and Sepolia RPC_URL after deployment. ENABLE_DEPLOY_UI enables the four-transaction MetaMask deployment helper and is disabled for normal operation. No wallet private key is held by the server.
## Verified public deployment
Application: https://workledger-dapp.onrender.com
Ethereum Sepolia, chain 11155111, deployment start block 11934470.
- RoleRegistry: `0x75A9161ee99560194f6E3B7b50C6D7be13D97100`
- PaymentEscrow: `0xF8319e30eBaE7917f46903d81E3fD156394B839A`
- DisputeBoard: `0x3a9469b1D8DccF8fEffD9ac281504E5000728fD4`
All three deployment receipts succeeded and the escrow board binding matches. Hosted chain readiness, database health, agreement reads and temporary EOA signature authentication were checked successfully on 17 October 2026. Deployment helper endpoints are disabled. Business-flow tests remain local; no public agreement existed at this verification.
