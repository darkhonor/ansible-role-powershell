# Ansible Role: PowerShell

Installs the [PowerShell](https://github.com/PowerShell/PowerShell) application,
including support for an airgap environment.

## Requirements

None

## Role Variables

You can modify any of the following variables as you wish in the role's `defaults/main.yml`:

* `airgap`: Boolean if the target is in an airgap'd environment (Default: `false`)
* `microsoft_rpm_repo_url`: Full URL to the Microsoft RPM repository (Default: <https://packages.microsoft.com/rhel/$releasever/prod/>)
* `microsoft_gpg_key_url`: Full URL to the Microsoft RPM GPG Key (Default: <https://packages.microsoft.com/rhel/$releasever/prod/repodata/repomd.xml.key>)
* `trust_repository_certs`: Boolean if the source repository's certificate is trusted by the target (Default: `true`)

## Dependencies

None

## Example Playbook

Here is an example playbook using this role:

```yaml
- name: Configure workstations
  become: true
  become_method: sudo
  gather_facts: true
  hosts: all
  roles:
    - role: powershell
      airgap: true
      microsoft_rpm_repo_url: "{{ repo_server }}/{{ microsoft_repo_path }}"
      microsoft_gpg_key_url: "{{ repo_server }}/{{ microsoft_cert_path }}"
      trust_repository_certs: false
```

## License

MIT

## Author Information

Alex Ackerman, GitHub @darkhonor
