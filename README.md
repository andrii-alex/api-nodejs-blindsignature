# Blind Signature API

This Node.js Express API provides functionality for blind signatures. Blind signatures are cryptographic protocols where a user can obtain a signature on a message without revealing the content of the message to the signer.

## Installation

1. Clone the repository:

   ```bash
   git clone <repository_url>
   cd <repository_directory>
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

## Usage

### Key Generation

```javascript
const { keyGeneration } = require("./util");

const key = keyGeneration();
// Use the key for further operations
```

### Import Key Pair From Files

```javascript
const { importKeyPairFromFile } = require("./util");

const key = importKeyPairFromFile();
// Use the key for further operations
```

### Get Ethereum Address From RSA Key

```javascript
const { getEthereumAddressFromRSAKey } = require("./util");

const ethereumAddress = getEthereumAddressFromRSAKey(key);
// Use the Ethereum address as needed
```

### Blinding and Signing

```javascript
const { blind, sign, unblind } = require("./util");

const { blinded, r } = blind({ message, key, N, E });
const signed = sign({ blinded, key });
const unblinded = unblind({ signed, key, r, N });
// Use the blinded, signed, and unblinded values as needed
```

### Verification

```javascript
const { verify, verify2, verifyBlinding } = require("./util");

const result1 = verify({ unblinded, key, message, E, N });
const result2 = verify2({ unblinded, key, message });
const result3 = verifyBlinding({ blinded, r, unblinded, key, E, N });
// Use the verification results as needed
```

## File Structure

- `private.pem`: Private RSA key file.
- `public.pem`: Public RSA key file.
- `util.js`: Utility functions for key generation, blinding, signing, unblinding, and verification.

## Dependencies

- `secure-random`: Generates cryptographically strong random numbers.
- `jsbn`: JavaScript library for arbitrary precision integer arithmetic.
- `js-sha256`: SHA-256 implementation for JavaScript.
- `node-rsa`: RSA implementation for Node.js.
- `web3`: Ethereum JavaScript API.

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgments

- [secure-random](https://www.npmjs.com/package/secure-random)
- [jsbn](https://www.npmjs.com/package/jsbn)
- [js-sha256](https://www.npmjs.com/package/js-sha256)
- [node-rsa](https://www.npmjs.com/package/node-rsa)
- [web3](https://www.npmjs.com/package/web3)

Feel free to customize this README based on your specific project details.
