# BOXY

[![ansible-lint](https://github.com/stackzoo/boxy/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/stackzoo/boxy/actions/workflows/ansible-lint.yml)
<br/>

**Boxy** is a repository that we rely heavily on at *stackzoo*.
<br/>
It basically contains *vagrant* scripts (*hcl*) and *ansible* playbooks that allow our engineers to quickly provision linux VMs.
<br/>
Our members are free to follow the working method that best suits them but our advice is to always generate one (or more) VM per project/customer.

## Prerequisites
- <a href="https://www.vagrantup.com/">vagrant</a>
- <a href="https://docs.ansible.com/">ansible</a>
- <a href="https://www.virtualbox.org/">virtualbox</a>
- <a href="https://developer.hashicorp.com/vagrant/docs/plugins">vagrant plugins</a> (*vagrant-disksize*, *vagrant-vbguest*)

Note that, as of *10/03/2023*, `vagrant` and `virtualbox` are not fully supported on *macOS silicon*
and `ansible` does not run on Windows unless you are using <a href="https://learn.microsoft.com/en-us/windows/wsl/install">WSL</a>.
<br/>
Given this preamble, we at *stackzoo* strongly recommend using a linux machine for development, preferably *debian* based, such as <a href="https://ubuntu.com/">ubuntu</a>.

## Instructions
Clone this repo:
```console
git clone https://github.com/stackzoo/boxy.git
```


apply the changes that best suit your needs and then spin up the provisioning:

```console
vagrant up
```

Please note that the ansible playbook can be used to configure

## Useful Commands

*vagrant status* — Get the current status of your VM

*vangrant destroy* — Remove all traces of the virtual machine from your system

*vagrant suspend* — Stop the machine and save its current state.

*vagrant provision {vm-name}* — Manually execute ansible playbook against a VM.

*vagrant halt* — Shut down the virtual machine.

*vagrant box list* - List local vagrant box images

*vagrant box remove {vagrant-box-image-name}* - Remove local vagrant box images

*vagrant plugin list* - List local vagrant plugins