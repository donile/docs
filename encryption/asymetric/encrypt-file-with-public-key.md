# Encrypt File with Public Key

**Command**

`openssl pkeyutl`

Encrypts file with public key.

**Options**

`-encrypt` specifies the user wants to encrypt a file

`-in <plaintext.file>` specifies the file named `<plaintext.file>` should be encrypted

`-out <plaintext.file.encrypted>` specifies encrypted data should be written to a file named `<plaintext.file.encrypted>`

`-inkey <public.key>` specifies the file name of the public key that should be used to encrypt the plaintext file

`-pubin` specifies the public key and not the private key is being used to encrypt the data

`-keyform PEM | DER` specifies the encoding format of the `<public.key>` provided to the `openssl` CLI

The following example instructs `openssl` to:
* Encrypt a file
* Encrypt data in the file named `plaintext.file`
* Write encrypted data to `plaintext.file.encrypted`
* Use a public key to perform encryption (default is private key encryption)
* The public key is PEM encoded
* Use the public key in the file `public.key` to perform encryption

`openssl pkeyutl -encrypt -in plaintext.file -out plaintext.file.encrypted -pubin -keyform PEM -inkey public.key`