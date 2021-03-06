# Ansible Role: Dotfiles

[![CI](https://img.shields.io/gitlab/pipeline/rjh/ansible-role-dotfiles/main?gitlab_url=https%3A%2F%2Fgitlab.rickhenry.uk)](https://gitlab.rickhenry.uk/rjh/ansible-role-dotfiles/-/commits/main)
[![GitHub tag (latest SemVer)](https://img.shields.io/github/v/tag/rjhenry/ansible-role-dotfiles?sort=semver)]()
[![GitHub tag (latest by date)](https://img.shields.io/github/v/tag/rjhenry/ansible-role-dotfiles)]()

[![Ansible Role](https://img.shields.io/ansible/role/56009)](https://galaxy.ansible.com/rjhenry/dotfiles) 
[![Ansible Role Downloads](https://img.shields.io/ansible/role/d/56009)](https://galaxy.ansible.com/rjhenry/dotfiles) 
[![Ansible Quality Score](https://img.shields.io/ansible/quality/56009)](https://galaxy.ansible.com/rjhenry/dotfiles)

Installs a set of dotfiles from a given Git repository. This is heavily inspired
by [Jeff Geerling's repo](https://github.com/geerlingguy/dotfiles) of the same
name.

## Requirements

Requires `git` on the managed machine, though note that this will happily
install it for you.

## Role Variables

Available variables are listed below, along with default values (see
`defaults/main.yml`): ```yaml dotfiles_repository_url:
"ssh://git@gitlab.rickhenry.uk/rjh/dotfiles.git" dotfiles_repo_reference: main
```

The git repository URL and branch/tag/commit hash to use for retrieving
dotfiles. Dotfiles should generally be laid out within the root directory of the
repository. Note that - if you're using this role and are not, in fact, Rick,
you'll need to change this repository as this repo is locked down.

```yaml dotfiles_repo_accept_hostkey: false ```

Add the hostkey for the repo url if not already added. If `ssh_opts` contains
"-o StrictHostKeyChecking=no", this parameter is ignored.

```yaml dotfiles_repo_local_destination: "~/.dotfiles" ```

The local path where the dotfiles repo will be cloned.

```yaml dotfiles_home: "~" ```

The home directory where dotfiles will be linked. Generally, the default should
work, but in some circumstances, or when running the role as sudo on behalf of
another user, you may want to specify the full path.

```yaml dotfiles_files:
  - .bashrc
  - .gitconfig ```

Which files from the dotfiles repository should be linked to the
`dotfiles_home`.

## Dependencies

None

## Example Playbook

    - hosts: localhost roles:
	- { role: rjhenry.dotfiles }

## Contributing
If you feel the need to contribute to this role, please create
[issues](https://gitlab.rickhenry.uk/rjh/ansible-role-dotfiles/-/issues) on the
project. If you have patches you'd like to submit, create a PR on GitHub, from
where I'll pull those changes to GitLab.

