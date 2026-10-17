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
