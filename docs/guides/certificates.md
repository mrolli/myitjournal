# Certificates with OpenSSL

## Private Keys

### Create a Private Key

The following command creates a private key `domain.key` with a key length of
4096 bits. The key gets Triple-DES encrypted.

    openssl genrsa -des3 -out domain.key 4096

### Verify a Private Key

To check if a private key is valid, use the following command:

    openssl rsa -check -in domain.key

### Verify a Private Key Matches a Certificate and CSR

Get the MD5 sum for the private, the certificate and the CSR with the following
commands:

    openssl rsa -noout -modulus -in domain.key | openssl md5
    openssl x509 -noout -modulus -in domain.crt | openssl md5
    openssl req -noout -modulus -in domain.csr | openssl md5

If all three commands output the same MD5 sum, there is a high probability that
the private key, the certificate and the CSR match together.

### Encrypt a Private Key

Encrypt a previously unencrypted private key:

    openssl rsa -des3 -in unencrypted.key -out encrypted.key

Enter a desired pass phrase, to encrypt the key with.

### Decrypt a Private Key

Decrypt a previously encrypted private key:

    openssl rsa -in encrypted.key -out unencrypted.key

Enter the passphrase use to encrypt the pass phrase.

## Further Reading

* [OpenSSL Essentials](https://www.digitalocean.com/community/tutorials/openssl-essentials-working-with-ssl-certificates-private-keys-and-csrs#private-keys)
over at DigitalOcean
