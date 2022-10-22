# Infrastructure

This repository contains scripts and configuration for all our infrastructure.

## TODO

- ~~[ ] Connectivity~~
  - ~~[ ] Deploy VPN server~~
  - [ ] Configure VPN connection from Juniper firewall
- [x] Networking
  - ~~[ ] Configure VLANs~~
  - [x] Configure static leases for node0 - node3
- [x] Provisioning
  - [x] Add SSH key to nodes
  - ~~[ ] Enable passwordless sudo~~
- [x] Ansible playbook `bootstrap`
  - [ ] Disable password authentication
  - [ ] Install `dropbear-initramfs`
  - [ ] Install `kexec-tools` and configure `kboot`
- [x] Ansible playbook `main`

## License

This project is licensed under the term of the [MIT License][file-license].

[file-license]: ./LICENSE.md