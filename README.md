portage-cfg [![Molecule](https://github.com/someone-stole-my-name/portage-cfg/actions/workflows/molecule.yml/badge.svg)](https://github.com/someone-stole-my-name/portage-cfg/actions/workflows/molecule.yml)
=========

A role to manage a bunch of portage config files.

Role Variables
--------------

- `portage_ansible_managed_filename`: In cases when paths like `/etc/portage/package.accept_keywords` are directories, a file with this name will be created in the corresponding path to include the requested line. [Default: `ansible_managed`]

- `portage_accept_keywords`: List of keywords to accept. Example:
```yaml
portage_accept_keywords:
  - atom: app-admin/ansible
    keyword: ~amd64
    # If `name` is specified, file with that name is created inside the `portage.accept_keywords` directory.
    name: some_filename
```

- `portage_accept_license`: List of licenses to accept. Example:
```yaml
portage_accept_license:
  - atom: app-editors/visual-studio-code
    license: MS-vscode-EULA license
    # If `name` is specified, file with that name is created inside the `portage.accept_keywords` directory.
    name: some_filename
```

- `portage_unmask`: List of lines to add to `package.unmask` file or to a file inside that directory.
- `portage_mask`: List of lines to add to `package.mask` file or to a file inside that directory.
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

License
-------
BSD
