# Decrypt File with Private Key

**Command**

`openssl pkeyutl`

**Options**

`-decrypt` specifies the user wants to decrypt a file

`-in <plaintext.file.encrypted>` specifies the data in the file named `<plaintext.file.encrypted>` should be decrypted

`-out <plaintext.file.decrypted>` specifies the decrypted data should be written to a file named `<plaintext.file.decrypted>`

`-inkey <private.key>` specifies the name of the file where the private key is located

`-keyform PEM | DER` specifies the encoding format of the private key

`-passin pass:<password>` specifies the password required to decrypt the private key

The following example instructs `openssl` to:
* Decrypt data
* Read encrypted data from the file `plainext.file.encrypted`
* Write decrypted data to the file `plainext.file.decrypted`
* Use the private key in file `private.key`
* The private key is PEM encoded
* Use `super-secret-password` to decrypt private key

`openssl pkeyutl -decrypt -in plainext.file.encrypted -out plainext.file.decrypted -inkey private.key -keyform PEM -passin pass:super-secret-password`