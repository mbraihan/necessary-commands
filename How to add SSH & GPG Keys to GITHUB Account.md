How to add SSH & GPG Keys to GITHUB Account

# SSH
check if there is one
``` sh
ssh-add -l
```
if not
``` sh
$ ssh-keygen -t rsa -b 4096 -C "email"
```
enter a passphrase

then
``` sh
cat .ssh/id_rsa.pub
```
copy it

then

go to github.com --> settings --> SSH and GPG keys

new SSH key

add a title and paste key

then click add SSH key

if already a key exists, generate new one then

``` shell
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/{PrivatekeyName}
```





# GPG

[Generating a new GPG Key and setting it](https://docs.github.com/en/github/authenticating-to-github/managing-commit-signature-verification/generating-a-new-gpg-key)
