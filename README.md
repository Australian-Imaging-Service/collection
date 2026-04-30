# Ansible Collection - ais.core

The following instructions use **pipx** for Ansible, related application and requirements installation.
If you are using a different method you can use the links provided to help.

## Using this collection

### Installing the collection

```bash
ansible-galaxy collection install --force "git+https://github.com/Australian-Imaging-Service/collection.git"

# Install any python dependancies.
pipx runpip ansible install -r $HOME/.ansible/collections/ansible_collections/ais/core/requirements.txt
```

### Installing ansible

Ref. [Installing Ansible](https://docs.ansible.com/projects/ansible/latest/installation_guide/intro_installation.html#installing-and-upgrading-ansible-with-pipx)

Example Ansible setup using pipx on a MacOS or Linux host.

```bash
# Install Ansible and related development packages
pipx install --include-deps ansible
pipx inject --include-apps ansible ansible-lint
pipx inject --include-apps ansible antsibull-changelog

# Install all ansible collection python dependancies
# NB. You may wish to be more selective. This can take a while.
COLLECTIONS="$(ansible-galaxy collection list --format=json 2>/dev/null |jq -r 'keys[]')"
find $(echo "$COLLECTIONS" |xargs) -name 'requirements.txt' -type f -exec \
  pipx runpip ansible install --upgrade -r "{}" \;
```

Upgrade using pipx.

```bash
pipx upgrade --include-injected ansible
```
