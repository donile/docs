# Create Private Key

**Command**

`openssl genpkey`

Actually creates a keypair, not just a private key.  A keypair consists of a private and public key.

**Options**

`-out <private.key.file>` specifies the name of the file to which the key will be written

`-outform PEM | DER` specifies the encoding format of the private key file

`-pass pass:<password>` specifies the `<password>` that will be used to encrypt the private key

`-<cipher>` specifies the alogrithm used to encrypt the `<private.key.file>` with the provided password

`-algorithm <alogrithm>` specifies the asymetric algorithm to use to create the private key (keypair)

`-pkeyopt <option1:value1> ... <optionN>:<valueN>` specifies the additional options and their associated values for algorithm selected with the `-algorithm` parameter.

The following example instructs `openssl` to generate a
* `PEM` encoded 
* `RSA` private key (keypair)
* With 4096 bits
* Save the private key to a file named `private.key.pem`
* Encrypt the private key (keypair) using the AES-256 cipher 
* With the password `super-secret-password`

`openssl genpkey -outform PEM -algorithm RSA -pkeyopt rsa_keygen_bits:4096 -out private.key.pem22 -AES256 -pass pass:super-secret-password`