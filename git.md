
### Global gitignore
`touch ~/.gitignore`

`git config --global core.excludesfile '~/.gitignore'`

### Local ssh key
`git config core.sshCommand "ssh -i ~/.ssh/id_rsa_example -F /dev/null"`

### Install submodules
`git submodules update --init`

### Uninstall submodules
`git submodules deinit --all -f`
