# x402-canton-core

Core libraries for the Canton x402 stack: the shared protocol types and
the Canton ledger primitives that the merchant middleware and the payer
client build on.

## Packages

| Package | Version | Purpose |
| --- | --- | --- |
| [`@ftptech/x402-canton-core`](https://www.npmjs.com/package/@ftptech/x402-canton-core) | 1.4.0 | x402 v2 types, Canton network ids, header encoding, atomic amounts, and the payer's verify-before-sign checks. |
| [`@ftptech/x402-canton-ledger`](https://www.npmjs.com/package/@ftptech/x402-canton-ledger) | 0.6.2 | JSON Ledger API v2 client, Ed25519 external-party signing, and Scan API client. |

See each package README for details:
[`packages/core`](packages/core/README.md),
[`packages/ledger`](packages/ledger/README.md).

## Install

```bash
npm i @ftptech/x402-canton-core @ftptech/x402-canton-ledger
```

## Compatibility

Canton 3.6 participants need `@ftptech/x402-canton-ledger` 0.6.2 or
later. 0.6.1 sends the ACS filter inside `eventFormat`, and 0.6.2 reads
transactions through `update-by-id`. Canton 3.6 disables the old
endpoints and 3.7 removes them.

## Part of the x402 Canton suite

- [x402-canton-core](https://github.com/FTP-Tech-LLC/x402-canton-core) (this repo): shared types and ledger primitives.
- [x402-canton-merchant](https://github.com/FTP-Tech-LLC/x402-canton-merchant): Express and Next.js middleware to gate routes behind payment.
- [x402-canton-agent](https://github.com/FTP-Tech-LLC/x402-canton-agent): payer client SDK, agent wallet CLI, and MCP server.
- [x402-canton-facilitator](https://github.com/FTP-Tech-LLC/x402-canton-facilitator): the facilitator.

Docs: [x402-docs.ftptech.xyz](https://x402-docs.ftptech.xyz).
Scheme spec: [`scheme_exact_canton.md`](https://github.com/x402-foundation/x402/blob/main/specs/schemes/exact/scheme_exact_canton.md).

## License

Apache-2.0. See [LICENSE](LICENSE) and [NOTICE](NOTICE).
