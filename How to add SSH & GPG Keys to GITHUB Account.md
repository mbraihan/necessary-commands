How to add SSH & GPG Keys to GITHUB Account

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
