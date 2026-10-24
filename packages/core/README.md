# @ftptech/x402-canton-core

Shared TypeScript types and helpers for the Canton x402 protocol
stack. Used by `@ftptech/x402-canton-client`,
`@ftptech/canton-agent-wallet`, `@ftptech/x402-canton-express`, and
`@ftptech/x402-canton-next`.

## Install

```bash
npm i @ftptech/x402-canton-core
```

## What's in here

- `X402ResourceInfo`, `PaymentRequirements`, `CantonPaymentPayload`,
  `FacilitatorRequest`, `VerifyResponse`, `SettleResponse`,
  `SupportedResponse`, `CantonErrorCode` types per x402 v2.
- `CantonNetwork` identifiers: `canton:mainnet`, `canton:testnet`,
  `canton:devnet`. Copy the network value from the facilitator's
  `GET /supported`.
- `encodeBase64Json` / `decodeBase64Json` and the x402 v2 header
  names (`PAYMENT-REQUIRED`, `PAYMENT-SIGNATURE`, `PAYMENT-RESPONSE`).
  The v1 `X-PAYMENT` header is not supported.
- Atomic amounts: 1 token = 10^10 atomic units for every instrument
  (`decimalToAtomicCC`, `atomicToDecimalCC`).
- Verify-before-sign: decodes a prepared transaction and checks it
  against what the payer agreed to before the payer signs its hash
  (`decodePrepared`, `assertPreparedTransferMatches` and related).
- Merchant guards used by the middleware: `selectServerRequirements`,
  `assertAssetInstrumentConsistency`, `RedeemedStore`.

## Project

Code and issues:
[FTP-Tech-LLC/x402-canton-core](https://github.com/FTP-Tech-LLC/x402-canton-core).
Docs: [x402-docs.ftptech.xyz](https://x402-docs.ftptech.xyz).
Scheme spec:
[`scheme_exact_canton.md`](https://github.com/x402-foundation/x402/blob/main/specs/schemes/exact/scheme_exact_canton.md).
