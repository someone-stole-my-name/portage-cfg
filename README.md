portage-cfg
=========

A role to manage a bunch of portage config files.

Role Variables
--------------

- `portage_accept_keywords`: List of keywords to accept. Example:
```yaml
portage_accept_keywords:
  - atom: app-admin/ansible
    keyword: ~amd64
```
- `portage_accept_license`: List of licenses to accept. Example:
```yaml
portage_accept_license:
  - atom: app-editors/visual-studio-code
    license: MS-vscode-EULA license
```
- `portage_unmask`: List of lines to add to `package.unmask` file.
- `portage_mask`: List of lines to add to `package.mask` file.
- `portage_sets`: List of sets to create, each set is also added to `world_sets`. Example:
```yaml
portage_sets:
  - name: fonts
    packages:
      - media-fonts/corefonts
```
- `portage_package_use`: List of uses. Each "item" creates a new file under `/etc/portage/package.use` with its name. Example:
```yaml
portage_package_use:
  - name: ansible
    uses:
      - use: dev-python/ipython -qt5
        comments:
          - This pulls a bunch of crap
```
- `portage_world`: List of packages to add to `world` file.
- `portage_make`: List of custom lines to append to `make.conf`. Example:
```yaml
portage_make:
  - name: LINGUAS
    value:
      - en
      - es
```
- `portage_ansible_managed_filename`: in case paths like `/etc/portage/package.accept_keywords` are a directory, a file with this name will be created in the corresponding path to include the requested line. [Default: `ansible_managed`]

License
-------

BSD
