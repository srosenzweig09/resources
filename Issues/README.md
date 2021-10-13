# Problems and Solutions

This page documents issues that I've encountered and how I solved them. (I often will recall that I faced a problem and that I DID solve it... but I can't remember how!)

## Table of Contents

- [Problems and Solutions](#problems-and-solutions)
  - [Table of Contents](#table-of-contents)
  - [GRID](#grid)
    - [Certificate Not Recognized in Safari](#certificate-not-recognized-in-safari)

## GRID

### Certificate Not Recognized in Safari

**I downloaded the certificate and it shows up in Keychain Access under Certificates, but does not work in Safari.** The certificate itself does not require a password, but Safari does not recognize the certificate unless it is password-protected. I downloaded a new certificate for which I supplied a password, and Keychain Access automatically recognized it in My Certificates, which is where it needs to be, I think, to be accessed by Safari. (You can also check the Trust setting on the certificate and you may need to manually Trust the certificate through Keychain Access.)