### **Introduction to Information Security**
- **What is Information Security?**
  - When data travels between computers, it often leaves the safety of its protected physical environment. Once out in the open, it becomes vulnerable to unauthorized people who may try to modify or misuse the data, either for fun or their own benefit.
  - Information security is all about protecting this data and the systems storing or transmitting it from:
    - Unauthorized access (people who shouldn’t see it),
    - Unauthorized use (people using it without permission),
    - Disclosure (leaking information to the wrong people),
    - Disruption (causing systems to fail or data to disappear), or
    - Destruction (permanently damaging or erasing the data).

---

#### **OSI Security Architecture**
The OSI (Open Systems Interconnection) Security Architecture is a framework to understand the different elements required to secure an organization's information and systems. This framework includes:

1. **Security Attack:**
   - This refers to any deliberate action that compromises (harms or weakens) the security of the organization's information or systems. Examples include hacking, stealing data, or spreading malware.

2. **Security Mechanism:**
   - These are methods or techniques designed to:
     - Detect security attacks (like a firewall catching a hacker’s attempt to access your system),
     - Prevent attacks from happening, and
     - Recover from attacks that may have already occurred.

3. **Security Service:**
   - A set of actions or services aimed at improving the overall security of the organization’s data and systems, such as protecting data while it’s being processed or transferred between systems.

---

#### **Types of Security Services**
There are several key types of security services to protect data and systems:

1. **Confidentiality:**
   - Ensures that sensitive data can only be read by authorized individuals.
   - For example, only an authorized employee should be able to read confidential company files.

2. **Authentication:**
   - Confirms that the origin of a message or document is genuine.
   - For instance, if you receive an email, authentication ensures it really came from the person it claims to be from, not an impersonator.

3. **Integrity:**
   - Guarantees that data has not been tampered with or altered without permission.
   - This includes protecting data from being deleted, modified, delayed, or replayed by unauthorized people.

4. **Non-repudiation:**
   - Prevents the sender or receiver of a message from denying later that the message was sent or received. 
   - This ensures accountability in communications, for example, during a financial transaction.

5. **Availability:**
   - Ensures that data, applications, and systems are available to authorized users whenever needed.
   - For example, a company’s website or email system should be operational and accessible for its employees and customers.

---

#### **Security Mechanisms**
To achieve the above security services, several mechanisms are used. One of the most important mechanisms is **cryptography.**

- Cryptography involves transforming information so that only authorized people can read it. Examples of security mechanisms include:
  1. **Encipherment:** Converting information into an unreadable format using encryption.
  2. **Digital Signatures:** Ensuring authenticity and integrity of data by adding a unique signature to a document or message.
  3. **Access Control:** Restricting access to information and systems only to authorized individuals.

---

#### **Security Attacks**
Security attacks are attempts by malicious users to compromise data or systems. These attacks can be broadly categorized as:

1. **Interruption:**
   - The system or data is made unavailable or unusable.
   - Example: A server crash due to a cyberattack is an attack on the system’s availability.

2. **Interception:**
   - An unauthorized person gains access to data.
   - Example: Hackers intercept sensitive data being transmitted over the internet, like credit card information.

3. **Modification:**
   - An unauthorized person not only gains access to the data but also tampers with it.
   - Example: A hacker changes the content of an email to mislead the recipient.

4. **Fabrication:**
   - An unauthorized person inserts fake or counterfeit information into the system.
   - Example: A hacker creates fake user accounts to access restricted resources.

---

#### **Common Security Attacks**
Some specific examples of attacks include:

1. **Phishing Attacks:**
   - Deceptive emails or messages tricking users into revealing sensitive information like passwords or credit card details.

2. **Malware:**
   - Malicious software such as viruses, worms, or ransomware designed to harm systems, steal data, or disrupt operations.

3. **Denial of Service (DoS) Attacks:**
   - Overwhelming a system with so many requests that it becomes unavailable to legitimate users.

---

#### **Cryptographic Attacks**
There are two main types of cryptographic attacks aimed at breaking encryption or security protocols:

1. **Passive Attacks:**
   - The attacker quietly monitors or eavesdrops on communications to steal information.
   - Examples:
     - **Release of message contents:** The attacker intercepts and reads private communications.
     - **Traffic analysis:** The attacker studies the patterns and volume of communication to gather insights.

2. **Active Attacks:**
   - The attacker modifies the data stream or creates fake communication.
   - Examples:
     - **Masquerade:** Pretending to be an authorized user.
     - **Replay:** Re-sending previously intercepted communications to trick the system.
     - **Modification of Messages:** Tampering with data during transmission.
     - **Denial of Service:** Disrupting the availability of systems.

---

#### **Requirements for Symmetric Encryption**
To securely use symmetric encryption (where the same key is used for encryption and decryption), two things are essential:
1. A strong encryption algorithm.
2. A secret key shared only between the sender and receiver.

The process can be represented as:
- **Encryption:** `Y = E(K, X)`  
  - Y: Encrypted message (ciphertext)
  - K: Secret key
  - X: Original message (plaintext)
- **Decryption:** `X = D(K, Y)`

---

#### **Cryptanalysis**
Cryptanalysis is the process of trying to break encryption to uncover the original message (plaintext) or the secret key. Different approaches include:

1. **Cryptanalytic Attack:** Using weaknesses in the encryption method.
2. **Brute-Force Attack:** Trying all possible keys until the correct one is found.

---

#### **Types of Cryptanalytic Attacks**
1. **Ciphertext-Only Attack (COA):**
   - The attacker has only the ciphertext and tries to deduce the plaintext or key.

2. **Known-Plaintext Attack (KPA):**
   - The attacker has both the plaintext and the ciphertext and uses this to find the key.

3. **Chosen-Plaintext Attack (CPA):**
   - The attacker chooses specific plaintexts to be encrypted and studies the resulting ciphertexts to gather more information about the encryption process.

4. **Chosen-Ciphertext Attack (CCA):**
   - The attacker chooses ciphertexts to be decrypted and analyzes the resulting plaintexts to gain insight into the decryption method.

---

### **Introduction to Classical Cryptography**

Classical cryptography refers to the traditional methods used for encrypting and decrypting data before the invention of modern cryptographic techniques. These techniques focused on ensuring confidentiality and protecting sensitive information. Key elements in classical cryptography include:  

1. **Encryption:**  
   - The process of converting plaintext (readable text) into ciphertext (unreadable text) using an encryption algorithm and a key.  
   - Example: Converting "HELLO" into "KHOOR" using a Caesar Cipher with a shift of 3.  

2. **Decryption:**  
   - The reverse process of turning ciphertext back into plaintext to make the message readable again.  
   - Example: Converting "KHOOR" back into "HELLO" using the same key (a shift of 3).  

3. **Key:**  
   - A special piece of information required to perform encryption and decryption.  
   - In symmetric cryptography, the same key is used for both encryption and decryption, while in asymmetric cryptography, different keys are used (public and private keys).  

4. **Cipher:**  
   - The algorithm or method used to perform encryption and decryption. It dictates how the plaintext is transformed into ciphertext and vice versa.  

Classical cryptographic techniques are fundamental to understanding how modern encryption methods evolved. These methods, though simple, were effective during their time.

---

### **Ciphering Techniques**  

Cryptography can be classified into two main types based on the key usage:

#### 1. **Symmetric Cryptography**  
   - Also known as **private-key cryptography** or **single-key cryptography**.  
   - **How it works:** The same key is shared between the sender and the receiver. Both use the same key for encryption and decryption.  
   - This method was widely used before the invention of public-key cryptography in the 1970s.  
   - Example of symmetric ciphers:
     - **Caesar Cipher** (a substitution cipher).
     - **Data Encryption Standard (DES)** (a modern symmetric cipher).

#### 2. **Asymmetric Cryptography**  
   - Also known as **public-key cryptography**.  
   - **How it works:** Two keys are used: a public key and a private key.  
     - The **public key** is shared with everyone and is used for encryption.  
     - The **private key** is kept secret by the owner and is used for decryption.  
   - Example of asymmetric ciphers:
     - **RSA (Rivest-Shamir-Adleman Algorithm)**.
     - **ECC (Elliptic Curve Cryptography)**.

---

### **Types of Ciphers**

There are two primary types of ciphers, based on how the plaintext is transformed:

#### 1. **Substitution Ciphers**  
   - In substitution ciphers, each letter or symbol in the plaintext is replaced with another letter or symbol according to a specific rule or key.  
   - Examples of substitution ciphers include:
     - **Caesar Cipher**
     - **Monoalphabetic Cipher**
     - **Polyalphabetic Ciphers** (e.g., Vigenère Cipher)
     - **Playfair Cipher**
     - **Hill Cipher**

#### 2. **Transposition Ciphers**  
   - In transposition ciphers, the positions of the letters in the plaintext are rearranged (permuted) to form the ciphertext.  
   - Unlike substitution ciphers, the letters themselves remain unchanged.  
   - Examples include:
     - **Rail Fence Cipher**
     - **Row-Column Transposition Cipher**

---

### **Substitution Ciphers in Detail**

#### **Caesar Cipher**
- One of the simplest and oldest substitution ciphers.  
- Invented by Julius Caesar for secure communication during military campaigns.  
- **How it works:** Each letter in the plaintext is replaced by a letter that is a fixed number of positions down the alphabet.  
- **Example with a shift of 3:**
  - Plaintext: **meet me after the toga party**  
  - Ciphertext: **PHHW PH DIWHU WKH WRJD SDUWB**  

##### **Mathematical Representation:**
1. Encryption:  
   `C = (P + K) mod 26`  
   - `C` is the ciphertext letter.  
   - `P` is the plaintext letter’s position in the alphabet (0-25).  
   - `K` is the shift key.  

2. Decryption:  
   `P = (C - K) mod 26`  
   - The same key (`K`) is used to revert the ciphertext back to plaintext.

**Example:**
- Plaintext: **JAVATPOINT**  
- Encryption (Shift = 3):  
  Ciphertext: **MDYDWSRLQW**

**Weakness of Caesar Cipher:**
- **Brute Force Attack:** Since there are only 26 possible shifts, an attacker can try all shifts to decode the message.  
- Example:
  - Ciphertext: **GCUA VQ DTGCM**  
  - By trying all 26 shifts, the plaintext can be easily recovered.

---

#### **Monoalphabetic Cipher**
- Instead of a simple shift, letters are shuffled randomly to create the key.  
- Each plaintext letter maps to a unique ciphertext letter.  
- Example Key:  
  Plain: **abcdefghijklmnopqrstuvwxyz**  
  Cipher: **DKVQFIBJWPESCXHTMYAUOLRGZN**  

**Example:**
- Plaintext: **if we wish to replace letters**  
- Ciphertext: **WIRFRWAJUHYFTSDVFSFUUFYA**

**Challenge:**  
- Though more secure than Caesar Cipher, monoalphabetic ciphers can still be broken using **frequency analysis**, as the same plaintext letter always maps to the same ciphertext letter.

---

#### **Vigenère Cipher**
- A **polyalphabetic substitution cipher** that uses multiple Caesar Ciphers with different shift values.  
- A **keyword** determines the shift for each letter in the plaintext.

**Steps to Encrypt:**
1. Write the plaintext.  
2. Repeat the keyword above the plaintext until it matches the plaintext’s length.  
3. Each letter in the plaintext is shifted based on the corresponding keyword letter.

**Mathematical Representation:**  
1. Encryption: `C = (P + K) mod 26`  
2. Decryption: `P = (C - K) mod 26`  

**Example:**
- Keyword: **DECEPTIVE**  
- Plaintext: **we are discovered save yourself**  
- Ciphertext: **ZICVTWQNGRZGVTWAVZHCQYGLMGJ**

**Strength:**  
- Harder to break than monoalphabetic ciphers as the same letter in the plaintext can be encrypted differently depending on its position.

---

#### **Playfair Cipher**
- Invented by Charles Wheatstone in 1854 but named after Baron Playfair.  
- Encrypts pairs of letters (digrams) instead of single letters, making it more secure.  

**Key Matrix:**
1. A 5x5 grid of letters is created using a keyword (e.g., **MONARCHY**).  
2. Duplicate letters are removed, and **I** and **J** are treated as the same.  

Example Matrix:  
```
M O N A R  
H Y B F G  
I/J P Q S T  
U V W X Z  
```

**Encryption Steps:**
1. Divide the plaintext into pairs of letters (e.g., **attack** → **at ta ck**).  
2. Follow these rules:
   - If both letters are in the same row, shift them to the right.  
   - If both are in the same column, shift them downward.  
   - Otherwise, form a rectangle and swap the corners.

**Example:**
- Plaintext: **attack**  
- Ciphertext: **rs sr de**

**Strength:**  
- Stronger than monoalphabetic ciphers but still vulnerable to analysis with enough ciphertext.

---

### **Transposition Ciphers in Detail**

#### **Rail Fence Cipher**
- A simple transposition cipher where the plaintext is written diagonally across multiple rows and then read row by row.  

**Example:**
- Plaintext: **meet me after the toga party**  
- Write diagonally in 2 rows:  
  ```
  m e m a t r h t g p r y  
  e t e f e t e o a a t
  ```
- Ciphertext: **MEMATRHTGPRYETEFETEOAAT**

---

#### **Row Transposition Cipher**
- The plaintext is written in rows over a set number of columns, then the columns are rearranged based on a key.

**Example:**
- Key: **4312567**  
- Plaintext:  
  ```
  a t t a c k p  
  o s t p o n e  
  d u n t i l t  
  w o a m x y z  
  ```
- Ciphertext: **TTNAAPTMTSUOAODWCOIXKNLYPETZ**

--- 
