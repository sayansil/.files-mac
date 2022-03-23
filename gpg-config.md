```shell
brew install gpg
brew install pinentry-mac
```

```shell
gpg --version
```

```shell
echo "pinentry-program $(which pinentry-mac)" >> ~/.gnupg/gpg-agent.conf
gpgconf --kill gpg-agent
```

```shell
gpg --list-secret-keys --keyid-format=long
```

`Shell Output`

```shell
> /Users/sayansil/.gnupg/pubring.kbx
> sec   rsa4096/<gpg-key-id> 2000-01-01 [SC] [expires: 2001-01-01]
>       <alphabetic-string>
> uid                 [something] Sayan Sil <email@domain.com>
```

```shell
gpg --armor --export <gpg-key-id>
```

`Shell Output`

```shell

> -----BEGIN PGP PUBLIC KEY BLOCK-----
>
> <HUGE BLOCK OF ALPHANUMERIC STRING>
>
> -----END PGP PUBLIC KEY BLOCK-----
```

**Add `<HUGE BLOCK OF ALPHANUMERIC STRING>` to GitHub if not already added.**

```shell
git config --global user.signingkey <gpg-key-id>
git config --global commit.gpgsign true
```
