# OSAA Infrastructure

## Ansible playbook for Open Space Aarhus Infrastructure

As an effort to document the infrastructure at Open Space Aarhus, we have started to put it into ansible playbooks

Currently we have a bootstrapping playbook and a main playbook that currently only handles user creation

Roles:
- users
- _more to come_

The users role takes input from a _users.yml_ file, this file contains an array of user objects, formated as following

```yaml
users:
- username: _the local user on the host_
  keyUrl: _github or gitlab url for the ssh public keys_
  passwordHash: _password hash for the password on the host_
```

Creating the hash for your password can be done with a simple command

```bash
mkpasswd --method=SHA-512
```

You will be asked for your password, the output is the hashed value that you need to put into the users.yml file.


This playbook creates a ansible user on the host. You will find private and public keys associated with the ansible user in the folder _certificates_
*NOTE: the private key part is encrypted with ccrypt and the decryptionkey can be found in our bitwarden.

_reach out to the infrastructure people to get help with this_

## Running the playbook

You need to decrypt the private key before you can run the _bootstrap_ playbook.

To decrypt use the following command
```bash
ccrypt -d certificates/bootstrap_ed25519.cpt
```

this will result in the cpt extention being stripped and the content is decrypted.

When you are done re-encrypt it using

```bash
ccrypt -e certificates/bootstrap_ed25519
```

if you forget the privatekey will not be uploaded to github, as its specified in the _.gitignore_ file, this is by design.

if you are missing ccrypt you can install using this command
```bash
sudo apt install ccrypt
```

Once you have handled the decryption you can run the playbooks

### Bootstrapping a new host

```bash
ansible-playbook bootstrap.yml -i hosts -K -k
```

You will be asked for both the ssh password and the sudo password

_the default user is **osaa**_

Once the host is bootstrapped, its ready to actually get provisioned by ansible.

### Provisioning the host

```bash
ansible-playbook main.yml -i hosts -K
```

This command assumes that the ansible user has been created by the bootstrapping, this wont work unless its bootstrapped first.

