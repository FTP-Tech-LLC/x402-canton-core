# Test fixtures

Real Canton MainNet prepared transactions, base64. The `packages/core`
tests read them from this path. They come from the agent wallet's
fixtures in
[x402-canton-agent](https://github.com/FTP-Tech-LLC/x402-canton-agent).

None of them can authorize anything: each was either never signed or
already executed. This directory is not a package.
