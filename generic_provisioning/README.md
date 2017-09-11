## About

A provisioning script for Debian. Includes:

* Running package updates and upgrades
* Installing a number of default packages
* Setting up iptables with a default inbound ruleset only allowing port 22
* Creating a non-root user and adding their public key
* Setting up dotfiles for the new user

## How to use

* Copy `hosts.template` to `hosts` and add the managed machines to the `provisioning` group.
* Copy `./group_vars/provisioning/vault.example` to `./group_vars/provisioning/vault`
* Replace `[password hash here]` in `vault` with a non-root user password hash
    * Run `mkpasswd --method=sha-512` to generate the correct hash
* Encrypt `vault` via `ansible-vault encrypt vault` and set a password
* Run the playbook via `ansible-playbook generic_provisioning.yml -i hosts --ask-vault-pass`
