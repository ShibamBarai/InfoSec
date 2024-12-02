## **For CA**

### **1. Public-Key Cryptography**
  
#### **Definition and Concept**
Public-Key Cryptography is also called **asymmetric cryptography** because it uses two different keys:
1. **Public Key**: This is shared openly and is used for encryption or verifying digital signatures.
2. **Private Key**: This is kept secret and is used for decryption or signing messages.

It contrasts with **symmetric cryptography**, where the same key is used for both encryption and decryption. Public-key cryptography solves the **problem of secure key sharing**.

#### **History and Importance**
- Developed by **Whitfield Diffie** and **Martin Hellman** in 1976.
- Revolutionized cryptography by allowing secure communication without needing to exchange a secret key beforehand.
- Used in:
  1. **Encryption**: To protect the confidentiality of data.
  2. **Digital Signatures**: To verify the sender’s identity and message integrity.
  3. **Key Exchange**: To share session keys securely.

---

### **2. RSA Algorithm (Rivest–Shamir–Adleman)**

#### **What is RSA?**
- RSA is the most widely used public-key cryptography algorithm, named after its inventors.
- It is based on the mathematical difficulty of **factoring large prime numbers**.
- RSA is used in:
  1. **Secure web browsing** (HTTPS).
  2. **Encrypting sensitive information**.
  3. **Digital certificates** and **signatures**.

---

#### **How Does RSA Work?**
The RSA algorithm has **three main parts**:
1. **Key Generation**: Create public and private keys.
2. **Encryption**: Use the public key to convert plaintext into ciphertext.
3. **Decryption**: Use the private key to recover plaintext from ciphertext.

---

#### **Step 1: Key Generation**
1. **Choose Two Large Prime Numbers (\(p\) and \(q\))**:
   - Example: \(p = 13\), \(q = 17\).
2. **Compute \(n = p \times q\)**:
   - \(n = 13 \times 17 = 221\).
   - \(n\) is the **modulus** used in encryption and decryption.
3. **Calculate the Totient (\(\phi(n)\))**:
   \[
   \phi(n) = (p - 1)(q - 1)
   \]
   Example: \(\phi(221) = (13 - 1)(17 - 1) = 192\).
4. **Choose the Public Key Exponent (\(e\))**:
   - \(e\) must satisfy \(1 < e < \phi(n)\), and \(gcd(e, \phi(n)) = 1\) (relatively prime to \(\phi(n)\)).
   - Example: \(e = 35\).
5. **Calculate the Private Key (\(d\))**:
   - Solve:
     \[
     (e \times d) \mod \phi(n) = 1
     \]
   - Example:
     - \(35 \times d \mod 192 = 1\)
     - \(d = 11\).

- **Public Key**: \((e, n) = (35, 221)\).
- **Private Key**: \((d, n) = (11, 221)\).

---

#### **Step 2: Encryption**
The sender uses the **public key** \((e, n)\) to encrypt a message \(M\):
\[
C = M^e \mod n
\]
Where:
- \(M\): The plaintext message.
- \(C\): The ciphertext.

**Example**:
- Message \(M = 7\).
- Public Key: \((e, n) = (35, 221)\).
- Compute:
  \[
  C = 7^{35} \mod 221 = 106
  \]

---

#### **Step 3: Decryption**
The recipient uses their **private key** \((d, n)\) to decrypt the ciphertext \(C\):
\[
M = C^d \mod n
\]
**Example**:
- Ciphertext \(C = 106\).
- Private Key: \((d, n) = (11, 221)\).
- Compute:
  \[
  M = 106^{11} \mod 221 = 7
  \]
Thus, the original message \(M = 7\) is recovered.

---

### **3. Hash Functions**

### **What is a Hash Function?**
- A **hash function** is a mathematical function that takes an input (data of any size) and produces a fixed-size output called a **hash** or **digest**.
- Hash functions are **one-way functions**, meaning you can’t reverse the hash to find the original data.

### **Why Use Hash Functions?**
1. **Data Integrity**: To ensure data hasn’t been altered. For example, when downloading files, you can compare the hash of the file you downloaded with the original hash provided by the source.
2. **Password Security**: Hashes are used to store passwords securely in databases.
3. **Digital Signatures**: Hash functions help in verifying the integrity and authenticity of a message.

---

### **Properties of a Good Hash Function**
1. **Deterministic**:
   - The same input will always produce the same hash.
   - Example: Hashing "hello" will always give the same output, e.g., `5d41402abc4b2a76b9719d911017c592`.

2. **Preimage Resistance**:
   - It’s hard to reverse-engineer the original input from the hash.
   - Example: Given the hash `5d41402a...`, it’s almost impossible to figure out the input was "hello".

3. **Collision Resistance**:
   - It’s difficult to find two different inputs that produce the same hash.
   - Example: Hash("hello") ≠ Hash("world").

4. **Fast Computation**:
   - Hash functions are designed to be quick to compute, even for large inputs.

---

### **Examples of Hash Functions**
1. **MD5 (Message Digest 5)**:
   - Produces a 128-bit hash.
   - Example:
     - Input: "hello"
     - MD5 Hash: `5d41402abc4b2a76b9719d911017c592`
   - MD5 is no longer considered secure because it’s vulnerable to collisions.

2. **SHA-256 (Secure Hash Algorithm)**:
   - Produces a 256-bit hash.
   - Example:
     - Input: "hello"
     - SHA-256 Hash: `2cf24dba5fb0a...`

---

### **4. Message Authentication Code (MAC)**

### **What is MAC?**
- A **Message Authentication Code** is a small piece of data (a “tag”) generated using:
  1. A **message**.
  2. A **secret key**.
- The tag is sent along with the message to ensure:
  1. The **message has not been altered** (integrity).
  2. The **sender is authentic** (authentication).

---

### **How MAC Works**
1. The sender uses a **secret key** and the message to generate a MAC (the “tag”).
2. The MAC is attached to the message and sent to the receiver.
3. The receiver, using the same **secret key**, generates their own MAC and compares it with the received MAC.
   - If they match, the message is valid.
   - If they don’t match, the message has been altered or is from an unauthenticated sender.

---

### **Example**
Let’s say:
- Secret key: `1234`
- Message: `"Hello"`

Using a MAC algorithm, the sender generates:
- MAC: `HMAC_SHA256("Hello", "1234") = abcdef...`

The sender sends:
- Message: `"Hello"`
- MAC: `abcdef...`

The receiver:
1. Uses the same key (`1234`) to compute their own MAC: `abcdef...`.
2. Compares their MAC with the received MAC.

If they match: The message is valid.

---

### **Limitations of MAC**
1. The secret key must be **shared securely** between the sender and receiver.
2. It doesn’t provide non-repudiation (the sender could deny creating the MAC).
   
---

### **5. HMAC (Hash-based MAC)**

### **What is HMAC?**
- HMAC stands for **Hash-based Message Authentication Code**.
- It’s a more secure version of MAC that combines:
  1. A **cryptographic hash function** (like SHA-256).
  2. A **secret key**.

---

### **How Does HMAC Work?**
1. Start with a secret key and a message.
2. Perform **two layers of hashing**:
   - First, hash the message with the key and padding.
   - Second, hash the result again with the key and another padding.

Formula:
\[
\text{HMAC}(K, M) = \text{Hash}((K \oplus \text{opad}) \parallel \text{Hash}((K \oplus \text{ipad}) \parallel M))
\]
Where:
- \(K\): Secret key.
- \(M\): Message.
- \(opad, ipad\): Padding constants.

---

### **Advantages of HMAC**
1. Resistant to cryptographic attacks because of double hashing.
2. Provides both **integrity** and **authentication**.
3. Works with any cryptographic hash function (e.g., SHA-256, MD5).

---

### **Example**
1. Message: `"Hello"`
2. Key: `1234`
3. Hash Function: SHA-256

Steps:
1. Compute `Hash(Key || Message)`.
2. Compute `Hash(Key || IntermediateHash)`.

HMAC Output: `f9a8b3...`

The receiver uses the same process to verify the HMAC.

---

---

### **6. Digital Signatures**

### **What is a Digital Signature?**
A **digital signature** is like an electronic seal that:
1. Verifies the **sender’s identity**.
2. Ensures the **message has not been tampered with**.

---

### **Why Are Digital Signatures Important?**
1. **Authentication**: Confirms the sender is genuine.
2. **Integrity**: Ensures the message hasn’t been altered.
3. **Non-repudiation**: The sender cannot deny signing the message.

---

### **How Digital Signatures Work**
1. The sender creates a **hash of the message**.
2. The sender encrypts the hash using their **private key**. This is the digital signature.
3. The receiver:
   - Decrypts the signature using the sender’s **public key**.
   - Computes the hash of the received message.
   - Compares the two hashes.

If the hashes match: The message is valid.

---

### **Example**
1. Message: `"Hello"`
2. Sender’s Private Key: Used to encrypt the hash.
3. Digital Signature: `abcdef...`

Receiver:
1. Uses the sender’s Public Key to decrypt `abcdef...`.
2. Computes the hash of `"Hello"`.
3. Compares the two hashes.

If they match: The signature is verified.

---

### **Popular Digital Signature Algorithms**
1. **RSA**: Uses the RSA algorithm for signing.
2. **DSA (Digital Signature Algorithm)**: Based on discrete logarithms.
   - Example: Generates a 320-bit signature for 512-1024 bit security.

---

### **Real-World Use Case**
1. **Emails**: Digital signatures verify that an email was sent by the claimed sender.
2. **Software Downloads**: Software developers use digital signatures to verify that their software hasn’t been tampered with.

---

## **More Theory (all same)**

Here is a **detailed theoretical breakdown** of the topics for asymmetric cryptography.

---

### **1. RSA (Rivest–Shamir–Adleman Algorithm)**

#### **Definition:**
RSA is a widely used public-key cryptosystem that allows secure data transmission through asymmetric encryption. It is based on the mathematical difficulty of factoring large composite numbers.

#### **Key Characteristics:**
- It uses **two keys**: a public key (for encryption) and a private key (for decryption).
- Security relies on the **factoring problem**: It is computationally infeasible to factorize large numbers into primes.
- RSA can be used for:
  1. **Encryption**: To ensure confidentiality.
  2. **Digital Signatures**: To verify authenticity.

---

#### **Steps in RSA:**

1. **Key Generation:**
   - Select two large prime numbers \(p\) and \(q\).
   - Compute \(n = p \times q\) (modulus).
   - Compute \(\phi(n) = (p-1)(q-1)\) (Euler’s totient function).
   - Choose a public key exponent \(e\) such that \(1 < e < \phi(n)\) and gcd(\(e, \phi(n)\)) = 1.
   - Compute the private key \(d\) such that:
     \[
     (e \times d) \mod \phi(n) = 1
     \]
   - Publish \((e, n)\) as the public key. Keep \((d, n)\) as the private key.

2. **Encryption:**
   - Convert plaintext message \(M\) to a number less than \(n\).
   - Encrypt using the public key:
     \[
     C = M^e \mod n
     \]
   - \(C\): Ciphertext.

3. **Decryption:**
   - Decrypt using the private key:
     \[
     M = C^d \mod n
     \]
   - Recover plaintext \(M\).

---

#### **Example:**
1. Choose \(p = 3\), \(q = 11\):
   - \(n = 3 \times 11 = 33\),
   - \(\phi(n) = (3-1)(11-1) = 20\).

2. Choose \(e = 7\), gcd(\(7, 20\)) = 1.

3. Compute \(d\) such that \((7 \times d) \mod 20 = 1\), \(d = 3\).

4. Public key: \((7, 33)\), Private key: \((3, 33)\).

5. Encrypt \(M = 5\):
   \[
   C = 5^7 \mod 33 = 14
   \]

6. Decrypt \(C = 14\):
   \[
   M = 14^3 \mod 33 = 5
   \]

---

#### **Applications of RSA:**
1. **Secure Web Browsing**: Used in HTTPS.
2. **Email Encryption**: Ensures confidentiality of emails.
3. **Digital Signatures**: Verifies sender authenticity.

---

### **2. Hashing Functions**

#### **Definition:**
A hash function is a cryptographic algorithm that takes an input of arbitrary length and produces a fixed-length output, called a hash or digest.

#### **Properties of Hash Functions:**
1. **Deterministic**: Same input always produces the same hash.
2. **Collision Resistance**: Difficult to find two different inputs with the same hash.
3. **Preimage Resistance**: Impossible to reverse-engineer the input from the hash.
4. **Fixed Size**: Output length is fixed, regardless of input size.

---

#### **Examples of Hash Functions:**
1. **MD5 (Message Digest 5)**:
   - Produces a 128-bit hash.
   - Vulnerable to collisions.
2. **SHA-256 (Secure Hash Algorithm)**:
   - Produces a 256-bit hash.
   - Widely used in blockchain and digital certificates.

---

#### **Applications of Hash Functions:**
1. **Data Integrity**: Verifies files and messages haven’t been altered.
2. **Password Security**: Stores hashed passwords securely.
3. **Digital Signatures**: Verifies message authenticity.

---

### **3. Message Authentication Code (MAC)**

#### **Definition:**
A **Message Authentication Code (MAC)** is a cryptographic checksum generated using a secret key and a message to ensure data integrity and authenticity.

#### **How MAC Works:**
1. Sender and receiver share a **secret key**.
2. Sender computes MAC:
   \[
   MAC = F(Key, Message)
   \]
3. The receiver computes the MAC again upon receiving the message. If both MACs match, the message is authentic.

---

#### **Properties of MAC:**
1. **Authenticity**: Ensures the message is from the claimed sender.
2. **Integrity**: Ensures the message hasn’t been tampered with.

---

#### **Limitations:**
- Does not provide non-repudiation (sender can deny sending the message).

---

### **4. HMAC (Hash-based MAC)**

#### **Definition:**
**HMAC** is a specific type of MAC that combines a hash function (like SHA-256) with a secret key for added security.

#### **How HMAC Works:**
1. Padding constants (opad and ipad) are used.
2. Perform double hashing with the secret key:
   \[
   HMAC = Hash((Key \oplus opad) || Hash((Key \oplus ipad) || Message))
   \]

---

#### **Advantages of HMAC:**
1. Resistant to cryptographic attacks.
2. Works with any hash function (e.g., MD5, SHA-1).
3. Ensures both integrity and authenticity.

---

#### **Applications of HMAC:**
1. **TLS/SSL Protocols**: Ensures secure communication on the web.
2. **APIs**: Verifies data authenticity in API requests.

---

### **5. Digital Signature**

#### **Definition:**
A **digital signature** is a cryptographic mechanism that:
1. Verifies the authenticity of the sender.
2. Ensures the integrity of the message.
3. Provides **non-repudiation** (the sender cannot deny their involvement).

---

#### **How Digital Signatures Work:**
1. The sender creates a hash of the message.
2. The hash is encrypted using the sender’s private key. This becomes the **digital signature**.
3. The receiver:
   - Decrypts the signature using the sender’s public key to retrieve the hash.
   - Computes the hash of the received message.
   - Compares the two hashes. If they match, the signature is valid.

---

#### **Applications of Digital Signatures:**
1. **Emails**: Verifies sender authenticity.
2. **Software Downloads**: Ensures the software hasn’t been tampered with.
3. **Blockchain**: Secures transactions.

---

#### **Example of Digital Signatures:**
1. Message: `"Hello"`
2. Hash: `abcdef...`
3. Signature: Encrypted hash using the private key.
4. Verification: Decrypt signature using the public key and compare hashes.

---

## **Only Numerical**

Certainly! I'll reanalyze your lecture notes thoroughly and provide step-by-step solutions to the problems and additional explanations wherever needed. Let me extract and address the **numerical examples and key problems** from the notes.

### **Reanalysis of Problems in the Notes**
The lecture notes contain problems for:
1. **RSA Key Generation** (finding \(e\), \(d\), encryption, and decryption).
2. **Diffie-Hellman Key Exchange**.
3. **HMAC Calculations**.
4. Examples related to **Digital Signatures**.

Let’s go through each topic with an explanation and problem-solving steps.

---

### **1. RSA Problems**

#### **Key Problem 1: Find the value of \(e\)**
**Given:**
- \(p = 3\), \(q = 11\), \(d = 7\).

**Solution:**
1. Compute \(n = p \times q\):
   \[
   n = 3 \times 11 = 33
   \]

2. Compute \(\phi(n) = (p-1)(q-1)\):
   \[
   \phi(n) = (3-1)(11-1) = 2 \times 10 = 20
   \]

3. Use the relation:
   \[
   d \times e \mod \phi(n) = 1
   \]
   Substitute \(d = 7\), \(\phi(n) = 20\):
   \[
   7 \times e \mod 20 = 1
   \]

4. Solve for \(e\):
   - Multiply \(7 \times e\) until it’s divisible by 20 with a remainder of 1:
     - \(7 \times 1 = 7 \mod 20 \neq 1\)
     - \(7 \times 2 = 14 \mod 20 \neq 1\)
     - \(7 \times 3 = 21 \mod 20 = 1\)

   So, \(e = 3\).

---

#### **Key Problem 2: Find the value of \(d\)**
**Given:**
- \(p = 3\), \(q = 5\), \(e = 3\).

**Solution:**
1. Compute \(n = p \times q\):
   \[
   n = 3 \times 5 = 15
   \]

2. Compute \(\phi(n) = (p-1)(q-1)\):
   \[
   \phi(n) = (3-1)(5-1) = 2 \times 4 = 8
   \]

3. Use the relation:
   \[
   d \times e \mod \phi(n) = 1
   \]
   Substitute \(e = 3\), \(\phi(n) = 8\):
   \[
   d \times 3 \mod 8 = 1
   \]

4. Solve for \(d\):
   - Multiply \(3 \times d\) until it’s divisible by 8 with a remainder of 1:
     - \(3 \times 1 = 3 \mod 8 \neq 1\)
     - \(3 \times 2 = 6 \mod 8 \neq 1\)
     - \(3 \times 3 = 9 \mod 8 = 1\)

   So, \(d = 3\).

---

#### **Key Problem 3: Encrypt and Decrypt a Message**
**Given:**
- \(p = 17\), \(q = 11\), \(e = 7\), Message \(M = 88\).

**Solution:**
1. Compute \(n = p \times q\):
   \[
   n = 17 \times 11 = 187
   \]

2. Compute \(\phi(n) = (p-1)(q-1)\):
   \[
   \phi(n) = (17-1)(11-1) = 16 \times 10 = 160
   \]

3. Public key: \((e, n) = (7, 187)\).

4. Compute private key \(d\):
   Solve:
   \[
   d \times e \mod \phi(n) = 1
   \]
   Substitute \(e = 7\), \(\phi(n) = 160\):
   - \(7 \times d \mod 160 = 1\).
   - \(d = 23\) (found by trial or extended Euclidean algorithm).

5. **Encryption**:
   Use:
   \[
   C = M^e \mod n
   \]
   Substitute \(M = 88\), \(e = 7\), \(n = 187\):
   \[
   C = 88^7 \mod 187 = 11
   \]

6. **Decryption**:
   Use:
   \[
   M = C^d \mod n
   \]
   Substitute \(C = 11\), \(d = 23\), \(n = 187\):
   \[
   M = 11^{23} \mod 187 = 88
   \]

   The decrypted message is \(M = 88\).

---

### **2. Diffie-Hellman Key Exchange**

#### **Key Problem: Compute the Shared Secret**
**Given:**
- \(g = 5\), \(p = 23\), \(a = 6\), \(b = 15\).

**Solution:**
1. **Step 1**: Compute \(A\) (Alice's public key):
   \[
   A = g^a \mod p = 5^6 \mod 23 = 8
   \]

2. **Step 2**: Compute \(B\) (Bob's public key):
   \[
   B = g^b \mod p = 5^{15} \mod 23 = 19
   \]

3. **Step 3**: Compute shared secret:
   - Alice computes:
     \[
     S = B^a \mod p = 19^6 \mod 23 = 2
     \]
   - Bob computes:
     \[
     S = A^b \mod p = 8^{15} \mod 23 = 2
     \]

   Shared secret: \(S = 2\).

---

### **3. HMAC Problems**

#### **Example Problem: Compute HMAC**
**Given:**
- Message \(M = "Hello"\),
- Key \(K = "1234"\),
- Hash function: SHA-256.

**Solution:**
1. **Step 1**: Create padded keys:
   - Inner padding (\(ipad\)) and outer padding (\(opad\)) are constants.
   - \(K \oplus ipad\): XOR key with \(ipad\).
   - \(K \oplus opad\): XOR key with \(opad\).

2. **Step 2**: Hash the inner combination:
   \[
   H_1 = \text{Hash}((K \oplus ipad) \parallel M)
   \]

3. **Step 3**: Hash the outer combination:
   \[
   HMAC = \text{Hash}((K \oplus opad) \parallel H_1)
   \]

   Use SHA-256 to compute the intermediate and final hashes.

---

### **4. Digital Signature Problems**

#### **Example Problem: Verify a Signature**
**Given:**
- Message \(M = "Hello"\),
- Hash of the message: \(H(M) = 5d41402a...\),
- Sender’s private key \(d = 7\),
- Modulus \(n = 33\),
- Public key \(e = 3\).

**Solution:**
1. Sender computes the signature:
   \[
   S = H(M)^d \mod n
   \]
   Substitute \(H(M) = 5d41402a...\) (convert to number), \(d = 7\), \(n = 33\).

2. Receiver verifies:
   \[
   H'(M) = S^e \mod n
   \]
   Substitute \(S\), \(e = 3\), \(n = 33\).

3. If \(H'(M)\) matches the original \(H(M)\), the signature is valid.

---

## **Bengali Basic Explanation**

### **1. RSA Algorithm (Rivest–Shamir–Adleman)**

#### **RSA Ki?**
RSA holo **ekta public-key cryptosystem** ja **asymmetric encryption** er upor base kore. Er mane holo, **public key** diye message **encrypt** kora hoy ebong **private key** diye **decrypt** kora hoy. **Public key** je keu use korte pare, kintu **private key** sudhu recipient (receiver) er kase thake.

**Key Features:**
- **Encryption**: Message ke safe rakhte public key use kore encryption kora hoy.
- **Digital Signatures**: Sender er identity verify korte private key diye signature kora hoy.
- **Security**: RSA er security chhilo **factoring problem** er upor, mane je onek boro prime number er **factorization** khub kothin, jar karone RSA ke safe rakha hoy.

#### **RSA Steps:**

1. **Key Generation (Chabi toiri kora)**:
   - **Step 1**: Duto large prime number \(p\) aar \(q\) choose koro. Example: \(p = 17\), \(q = 11\).
   - **Step 2**: Compute modulus \(n = p \times q\). Example: \(n = 17 \times 11 = 187\).
   - **Step 3**: Compute totient function \(\phi(n)\), ja \((p-1)(q-1)\) er moto kora hoy. Example: \(\phi(187) = (17-1)(11-1) = 160\).
   - **Step 4**: Choose public key exponent \(e\) jehetu \(1 < e < \phi(n)\) ebong \(gcd(e, \phi(n)) = 1\). Example: \(e = 7\).
   - **Step 5**: Calculate private key \(d\) er value ja satisfy kore: \((e \times d) \mod \phi(n) = 1\). Example: \(d = 23\).

2. **Encryption (Message Encrypt kora)**:
   - **Step 1**: Public key \(e\) ebong \(n\) use kore message \(M\) ke encrypt kora hoy. Formula: 
     \[
     C = M^e \mod n
     \]
     Jekhane \(C\) holo ciphertext ebong \(M\) holo original message.

3. **Decryption (Message Decrypt kora)**:
   - **Step 1**: Private key \(d\) ebong \(n\) use kore ciphertext \(C\) ke decrypt kora hoy. Formula:
     \[
     M = C^d \mod n
     \]
     Jekhane \(M\) holo decrypted message.

#### **Example:**
1. Choose \(p = 17\), \(q = 11\).
   - \(n = 17 \times 11 = 187\), \(\phi(n) = (17-1)(11-1) = 160\).
   - \(e = 7\) (chosen so that \(gcd(e, \phi(n)) = 1\)).
   - Calculate \(d\): \((7 \times d) \mod 160 = 1\), so \(d = 23\).
   - Public key: \((7, 187)\), Private key: \((23, 187)\).

2. Encrypt \(M = 88\):
   \[
   C = 88^7 \mod 187 = 11
   \]
   
3. Decrypt \(C = 11\):
   \[
   M = 11^{23} \mod 187 = 88
   \]

---

### **2. Hash Functions**

#### **Hash Function Ki?**
Hash function holo ekta mathematical function ja **any length er input** ke **fixed length er output** (digest) e convert kore. Eta **one-way function** er moto kaj kore, mane input ke **reverse** kore ber kora jaay na. Hash function mainly **data integrity**, **password storage**, ebong **digital signatures** er jonno use kora hoy.

#### **Hash Function er Properties:**
1. **Deterministic**: Same input er jonno same output hobe. Example: "Hello" er hash shob somoy same thakbe.
2. **Fixed Length Output**: Input jekono size holeo output er size fixed thakbe.
   - Example: MD5 hash always 128-bit, SHA-256 always 256-bit.
3. **Collision Resistance**: Duto alada input same hash generate korbe na.
4. **Preimage Resistance**: Hash theke original input ber kora jabe na.

#### **Examples of Hash Functions**:
1. **MD5**:
   - 128-bit output.
   - Example: "Hello" -> MD5 hash: `5d41402abc4b2a76b9719d911017c592`.
   - Vulnerable to collisions, so not secure anymore.

2. **SHA-256**:
   - 256-bit output.
   - Example: "Hello" -> SHA-256 hash: `2cf24dba5fb0a...`.

#### **Use of Hash Functions**:
1. **Data Integrity**: Verifying that files or messages haven't been tampered with.
2. **Password Storage**: Secure password storage by hashing passwords before saving them.
3. **Digital Signatures**: Used to generate the hash for signing.

---

### **3. Message Authentication Code (MAC)**

#### **MAC Ki?**
Message Authentication Code (MAC) holo ekta cryptographic checksum je **message** aar **secret key** diye generate kora hoy. Eta use hoy **message authenticity** r **integrity** verify korar jonno. MAC er main purpose holo **message ke tamper na kora** ebong **sender ke verify kora**.

#### **How MAC Works**:
1. Sender ebong receiver er kase same **secret key** thake.
2. Sender message er sathe **MAC** generate kore secret key diye.
3. Receiver o same key diye **MAC** compute kore. Jodi duita MAC match kore, tahole message **authentic**.

#### **MAC Properties**:
1. **Authenticity**: Sender er identity verify kora.
2. **Integrity**: Message ta change hoyeche ki na ta check kora.

---

### **4. HMAC (Hash-based MAC)**

#### **HMAC Ki?**
HMAC holo ekta specific type er MAC ja hash function (like SHA-256) ke secret key er sathe combine kore. HMAC ke **more secure** banano hoyeche **double hashing** diye, ja cryptanalysis er against protect kore.

#### **How HMAC Works**:
1. **Key padding** kora hoy inner padding (\(ipad\)) and outer padding (\(opad\)) er sathe.
2. HMAC function:
   \[
   HMAC = \text{Hash}((K \oplus opad) \parallel \text{Hash}((K \oplus ipad) \parallel M))
   \]
   Jekhane:
   - \(K\) secret key,
   - \(M\) message,
   - \(ipad\) and \(opad\) are padding constants.

#### **Advantages of HMAC**:
1. **Security**: Double hashing makes it resistant to attacks.
2. **Integrity & Authenticity**: Ensures both message authenticity and integrity.

#### **Use of HMAC**:
- **TLS** and **SSL** protocols (for web security).
- **API request verification**.

---

### **5. Digital Signature**

#### **Digital Signature Ki?**
Digital signature ekta cryptographic method ja **sender er identity verify** kore ebong **message integrity** ensure kore. Eta **non-repudiation** provide kore, mane sender **signature deny** korte parbe na.

#### **How Digital Signatures Work**:
1. Sender **message hash** generate kore.
2. Hash ke **private key** diye encrypt kore, jeita **digital signature** hoye jay.
3. Receiver:
   - Sender er **public key** diye signature ke decrypt kore.
   - Message er hash compute kore.
   - Compare kore jei duita hash match kore tahole message valid.

#### **Use of Digital Signatures**:
1. **Emails**: Authenticity verify kora.
2. **Software Downloads**: Ensure kora je software tampered hoye nai.
3. **Blockchain Transactions**: Transaction security.
