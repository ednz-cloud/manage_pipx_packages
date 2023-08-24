manage_pipx_packages
=========

A brief description of the role goes here.

Requirements
------------

None.

Role Variables
--------------
Available variables are listed below, along with default values. A sample file for the default values is available in `default/manage_pipx_packages.yml.sample` in case you need it for any `group_vars` or `host_vars` configuration.

```yaml
manage_pipx_packages_install_prereqs: true # by default, set to true
```
This variable defines if the prerequisites for the role should be installed. This should be left to true, unless you install python and pipx from another role prior to running this one.

```yaml
manage_pipx_packages_home: "/opt/pipx" # by default, set to /opt/pipx
```
This variable define where the pipx packages should be installed. By default, this is a generic path, in order to not tie the installs to a specific user.

```yaml
manage_pipx_packages_path: "/usr/local/bin" # by default, set to /usr/local/bin
```
This variable defines the path on which to make the package available. Please note that the actual installation will be done on the `manage_pipx_packages_home` path. The path given here will be simlinked to the installed package.

```yaml
manage_pipx_packages_list: # by default, set to install ansible-core
  - name: ansible-core
    version_constraint: latest
    state: present
```
This variable is a list of packages, with their name, desired version and state. `version_constraint` can be multiple constraints,separated by commas (example: `>1.10`, `>1.10,<1.15,!=1.12`,`==1.13`).
[!WARNING]
Test ?

Dependencies
------------

None.

Example Playbook
----------------

```yaml
# calling the role inside a playbook with either the default or group_vars/host_vars
- hosts: servers
  roles:
    - ednxzu.manage_pipx_packages
```

License
-------

MIT / BSD

Author Information
------------------

This role was created by Bertrand Lanson in 2023.
