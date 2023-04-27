# RSA

[RSA](https://en.wikipedia.org/wiki/RSA_(cryptosystem)) (Rivest–Shamir–Adleman) is a public-key encryption algorithm that is based on the difficulty of factoring the product of two large prime numbers. The security of RSA is based on the assumption that it is computationally infeasible to factor the product of two large primes. It can be used to encrypt and decrypt messages of arbitrary length. However, RSA is not typically used as a block cipher.

This notebook contains a full implementation of the algorithm from scratch. You can configure keys and block sizes and define a message (with any size) to be encrypted (Please note that the bigger the key size the longer it takes to finish execution. At key size 4096 bits it took 16 mins to finish which is the last run made on the notebook).

## Steps

**First**, generate the public/private keys which involves the following steps:
1. Generate two different large primes p and q
2. Calculate the modulus n = p × q
3. Calculate the totient φ(n) = (p − 1) × (q − 1)
4. Select for public exponent an integer e such that 1 < e < φ(n)
and gcd(φ(n), e) = 1
5. Calculate for the private exponent a value for d such that
d = e
−1 mod φ(n)
6. Public Key = [e, n]
7. Private Key = [d, n]

**Then**, divide the input message into blocks of defined **BLOCK_SIZE** and use padding if necessary.

**Finally**, perform the encryption and decryption as described below:
```
Enryption := C = M^e mod n
Decryption := M = C^d mod n

C -> cipher text
M -> plain text (message)
n -> modulus (equals to p*q)
e -> exponent (public key)
d -> multiplicative invese of the exponent mod φ(n) (private key)
```
