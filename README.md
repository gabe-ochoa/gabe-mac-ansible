# Jayson's Mac Ansible Playbook

[![Build Status](https://travis-ci.org/jayson/jayson-mac-ansible.svg?branch=master)](https://travis-ci.org/jayson/jayson-mac-ansible)

This playbook installs all my homebrew apps and configurations for me instead
of manually configuring every new laptop I get.

*See Also*
  - Forked from [mac-dev-playbook](https://github.com/geerlingguy/mac-dev-playbook) by [Jeff Geerling](http://www.jeffgeerling.com/)

## Installation

  1. Ensure Apple's command line tools are installed (`xcode-select --install` to launch the installer).
  2. [Install Ansible](http://docs.ansible.com/intro_installation.html).
  3. Clone this repository to your local drive.
  4. Run `$ ansible-galaxy install -r requirements.yml` inside this directory to install required Ansible roles.
  5. Run `ansible-playbook main.yml -i inventory -K` inside this directory. Enter your account password when prompted.

> Note: If some Homebrew commands fail, you might need to agree to Xcode's license or fix some other Brew issue. Run `brew doctor` to see if this is the case.

### Running a specific set of tagged tasks

You can filter which part of the provisioning process to run by specifying a set of tags using `ansible-playbook`'s `--tags` flag. The tags available are `dotfiles`, `homebrew`, `mas`, `extra-packages` and `osx`.

    ansible-playbook main.yml -i inventory -K --tags "dotfiles,homebrew"

My [dotfiles](https://github.com/gabe-ochoa/dotfiles) are also installed into the current user's home directory. You can disable dotfiles management by setting `configure_dotfiles: no` in your configuration.

## Future additions

### Configuration to be added:

  - [ ] Change shell for user to zsh
  - [ ] Merge dot files from multiple computers
  - [ ] iTerm settings and config into dotfiles and move it to correct location
  - [ ] Keybindings for vscode, put into dotfiles and hardlink to vscode bindings in ~/Library/application suport/code/.../stuff/stuff
  - [ ] Make hardlinks to dotfile repo
    - Need to use hln for this on mac because Apple crippled `ln`
    - brew install hardlink-osx
  - [ ] git username and email setup
  - [ ] clone down prezto from forked repo
  - [ ] pull down fork of pure submodule for custom prompts
    - replace submodule origin and pull?
  - [ ] install fonts 
  - Installing licenses for apps

## Testing the Playbook

  You can follow the instructions here to create a [Mac OS X VirtualBox VM](https://github.com/geerlingguy/mac-osx-virtualbox-vm) for testing your playbook changes

This project is [continuously tested on Travis CI's macOS infrastructure](https://travis-ci.org/jayson/jayson-mac-ansible).

## Author

  [Jayon Paul](http://www.jaysonmpaul.com/), 2017 (originally forked from [mac-dev-playbook](https://github.com/geerlingguy/mac-dev-playbook) by [Jeff Geerling](http://www.jeffgeerling.com/))
