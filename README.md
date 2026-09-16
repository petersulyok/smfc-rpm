# smfc RPM repository

This repository hosts the RPM packages for [smfc](https://github.com/petersulyok/smfc) — a fan controller for SuperMicro (home) servers.

## Compatible distributions

Requires Python ≥ 3.10. Supported on:

| Distribution  | Version                | Repository file |
|---------------|------------------------|-----------------|
| Fedora        | 39+                    | smfc.repo       |
| RHEL          | 10+                    | smfc-el.repo    |
| CentOS Stream | 10+                    | smfc-el.repo    |
| Rocky Linux   | 10+                    | smfc-el.repo    |
| AlmaLinux     | 10+                    | smfc-el.repo    |
| openSUSE      | Leap 15.5+, Tumbleweed | smfc.repo       |

## Installation

```bash
sudo dnf config-manager addrepo --from-repofile=https://petersulyok.github.io/smfc-rpm/smfc.repo
sudo dnf install smfc
```

For older `dnf` versions or Enterprise Linux:
```bash
sudo dnf config-manager --add-repo=https://petersulyok.github.io/smfc-rpm/smfc.repo # or smfc-el.repo
sudo dnf install smfc
```

## Updating

```bash
sudo dnf upgrade smfc
```

## Removing

```bash
sudo dnf remove smfc
sudo rm /etc/yum.repos.d/smfc.repo    # or smfc-el.repo
```
