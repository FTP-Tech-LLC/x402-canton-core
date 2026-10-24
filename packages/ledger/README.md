# @ftptech/x402-canton-ledger

Shared Canton ledger primitives used by `@ftptech/x402-canton-client`,
`@ftptech/canton-agent-wallet` and the FTP facilitator.

## Install

```bash
npm i @ftptech/x402-canton-ledger
```

## Compatibility

Canton 3.6 participants need 0.6.2 or later. 0.6.1 sends the ACS filter
inside `eventFormat`, and 0.6.2 reads transactions through
`/v2/updates/update-by-id`. Canton 3.6 disables the old endpoints and
3.7 removes them.

## What's in here

- **`CantonClient`**: JSON Ledger API v2 wrapper. Encodes the
  documented gotchas (template id `#package:Module:Entity`, wrapped
  vs flat body shapes per endpoint, `disclosedContracts`, Daml
  `Int` as JSON string). Includes `submitAndWaitForTransaction`,
  `submitAndWait`, `queryActiveContracts`, `getLedgerEnd`,
  `getTransactionById`, `findCommandCompletions`, and the
  `interactiveSubmissionPrepare` + `interactiveSubmissionExecute`
  pair used for external-party signing.
- **Bounded ACS reads**: `queryActiveContractsSlice` and
  `queryActiveContractsBounded` for parties with more contracts than
  the participant lists in one response (`ACS_DEFAULT_LIST_LIMIT`).
- **`CantonExternalPartySigner`** + `ed25519KeyFromNodeKeyPair`
  + `signPreparedTransactionHash`: Ed25519 signing primitives over
  `/v2/interactive-submission/prepare` + `/execute`. Lets an agent
  hold its own key and authorize commands without surrendering it
  to a participant.
- **`ScanClient`**: Scan API reader for AmuletRules,
  open-and-issuing mining rounds, completed transfers via
  `getUpdateById`, transfer-kind resolution (`resolveTransferKind`),
  and traffic-status. Validator-proxy + SV-direct flavors.
- CIP-56 token helpers and prepared-transaction hash recompute.

## How the payment flow uses it

The facilitator relay prepares a `TransferFactory_Transfer` for the
payer. The payer checks it with verify-before-sign from
`@ftptech/x402-canton-core` and signs only its hash. The facilitator
then executes it and pays the traffic. This package is the
lower-level plumbing under those steps and is reusable by anyone.

## Project

Code and issues:
[FTP-Tech-LLC/x402-canton-core](https://github.com/FTP-Tech-LLC/x402-canton-core).
Docs: [x402-docs.ftptech.xyz](https://x402-docs.ftptech.xyz).
