# GPG

## Key generation

Create a master key and three subkeys

### Master key

Init key master key generation process:

`gpg --expert --full-gen-key`

Select `(8) RSA (set your own capabilities)`

Make the master key's only attribute `C` (Certify)

Toggle (S) **sign** and (E) **encrypt**, so that the only availble attribute is: **authenticate**

`Current allowed actions: Certify`

Exit, by pressing `q`

Set key size to `4096`.

Set key duration to a relatively long period, like 2 or 3 years:

`3y`

Add your identity and a **strong** passphrase.

Note that a revocation certificate should be created as well in the folder: `$GNUPGHOME\openpgp-revocs.d`


### Subkeys

List the available keys. The newly created master key should appear:

`gpg --list-keys`

Export or copy the key id (the value after rsa4096: eg. `rsa4096/1A8132B1`)

`export KEYID=1A8132B1`

Add the three subkeys, by adding a key for each attribute (sign, encrypt, authenticate).

`gpg --expert --edit-key $KEYID`

type `addkey`

select `(8) RSA (set your own capabilities)`

select `(S) Toggle the sign capability`

exit by typing `q`

Select `4096` as key size

Select a much shorter period for the sub-keys duration: between **6 months and one year**.

Repeat the process **two more times** for the remaining capabilities: encrypt and authenticate.

Save by typing `save` and exit with `quit`.

The master key and sub-keys are now created.

### verify

`gpg --list-keys`

```
-----------------------------------------------
pub   rsa4096 2019-10-27 [C] [expires: 2023-10-26]
      C2AAA1A1111111A2B216DD3DA6A96E41109BC83C
uid           [ultimate] John Doe <johndoe@secret.com>
sub   rsa4096 2019-10-27 [S] [expires: 2020-04-24]
sub   rsa4096 2019-10-27 [E] [expires: 2020-04-24]
sub   rsa4096 2019-10-27 [A] [expires: 2020-04-24]
```

### export keys

```
# export public key
gpg --export --armor $KEYID > $KEYID.pub.asc
# export private key
gpg --export-secret-keys --armor $KEYID > $KEYID.priv.asc
# export private subkeys
gpg --export-secret-subkeys --armor $KEYID > $KEYID.sub_priv.asc
```

### delete master private key

`gpg --delete-secret-key $KEYID`


### import private subkeys

`gpg --import $KEYID.sub_priv.asc


### verify

`gpg --list-secret-keys`


```
-----------------------------------------------
sec#  rsa4096 2019-10-27 [C] [expires: 2023-10-26]
      C2AAA1A1111111A2B216DD3DA6A96E41109BC83C
uid           [ultimate] John Doe <johndoe@secret.com>
ssb   rsa4096 2019-10-27 [S] [expires: 2020-04-24]
ssb   rsa4096 2019-10-27 [E] [expires: 2020-04-24]
ssb   rsa4096 2019-10-27 [A] [expires: 2020-04-24]
```

The small # before sec indicates that the secret key of the master key no longer exists, it’s a stub instead.

### resources

https://blog.eleven-labs.com/en/openpgp-almost-perfect-key-pair-part-1/

https://gitlab.com/gitlab-com/runbooks/blob/master/howto/yubikey.md