# Scryware Command — releases

Signed installer packages for **Scryware Command** (sysadmin-agent).
This repository carries release artifacts only; the source code
lives in a private repository.

## Downloads

Pick the package for your platform from the
[latest release](https://github.com/GrumpyDadPool/scryware-command-releases/releases/latest):

- `scryware-hub_<version>_amd64.deb` — hub, Debian/Ubuntu
- `scryware-hub_<version>_amd64.msi` — hub, Windows
- `scryware-reporter_<version>_amd64.deb` — reporter agent, Debian/Ubuntu
- `scryware-reporter_<version>_amd64.msi` — reporter agent, Windows

The hub runs the fleet dashboard and API; the reporter is the
lightweight agent installed on each managed endpoint. Most
installs want one hub and a reporter on everything else.

## Verify your download

Every release ships `SHA256SUMS` and a minisign signature,
`SHA256SUMS.minisig`. The release signing public key is:

```
untrusted comment: minisign public key 5C40C3793297C87E
RWRcQMN5MpfIfiuTQFxTgfDYT1sWfNY9clUMY3hhESnZ4KiIHfkdcwKQ
```

With [minisign](https://jedisct1.github.io/minisign/) installed:

```
minisign -Vm SHA256SUMS -P RWRcQMN5MpfIfiuTQFxTgfDYT1sWfNY9clUMY3hhESnZ4KiIHfkdcwKQ
sha256sum -c SHA256SUMS --ignore-missing
```

`SHA256SUMS` also lists the source tarball
(`sysadmin-agent-<version>.tar.gz`). The tarball is not mirrored
here, which is what `--ignore-missing` skips; the signature
covers the file exactly as published.

## Install

Debian/Ubuntu: `sudo apt install ./scryware-hub_<version>_amd64.deb`
Windows: run the `.msi`. The packages install a Python 3.10+
runtime environment from the system interpreter; see the release
notes on each release for specifics.
