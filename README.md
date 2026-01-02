From scratch (make sure Bash & Git are up to date first&mdash;looking at you macOS defaults 🙄):

- Go $HOME: `cd ~`
- Clone repo:
  - HTTPS: `git clone --bare https://github.com/CodeCiepol/dotfiles.git $HOME/.cfg`
  - SSH: `git clone --bare git@github.com:CodeCiepol/dotfiles.git $HOME/.cfg`
- Add `cfg` alias: `alias cfg='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'`
- Make backup directory: `mkdir -p .cfg-backup`
- Checkout dotfiles: `cfg checkout`
    - If conflicts: `cfg checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | xargs -I{} mv {} .cfg-backup/{}`
    - Re-checkout: `cfg checkout`
- Don't show untracked: `cfg config status.showUntrackedFiles no`
- Update submodules: `cfg submodule update --init --recursive`

## `ack`nowledgements

Tooling and configuration inspired by:

- https://github.com/Pinjasaur/dotfiles


## License
[MIT](https://pinjasaur.mit-license.org/2017).
