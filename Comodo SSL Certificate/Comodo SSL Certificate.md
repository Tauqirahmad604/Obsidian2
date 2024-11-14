Important Concepts to understand in a SSL certificate

# Chain of Trust

The "chain of trust" is a fundamental concept in the context of digital certificates, particularly SSL/TLS certificates used to secure websites and online communications. It refers to the hierarchical structure of trust established by Certificate Authorities (CAs) and their certificates. Here’s how it works:

### Key Concepts in Chain of Trust:

1. **Certificate Authorities (CAs)**:
    
    - CAs are trusted entities that issue digital certificates.
    - They validate the identity of organizations or individuals (like website  owners) before issuing certificates.

2. **Certificates**:
    
    - Certificates are electronic documents that bind a public key to an identity (e.g., a domain name).
    - They include information such as the domain name, the public key, validity period, and the digital signature of the issuing CA.
    
3. **Root Certificates**:
    
    - Root certificates are the top-level certificates in the CA hierarchy.
    - They are self-signed certificates that are inherently trusted by web browsers and operating systems.

4. **Intermediate Certificates**:

    - Intermediate certificates are issued by CAs and are used to sign other certificates, including SSL/TLS certificates issued to websites.
    - They help create a chain of trust between the root certificate and the SSL/TLS certificate presented by a website.




==**Comodo SSL Certificate usually contains given below files.**==

1. **Choosing the Right Files to Install.txt**
2. **PRIVATE KEY INFO !.txt**
3. **PKCS7 file** 
4. **Plain Text Files**
5. **CER - CRT Files**

# 1. **Choosing the Right Files to Install.txt**

This text file guides you on which files to install and how to install them. It contains important instructions. It have all the installation instructions related to all the files present in the certificate.

# 2. **PRIVATE KEY INFO !.txt**

This is a text file that contains information related to the private key. It might include instructions or details to help you handle the private key.

# 3. **PKCS7 File**

This file should be used if your server requires that you upload a PKCS7 or .p7b file format for installation. Common server types that require this kind of file are Azure and TomCat.

**How to generate the PKCS#7 File?**

Use the `openssl crl2pkcs7` command to generate the PKCS#7 file. Since you are working with multiple intermediate certificates, you'll include all relevant `.crt` files in the command:

```
openssl crl2pkcs7 -nocrl -certfile STAR_dirabgolf_com.crt -certfile SectigoRSADomainValidationSecureServerCA.crt -certfile USERTrustRSAAAACA.crt -certfile AAACertificateServices.crt -out your_domain.p7b
```


# 4. **CER - CRT Files**

This directory contains CER (Certificate) and CRT (Certificate) files. It includes your SSL certificate and intermediate certificates.
The files in this folder are .CER files. If you need .CRT files, ==simply use a file explorer and manually change the file extension from .CER to .CRT and you'll be all set.==

The files it contains are given below

1. **AAACertificateServices.crt**

    This is likely an intermediate certificate provided by AAA Certificate Services. Intermediate certificates like this one help establish a chain of trust from your SSL certificate (in this case, STAR_dirabgolf_com.crt) to a trusted root certificate authority.


2. **STAR_dirabgolf_com.crt**

    This is your primary SSL certificate for the domain `dirabgolf.com`. It's the certificate that is issued specifically for your domain.


3. **SectigoRSADomainValidationSecureServerCA.crt**

    This is another intermediate certificate provided by Sectigo (formerly Comodo). It's part of the chain of trust necessary for validating your primary SSL certificate.

 4. **USERTrustRSAAAACA.crt**

    This intermediate certificate is provided by USERTrust and is also part of the chain of trust.

# 5. **Plain Text Files**

These files should be used if your server or hosting provider gives you a form to copy/paste your certificates into. Common hosting providers and servers that require these kinds of files are cPanel, GoDaddy, HostGator, and WHM.


"All the certificates located in the **CER - CRT Files** directory are also available as `.txt` files, which can be conveniently copied and pasted onto the desired server."

**i.** AAACertificateServices.txt 
**ii.** STAR_dirabgolf_com.txt 
**iii.** SectigoRSADomainValidationSecureServerCA.txt
**iv.** USERTrustRSAAAACA.txt



