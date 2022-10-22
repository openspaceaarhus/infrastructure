# Infrastructure

This repository contains scripts and configuration for all our infrastructure.

## TODO

- [ ] Connectivity
  - [ ] Deploy VPN server
  - [ ] Configure VPN connection from Juniper firewall
- [ ] Networking
  - [ ] Configure VLANs
  - [ ] Configure static leases for node0 - node3
- [ ] Provisioning
  - [ ] Add SSH key to nodes
  - [ ] Enable passwordless sudo
- [ ] Ansible playbook `setup`
  - [ ] Disable password authentication
  - [ ] Install `dropbear-initramfs`
  - [ ] Install `kexec-tools` and configure `kboot`

## License

This project is licensed under the term of the [MIT License][file-license].

[file-license]: ./LICENSE.md