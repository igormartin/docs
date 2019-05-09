### Initial setup
`git config --global user.name "John Doe"`   
`git config --global user.email johndoe@example.com`

### Select editor
git config --global core.editor mcedit

### Global gitignore
`touch ~/.gitignore`   
`git config --global core.excludesfile '~/.gitignore'`

### Local ssh key
`git config core.sshCommand "ssh -i ~/.ssh/id_rsa_example -F /dev/null"`

### Install submodules
`git submodule update --init`

### Uninstall submodules
`git submodule deinit --all -f`
