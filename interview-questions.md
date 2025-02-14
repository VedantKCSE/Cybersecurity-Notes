# Interview Questions

### **Interview Questions & Answers on Broken Access Control**

💡 **Basic Questions:**

1. **What is Broken Access Control?**
   * "Broken Access Control occurs when an application fails to enforce **restrictions** on what users can do, leading to unauthorized data access or modification."
2. **How does Broken Access Control differ from Authentication issues?**
   * "Authentication verifies **who you are**, while Access Control enforces **what you can do** after authentication."
3. **What are the common causes of Broken Access Control?**
   * Misconfigured access control policies
   * Relying on client-side access controls
   * Not enforcing role-based access properly
   * Insecure APIs with missing access checks

***

💡 **Advanced Questions (Scenario-Based):** 4. **How would you prevent IDOR vulnerabilities?**

* "By implementing **server-side authorization checks** before returning sensitive data and using **UUIDs** instead of numeric identifiers."

5. **What security risks arise from improper CORS configurations?**
   * "A misconfigured CORS policy can allow **unauthorized websites** to make API requests on behalf of a user, leading to **data theft or unauthorized actions**."
6. **Can JWTs lead to Broken Access Control?**
   * "Yes, if JWTs are not properly validated, an attacker can **modify tokens**, elevate privileges, or reuse expired tokens."

### **Interview Questions & Answers on Cryptographic Failures**

💡 **Basic Questions:**

1. **What is Cryptographic Failure?**
   * "It refers to vulnerabilities arising from improper encryption, weak cryptographic algorithms, or insecure key management, leading to sensitive data exposure."
2. **What are the best practices for securely storing passwords?**
   * "Use **bcrypt, Argon2, scrypt, or PBKDF2** with a salt and a high iteration count."
3. **Why is MD5 or SHA1 no longer recommended?**
   * "They are **fast and predictable**, making them vulnerable to **collision attacks** and **rainbow table attacks**."

***

💡 **Advanced Questions (Scenario-Based):** 4. **How can you prevent MITM attacks on a login page?**

* "Use **TLS 1.3**, enforce **HSTS**, and implement **certificate pinning**."

5. **How do you securely generate cryptographic keys?**
   * "Use a **CSPRNG** like `secrets.token_bytes()` in Python or `crypto.randomBytes()` in Node.js."
6. **What is Forward Secrecy, and why is it important?**
   * "Forward Secrecy ensures that **past communication remains secure** even if future keys are compromised. It prevents attackers from decrypting old messages."

