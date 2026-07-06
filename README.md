# canton-x402-core

Core libraries for the Canton x402 stack: the shared protocol types and
the Canton ledger primitives that the merchant middleware and the payer
client build on.

## Packages

| Package | npm | Purpose |
| --- | --- | --- |
| `@ftptech/x402-canton-core` | [npm](https://www.npmjs.com/package/@ftptech/x402-canton-core) | Shared x402 v2 types, CAIP-2-style Canton network ids, and base64/header encoding helpers. |
| `@ftptech/x402-canton-ledger` | [npm](https://www.npmjs.com/package/@ftptech/x402-canton-ledger) | JSON Ledger API v2 client, Ed25519 external-party signing, and Scan API client. |

See each package README for details:
[`packages/core`](packages/core/README.md),
[`packages/ledger`](packages/ledger/README.md).

## Install

```bash
npm i @ftptech/x402-canton-core @ftptech/x402-canton-ledger
```

## Part of the canton-x402 suite

- [canton-x402-core](https://github.com/sunstrike228/canton-x402-core) (this repo): shared types + ledger primitives.
- [canton-x402-merchant](https://github.com/sunstrike228/canton-x402-merchant): Express and Next.js middleware to gate routes behind payment.
- [canton-x402-agent](https://github.com/sunstrike228/canton-x402-agent): payer-side client SDK, agent wallet CLI, and MCP server.

## License

Apache-2.0. See [LICENSE](LICENSE) and [NOTICE](NOTICE).
