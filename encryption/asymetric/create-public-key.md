## Create Public Key

**Command**

`openssl pkey`

Actually extracts a public key from the keypair.

**Options**

`-in <private.key.file>` specifies the private key file from which the public key will be extracted

`-pubout` specifies the output should be a public key

`-out <public.key.file>` specifies the name of the file where the public key will be written

-`passin pass:<password>` specifies the password of the private key

The following example instructs `openssl` to:

* Use the private key in the file `private.key.pem`
* Use the password `super-secret-password` to decrypt the private key
* Produce a public key
* Save the public key in the file `public.key.pem`

`openssl pkey -in private.key.pem -passin pass:super-secret-password -pubout -out public.key.pem`