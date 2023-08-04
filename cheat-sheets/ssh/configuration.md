`~/.ssh/config` file example

```
Host github.com
  User juliuszlioba
  Hostname github.com
  IdentitiesOnly yes
  IdentityFile ~/.ssh/id_github
```


## comands to remember

List current Identities:

```bash
ssh-add -L
```

Delete Identities:

```bash
# delete all
ssh-add -D
```