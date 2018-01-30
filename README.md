# SSHD Git

Minimal Alpine Linux Docker container with `sshd` exposed and `git` installed.

## Environment Options

* `AUTHORIZED_KEY`

## Usage Example

```
docker run -d -p 2222:22 -e AUTHORIZED_KEY="$(cat id_rsa.pub)" cwhimura/sshd-git
ssh-keygen -R [127.0.0.1]:2222
ssh -oStrictHostKeyChecking=no -i $(pwd)/id_rsa git@127.0.0.1 -p 2222 git init --bare sample.git
export GIT_SSH_COMMAND="ssh -oStrictHostKeyChecking=no -i $(pwd)/id_rsa"
git clone ssh://git@127.0.0.1:2222/~/sample.git
cd sample
echo Hello > README.md
git add .
git commit -m "initial"
git push
```

## Links

* [panubo/docker-sshd](https://github.com/panubo/docker-sshd)
