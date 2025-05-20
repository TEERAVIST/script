# scripts



before useing this script need to gen key private , pub.

```bash
ssh-keygen -t ed25519 -C "<email>" -f ~/.ssh/id_ed25519_personal
```

then login github and https://github.com/settings/keys "new ssh key" and copy your 

```bash
~/.ssh/id_ed25519_personal.pub
``` 
and paste to ssh key

edit ~/.ssh/config file looklike this
```config
# Personal GitHub <user>
Host github-<user>
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_personal
  IdentitiesOnly yes
```

checking ssh is it work for now?
```bash
ssh -T git@github-<user>
```

next, add set-url remote (origin or whatever) to ssh
```bash
git remote set-url origin git@github-<user>:<repo-name>.git
```

convert script to elf
```bash
shc -f git-push-helper
```
change name of elf file to push
```bash
mv git-push-helper push
```

make push command for global command (user)
```bash
sudo mv push /usr/local/bin

```
