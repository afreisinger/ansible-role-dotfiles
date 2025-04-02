# Ansible Role: Dotfiles

[![CI](https://github.com/afreisinger/ansible-role-dotfiles/actions/workflows/ci.yml/badge.svg)](https://github.com/afreisinger/ansible-role-dotfiles/actions/workflows/ci.yml)

Installs a set of dotfiles from a given Git repository. By default, it will install my (afreisinger's) [dotfiles](https://github.com/afreisinger/dotfiles), but you can use any set of dotfiles you'd like, as long as they follow a conventional format.

## Requirements

Requires `git` on the managed machine (you can easily install it with `afreisinger.git` if required).

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    dotfiles_repo: "https://github.com/afreisinger/dotfiles.git"
    dotfiles_repo_version: main

The git repository and branch/tag/commit hash to use for retrieving dotfiles. Dotfiles should generally be laid out within the root directory of the repository.

    dotfiles_repo_accept_hostkey: false

Add the hostkey for the repo url if not already added. If ssh_opts contains "-o StrictHostKeyChecking=no", this parameter is ignored.

    dotfiles_repo_local_destination: "~/dotfiles"

The local path where the `dotfiles_repo` will be cloned.

    dotfiles_home: "~"

The home directory where dotfiles will be linked. Generally, the default should work, but in some circumstances, or when running the role as sudo on behalf of another user, you may want to specify the full path.

    dotfiles_files:
      - .zshrc
      - .gitignore
      - .inputrc
      - .vimrc

Which files from the dotfiles repository should be linked to the `dotfiles_home`.

## Dependencies

None

## Example Playbook

    - hosts: localhost
      roles:
        - { role: afreisinger.dotfiles }

## License

MIT / BSD

## Author Information

Created in 2025 by [Adrian Freisinger](https://afreisinger.gitlab.io/), inspired by [Ansible for DevOps](https://www.ansiblefordevops.com/) by [Jeff Geerling](https://www.jeffgeerling.com/).
