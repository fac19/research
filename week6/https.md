# HTTPS

![security](https://media.giphy.com/media/HDqg96dEcf49W/giphy.gif)

---

## Why do we want security anyway?

![secret](https://media.giphy.com/media/3oFyCYNrra8qo1Cv8Q/giphy.gif)

---

### Privacy
![private](https://media.giphy.com/media/3otPoyXM2G9VRgROnK/giphy.gif)

---

### Integrity 

![piggy](https://metro.co.uk/wp-content/uploads/2016/03/george.gif)

---

### Identification

![id](https://media.giphy.com/media/RPrmB9N6HsMCY/giphy.gif)

---

## Certificate Authority

![certifcate](https://media.giphy.com/media/3ofSBzgAwE3X3EtddK/giphy.gif)

---

- CA are third party companies that:
    - Issue certificates
    - Confirm identities of certificate owners 
    - Prove validiity of certificates.

- Root store is a database of trusted CAS. Microsoft, apple, and mozilla have their own that they pre-install for their browsers

---

## HTTPS

![safety](https://i.imgur.com/6CLXL6I.png)

---

## HTTP (no S)

![unsecure](https://i.imgur.com/hoSziHy.png)

---

## How is HTTPS different?
It's still the same conversation between a browser and server! But now it's got **T**ransport **L**ayer **S**ecurity...

---

## What is TLS?

TLS = Transport Layer Security
- Encrypts the communication between web applications and servers
- HTTPS is an implementation of TLS encryption (any site using HTTPS is employing TLS encryption)
- TLS helps protect against attacks

---

## Keys

![key](https://media.giphy.com/media/6vtfipBMkwEP6/giphy.gif)

- Symmetric vs asymmetric
- Private and public (asymmetric) keys are used to encrypt the pre-master key meaning nobody will be able to intercept it
- Pre-master key + master key (both symmetric)

---

### How does TLS work?
- Encryption: Hides data from third parties
- Authentication: Ensures parties are who they claim to be
    - Data encrypted with the public key can only be decrypted with a private key and vice versa
- Integrity: Is the data free from tampering?
    - Data is signed with a Message Authentication Code (MAC) and verifies the integrity of the data

---

### TLS Handshake

-  Before exchanging data the browser and server need to agree first on a common set of algorithms to secure the connection

![handshake](https://media.giphy.com/media/sKnQAVhutT4Zi/giphy.gif)

---

![tls handshake](https://i.imgur.com/hBitXro.png =500x)

---

## Any Questions?

![simple](https://media.giphy.com/media/H1THXNSQOooS7Ytw1E/giphy.gif)


