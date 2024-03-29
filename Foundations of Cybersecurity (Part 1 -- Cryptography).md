Cryptography: The science of secret writing

Cryptanalysis: The science of code breaking

Cryptology = Cryptography + Cryptanalysis

Cipher: An algorithm that turns messages (plaintext) into unreadable messages (ciphertext)
### Key
A key is basically the stuff we use as a way to encrypt a message.

Keep this a secret.

A Key is a fundamental part of cryptography. Even in the rot-n algorithm, we can think of 'n' as a key.

## Types of Cryptography

### Secret Key Cryptography

As called __symmetric cryptography__, the key is used for both encrypting and decrypting, ie, it's a two way street.
A nice analogy is a locked box that can be opened with only one key. The messenger can put the message in the box, while the receiver will use the same key (ideally a copy) to open the box

#### Problems with Secret Key
1. Distributing keys: There is no practical way to distribute a secret key over a network.
	Solution: Public key cryptography

This problem led to our next point...

### Public Key Cryptography
Also called __asymmetric cryptography__.
You generate a pair of keys. A public and private key. The public key is freely available and is used to encrypt the message, the private key -(held by the key pair owner) - is used to decrypt the message.


------------------------------------
====================================

### Jan 17, 2024 -- Tutorial 1

#### Modular arithmetic (Check physical notes)
I like to call it 'remainder arithmetic'
It only allows integer division
##### Congruences and modular addition
12 mod 12 and 24 mod 12 are congruent. ie, any two numbers in the integer space that had the same result in the modulo set are equivalent (congruent) to each other, ie,

for x, y, z ...{x === y | for all x, y in Z such that x mod a = c and y mod a = c }

Multiplicative inverse
y * 1/y = e (where e is 1, ie, the identity element)

## 22 Jan, 2022 (Lecture)
### Classical Encryption Techniques

#### Ways to break a cipher
- Brute force
- Cryptanalysis

#### Cryptanalysis
Exploit mathematical properties of the cipher
- In the case of __secret key ciphers__ 

#### Hardest to attach
- Ciphertext-only
- Known plaintext
- Chosen plaintext

Monoalphabet Subsitution:
one -> one mapping between characters/alphabets

Problems
Approximate messages can be extracted by using the word frequencies

## 23 Jan, 2024 (Lecture)
### Polyalphabetic Cipher
Plaintext -> a

## 29 Jan, 2024 (Lecture)
### Modern Ciphers
Another cipher classification:
* Stream Ciphers
* Block Ciphers

#### Stream Ciphers
Encode one bit/byte at a time
Examples: Rot-n, Vignere, RC4
#### Block Ciphers
Accumulates and encodes. Can theoretically work as a stream cipher by setting a block to one bit/byte
Examples: DES, AES, RSA

### DES (Data Encryption Standard)
- A symmetric block cipher (NIST, 1977)
- Block size of 64 bits, Key size 56 bits
- 16 rounds

#### Weakness
- The key is too short
- S-boxes. Fear that they were designed to be breakable
### Modern Alternative: AES

###  3-DES/Triple-DES (Should have been better, but Cryptanalysis and Moore's law disagreed)


## RSA Cipher!!!
First public key encryption algorithm
- Rivest, Shamir, Adleman 1977
- Turing award 2002
### Details
- Len(Public key) == Len(Private key)
### Encryption
C = M^e mod n
### Decrytion
M = C^d mod n


### KEY GENERATION
We will be tested on this

## 30 Jan, 2024 (Lecture)
x = ed mod phi = 1

Let phi = 160 (from the slides)

the set of numbers that will result in 1 mod 161
[1] = {161, 321, 481}
We must pick e and d such that e * d = 161 or 321 or 481
d will be the multiplicative inverse of e
e = 7 because gcd(160, 7) == 1
7 * 23 = 161
therefore d = 23 and is the multiplicative inverse of 7

___Remember___ that phi is gotten from (p - 1) * (q-1) where p * q = n

we use _n_ in as the actual mod, not _phi_
C = M^e mod n
where C is the Ciphertext, M is the message, and n is the mod

e is gotten from gcd(_phi_, e) == 1

So Decryption
M = C^d mod n
where d is the multiplicative inverse of e mod _phi_

### Padding
Padding is essential for block ciphers to indicate where a plaintext ends and ensure proper decrytion.
___PKCS#5___ is the standard
If the last 64-bit block(basically 8-bytes) is filled, add an extra block and fill it with the value '8' to indicate that all blocks are filled
Else, fill the last empty bytes of a block with the number of empty bytes

### Modes
These define HOW the plaintext is encrypted
#### Electronic Code Block (ECB)
Blocks here are encrypted in parallel (ie, independent of each other) because we can divide the data into blocks prior to encryption. The entire message will be needed in a naive implementation

#### Cipher Block Chaining (CBC)

#### Cipher Feedback (CFB) Mode

## 5 Feb, 2024
Padding

### Output Feedback Mode
#### Advantage
- Insensitive to transmission errors

## 6 Feb, 2024
### Message Digest (Hashing)
A digest is the output of a Hashing function
It is used as a unique "signature" to identify something in a computer system

Digest $\ne$ Encryption
Encryption is reversible, a hash is not
#### Idea? (Entropy as signature)
Look up the possibility of using entropy as a way of identifying something. A hash function essentially puts out irreversible gibberish. The usefulness is in the fact the hash acts as a signature even though we do not know what the original text is/was (ie, no useful information on text, the entropy IS the useful info)

#### Problems with hashing
##### Collisions
This is because a hash gives a fixed sized output respective of the the input length. This implies the the space of inputs is larger than the space of outputs, which means we cannot get a 1:1 mapping between the two sets

### Usefulness
We can "sign" messages using a hash function. Alice sends the digest and the message to Bob. If the message is tampered with, the message hash will not match the digest sent earlier.
Of course, if the attacker (Trudy) intercepts both the digest and the message, modifies the message, hashes it and then sends the new Digest and modified message to Bob, there is no way for him to know

##### How do we solve this?


## 12 Feb, 2024 (Lecture)

### MACs and Signatures

Back to this question "##### How do we solve this?"
The answer is ___Authentication___ 
We do this using MACs (Message Authentication Code) and Signatures
- __MAC__ = digest + secret key cryptography
- Signature = digest + public key cryptography

#### MAC
Basically, Alice generates a MAC by passing the plaintext and a secret key into a digest algorithm. She sends the MAC and the plaintext to Bob. When Bob gets the plaintext, he uses the same digest algorithm to generate a MAC using the plaintext + secret key (which should be the same). If Bob's generated MAC and the MAC sent by Alice doesn't match, then the message has been tampered with.
##### Problems with MAC
Securely distributing the Secret key
__Solution__: PK cryptography, in this case, the use of Signatures.

#### Signatures
The digest here is created differently here. The secret key is NOT an input to the digest algorithm. Alice's private key is instead used to encrypt the generated digest from the plain text. ie, signing the digest

Bob receives the plaintext and the encrypted digest decrypts the digest. He generates his own digest using the plain text and then compares the decrypted digest to his generated digest. If they do not match, then he knows that the message has been tampered with.

## 13 Feb, 2024 (Lecture)
#### The birthday Attach
Using the concept of the birthday paradox, find any two messages that have the same digest/hash. Here, we don't care about finding a message that has the same hash as the message we want to unravel. That's too computationally difficult. We just want to find two messages with the same hash



### Certificates
Public key systems are used for
- Confidentiality: encryption
- Authentication and integrity: signatures
#### Problems with public key
- The system can be hacked if the public key has to be downloaded from the web

Scenario: If Alice need to send a message to Bob, and goes to his website to get his public key, Trudy can hack the his website and intercept the download request and send her public key to Alice instead. This means that Alice will use Trudy's pub key to encrypt her message. Trudy can then conveniently decrypt it and either read it, or change it and send the fake message to Bob instead. This is a type of man in the middle attack

So what's the solution? Signatures of course!!!
Here, the signatures are called certificates

What do they do?
They sign the public keys to ensure the integrity of the key. ie, they make a digest that must match the digest the end-user generates from the actual public key

Of course, we come full circle and the certificate issuer in turn needs to have their own public key signed. The solution to this is a naive one, where a "Chain of Certificates" are used, with the chain ending in a final authority that can self sign its own public key. The biggest such final authority is VeriSign (heard of them have you :) ) 

### Key Agreement
How do we distribute shared secret keys between two or more participants (remember this problem?)

The Diffe-Hellman protocol comes to the rescue.

#### Diffe-Hellman Protocol

##### Problem with Diffe-Hellman
Man in the middle attack is possible. Trudy can still implant her own e(a) and e(b) values with her own e(c) and e(d) during the message passing