# smfc RPM repository

This repository hosts the RPM packages for [smfc](https://github.com/petersulyok/smfc) — a fan controller for SuperMicro (home) servers.

## Compatible distributions

Requires Python ≥ 3.10. Supported on:

| Distribution | Version |
|---|---|
| Fedora | 39, 40, 41, 42, 43 |
| RHEL / Rocky / AlmaLinux | 9, 10 |
| CentOS Stream | 9, 10 |
| openSUSE | Leap 15.5+, Tumbleweed |

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