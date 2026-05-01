# rclone

[![Source Code](https://img.shields.io/badge/github-source%20code-blue?logo=github&logoColor=white)](https://github.com/rolehippie/rclone)
[![General Workflow](https://github.com/rolehippie/rclone/actions/workflows/general.yml/badge.svg)](https://github.com/rolehippie/rclone/actions/workflows/general.yml)
[![Readme Workflow](https://github.com/rolehippie/rclone/actions/workflows/docs.yml/badge.svg)](https://github.com/rolehippie/rclone/actions/workflows/docs.yml)
[![Galaxy Workflow](https://github.com/rolehippie/rclone/actions/workflows/galaxy.yml/badge.svg)](https://github.com/rolehippie/rclone/actions/workflows/galaxy.yml)
[![License: Apache-2.0](https://img.shields.io/github/license/rolehippie/rclone)](https://github.com/rolehippie/rclone/blob/master/LICENSE)
[![Ansible Role](https://img.shields.io/badge/role-rolehippie.rclone-blue)](https://galaxy.ansible.com/rolehippie/rclone)

Ansible role to install and configure rclone backup solution.

## Sponsor

Building and improving this Ansible role have been sponsored by my current and previous employers like **[Cloudpunks GmbH](https://cloudpunks.de)** and **[Proact Deutschland GmbH](https://www.proact.eu)**.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [rclone_arch](#rclone_arch)
  - [rclone_backups_extra](#rclone_backups_extra)
  - [rclone_backups_general](#rclone_backups_general)
  - [rclone_definitions](#rclone_definitions)
  - [rclone_package](#rclone_package)
  - [rclone_version](#rclone_version)
- [Discovered Tags](#discovered-tags)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.10`

## Default Variables

### rclone_arch

Architecture of the package to install

#### Default value

```YAML
rclone_arch: "{{ 'arm64' if ansible_architecture == 'aarch64' or ansible_architecture == 'arm64' else 'amd64' }}"
```

### rclone_backups_extra

List of extra backup jobs

#### Default value

```YAML
rclone_backups_extra: []
```

#### Example usage

```YAML
rclone_backups_extra:
  - name: example
    minute: "0"
    hour: "6"
    day: "*"
    month: "*"
    weekday: "*"
    content: |
      exit 1
  - name: example-from-url
    minute: "0"
    hour: "6"
    day: "*"
    month: "*"
    weekday: "*"
    url: http://example.com/example.yml
  - name: example-from-template
    minute: "0"
    hour: "6"
    day: "*"
    month: "*"
    weekday: "*"
    src: path/to/template.j2
  - name: example-to-remove
    state: absent
```

### rclone_backups_general

List of general backup jobs

#### Default value

```YAML
rclone_backups_general: []
```

#### Example usage

```YAML
rclone_backups_general:
  - name: example
    minute: "0"
    hour: "6"
    day: "*"
    month: "*"
    weekday: "*"
    content: |
      exit 1
  - name: example-from-url
    minute: "0"
    hour: "6"
    day: "*"
    month: "*"
    weekday: "*"
    url: http://example.com/example.yml
  - name: example-from-template
    minute: "0"
    hour: "6"
    day: "*"
    month: "*"
    weekday: "*"
    src: path/to/template.j2
  - name: example-to-remove
    state: absent
```

### rclone_definitions

List of remote definitions

#### Default value

```YAML
rclone_definitions: []
```

#### Example usage

```YAML
rclone_definitions:
  - name: flexvault
    endpoint: https://s3.tms.proactcloud.de
    access_key: 8OK3V7PXMFDUTJJ7O4MT
    secret_key: aCP5DMfw1-usOPkcu+wHSaRkgbAHY5O4rOKPCK6+
    bucket: backups
    filename_ecryption: standard
    directory_encryption: true
    primary_password: Mire5vohR0ohn6bei8tahngair4oophae6IefochuquopheemoaH
    secondary_password: iechaa6xoxa9rie1iu0ucoM9Fa2da8thao1hai9Iv8wohphievie
```

### rclone_package

Download URL for the package to install

#### Default value

```YAML
rclone_package: https://github.com/rclone/rclone/releases/download/v{{ rclone_version }}/rclone-v{{ rclone_version }}-linux-{{ rclone_arch }}.deb
```

### rclone_version

Version of the release to install

#### Default value

```YAML
rclone_version: 1.74.0
```

## Discovered Tags

**_rclone_**

## Dependencies

- None

## License

Apache-2.0

## Author

[Thomas Boerger](https://github.com/tboerger)
