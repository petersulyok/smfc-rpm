# smfc RPM repository

This repository hosts the RPM packages for [smfc](https://github.com/petersulyok/smfc) — a fan controller for SuperMicro (home) servers.

## Compatible distributions

Requires Python ≥ 3.11. Supported on:

| Distribution  | Version        | Package          | `.repo` file   |
|---------------|----------------|------------------|----------------|
| Fedora        | 43, 44         | `.fc43`, `.fc44` | `smfc.repo`    |
| RHEL          | 10 (with EPEL) | `.el10`          | `smfc-el.repo` |
| AlmaLinux     | 10 (with EPEL) | `.el10`          | `smfc-el.repo` |
| Rocky Linux   | 10 (with EPEL) | `.el10`          | `smfc-el.repo` |
| CentOS Stream | 10 (with EPEL) | `.el10`          | `smfc-el.repo` |
| Oracle Linux  | 10 (with EPEL) | `.el10`          | `smfc-el.repo` |

Each Fedora release has its own package, built for its Python version. The supported Fedora releases change with
the Fedora release cycle. One `.el10` package serves all Enterprise Linux 10 distributions.

Not supported:

- **Enterprise Linux 9**: smfc needs Python 3.11 or newer, and EL9 has `python3-pyudev` only for Python 3.9.
- **openSUSE**: the package uses Fedora macros and package names. On openSUSE, use the
  [Docker image](https://github.com/petersulyok/smfc/blob/main/README.md#94-docker-installation) or the
  [manual installation](https://github.com/petersulyok/smfc/blob/main/README.md#95-manual-installation-and-uninstallation).

## Installation

### Fedora

```bash
sudo dnf config-manager addrepo --from-repofile=https://petersulyok.github.io/smfc-rpm/smfc.repo
sudo dnf install smfc
```

### Enterprise Linux 10

The `python3-pyudev` dependency comes from [EPEL](https://docs.fedoraproject.org/en-US/epel/getting-started/), so
enable EPEL first:

```bash
sudo dnf install epel-release
sudo dnf config-manager --add-repo https://petersulyok.github.io/smfc-rpm/smfc-el.repo
sudo dnf install smfc
```

On RHEL and Oracle Linux, the `epel-release` package is not available under this name; enable EPEL as described in
the [EPEL documentation](https://docs.fedoraproject.org/en-US/epel/getting-started/).

### Repository signing key

The packages and the repository metadata are signed. On the first installation, `dnf` asks you to accept
[`smfc-repo.gpg`](https://petersulyok.github.io/smfc-rpm/smfc-repo.gpg). Check that its fingerprint is:

```
6912 A339 7CF9 7359 857A  B82F 9E06 E863 D50D 7541
```

### Old `smfc.repo` on Fedora

If `/etc/yum.repos.d/smfc.repo` contains `baseurl=https://petersulyok.github.io/smfc-rpm/` (without `fedora/`), it
points to the old repository, which receives updates only for a limited time. Replace the file with the current one:

```bash
sudo dnf config-manager addrepo --overwrite --from-repofile=https://petersulyok.github.io/smfc-rpm/smfc.repo
```

## Updating

```bash
sudo dnf upgrade smfc
```

## Removing

```bash
sudo dnf remove smfc
sudo rm -f /etc/yum.repos.d/smfc.repo     # Fedora
sudo rm -f /etc/yum.repos.d/smfc-el.repo  # Enterprise Linux 10
```

## Repository layout

The repository is served from the `gh-pages` branch. `publish-rpm.yml` runs on each smfc release and puts each RPM
in the tree of its dist tag:

```
fedora/43/      smfc-*.fc43.noarch.rpm, repodata/
fedora/44/      smfc-*.fc44.noarch.rpm, repodata/
el10/           smfc-*.el10.noarch.rpm, repodata/
packages/       old Fedora tree, for old smfc.repo files (transition period only)
smfc.repo       Fedora, baseurl: fedora/$releasever/
smfc-el.repo    Enterprise Linux, baseurl: el$releasever_major/
smfc-repo.gpg   public key
```

Every released version stays in its tree. The RPM files are also available on the
[smfc release pages](https://github.com/petersulyok/smfc/releases).
