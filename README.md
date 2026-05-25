# smfc RPM repository

This repository hosts the RPM packages for [smfc](https://github.com/petersulyok/smfc) — a fan controller for SuperMicro (home) servers.

## Compatible distributions

Requires Python ≥ 3.10. Supported on:

| Distribution  | Version                |
|---------------|------------------------|
| Fedora        | 39+                    |
| RHEL          | 9+ (with EPEL)         |
| CentOS Stream | 9+ (with EPEL)         |
| Rocky Linux   | 9+ (with EPEL)         |
| AlmaLinux     | 9+ (with EPEL)         |
| openSUSE      | Leap 15.5+, Tumbleweed |

## Installation

```bash
sudo dnf config-manager addrepo --from-repofile=https://petersulyok.github.io/smfc-rpm/smfc.repo
sudo dnf install smfc
```

(On older `dnf` versions: `sudo dnf config-manager --add-repo=https://petersulyok.github.io/smfc-rpm/smfc.repo`.)

## Updating

```bash
sudo dnf upgrade smfc
```

## Removing

```bash
sudo dnf remove smfc
sudo rm /etc/yum.repos.d/smfc.repo
```