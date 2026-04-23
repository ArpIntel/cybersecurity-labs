Encryption & Public Key Infrastructure (PKI)
Subject: Network Security — UTS
Tools Used: OpenSSL, Linux CLI
Topics: Symmetric Encryption, Cipher Modes, Certificate Authorities, PKI

Overview
This lab explored how encryption works in practice using OpenSSL — from basic file encryption to building a PKI chain that mirrors how real HTTPS certificates work. The goal was to get hands-on with the tools that underpin most of the security on the internet today.

What I Did
Task 1 — Encrypting Files with OpenSSL
Encrypted both a text file and an image file using two different AES cipher modes — AES-128-ECB and AES-128-CFB1 — and compared the outputs.
The key takeaway here was the difference between ECB and CFB modes. ECB encrypts each block independently, which means identical input blocks produce identical output — this makes patterns visible in the ciphertext, especially in images. CFB operates as a stream cipher where each block depends on the previous one, producing a much more randomised output. This is a well-known weakness of ECB that's easy to overlook in theory but becomes very obvious when you actually see it on an encrypted image.
Task 2 — Becoming a Certificate Authority (CA)
Generated a self-signed root CA certificate using OpenSSL. This involved creating a private key and signing the certificate ourselves — essentially what a trusted CA like DigiCert or Let's Encrypt does, but in a local environment.
Task 3 — Issuing a Certificate as a Root CA
Acting as the root CA, created and signed a certificate for the domain cybersec.com.au. This simulated the real-world process of how a domain owner requests a certificate and a CA verifies and signs it.
Task 4 — Deploying PKI for a Website
Used the issued certificate to enable HTTPS on a local web server — tying together the full PKI chain from certificate creation to deployment.

Key Takeaways

ECB mode is fundamentally insecure for anything beyond single-block data — the pattern leakage is a real vulnerability, not just a theoretical one
The PKI trust chain (root CA → intermediate CA → end-entity certificate) is what makes HTTPS trustworthy at scale
OpenSSL is incredibly powerful and is the backbone of most TLS implementations in production environments


Skills Demonstrated
OpenSSL AES Encryption Cipher Mode Analysis PKI X.509 Certificates TLS/HTTPS Linux CLI
