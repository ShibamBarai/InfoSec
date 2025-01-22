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

![image](https://github.com/user-attachments/assets/17cbe68c-e058-4546-a2e8-bd5d6230545d)

![image](https://github.com/user-attachments/assets/34842ba0-5880-4c5c-bf70-18a94ae044bd)

---

![image](https://github.com/user-attachments/assets/12876468-3f7d-4fc5-9433-3d29debcfa98)

---

![image](https://github.com/user-attachments/assets/f7a84118-648d-42f2-8ba7-b4e27c662695)

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

![image](https://github.com/user-attachments/assets/68b6d437-e201-4a8c-8a24-32fe2b00b0ac)


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

   MAC = F(Key, Message)
  
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

### **Reanalysis of Problems in the Notes**
The lecture notes contain problems for:
1. **RSA Key Generation** (finding \(e\), \(d\), encryption, and decryption).
2. **Diffie-Hellman Key Exchange**.
3. **HMAC Calculations**.
4. Examples related to **Digital Signatures**.

Let’s go through each topic with an explanation and problem-solving steps.

---

![image](https://github.com/user-attachments/assets/99ea0ee7-acf6-4a6d-baf6-ca93e5b56d81)


![image](https://github.com/user-attachments/assets/ad7c6d23-101a-4324-85da-84911df69a2c)


---

![image](https://github.com/user-attachments/assets/f6667cf9-2d22-442c-a5ab-2a28b7d32d64)

![image](https://github.com/user-attachments/assets/b1dbe01d-ff82-43c4-b43a-17f3816256c3)

---

![image](https://github.com/user-attachments/assets/a28fc0dc-f90f-4beb-a093-1faf8d2cedb4)


![image](https://github.com/user-attachments/assets/e4f4a05a-054c-4583-9923-548fe69b85bb)

![image](https://github.com/user-attachments/assets/97ecdfca-0da2-4cfc-b7e6-28e0abc03e8c)


---

### **2. Diffie-Hellman Key Exchange**

![image](https://github.com/user-attachments/assets/d7355e3a-72af-4071-8674-0d10016c8729)

![image](https://github.com/user-attachments/assets/88543021-c0f7-41c4-9d11-31c445c6b21e)

---

### **3. HMAC Problems**

![image](https://github.com/user-attachments/assets/042cbe2c-8b9d-4d47-8e66-221a04bf8de0)


![image](https://github.com/user-attachments/assets/95c13df5-518e-4db9-b30f-cf78d256b1be)


---

### **4. Digital Signature Problems**

![image](https://github.com/user-attachments/assets/298cf659-ff65-4c56-964d-2809986bd9fa)


![image](https://github.com/user-attachments/assets/0c8080f3-77a9-4751-81cb-2641c6fa7f97)


