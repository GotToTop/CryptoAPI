# CryptoAPI
REST API backend for cryptography.

## Usage
To use, compile and run executable. You can now access the API over HTTP.
To hash a string, send JSON object `{"method":"sha256","contents":"aGVsbG8=","salt":"3q2+7w=="}`
where method is one of supported methods: sha256, sha1, md5, sha512, sha384. Both contents and salt are base64 encoded byte array (in this case, `aGVsbG8=` is base64 encoded string `hello` and `3q2+7w==` is base64 encoded byte array `0xDEADBEEF`)
Server will reply with a JSON object `{"method":"sha256","contents":"fec5a7b4f37f65b902d803018e84cdcbea213fe7ec963db2ac5471a470845f6d","salt":"3q2+7w=="}`, where `method` will be the method you've chosen and `contents` will contain HEX string representation of a hash. `salt` field will contain base64 value of salt.

Salting is done by hashing "`contents`+`salt`". If no salt is provided, no salt is used.