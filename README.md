# Nomad musl builds for Alpine Linux

Unofficial musl-linked Nomad binaries, built from upstream
[hashicorp/nomad](https://github.com/hashicorp/nomad).

## Why?

HashiCorp only ships musl binaries for the **Enterprise** edition.
Community (OSS) binaries link against glibc and don't run on Alpine.

This repo automatically builds the community edition against musl.

## Usage

```sh
# Download
VERSION=v2.0.4
wget https://github.com/YOUR_USER/nomad-musl/releases/download/${VERSION}-musl/nomad
chmod +x nomad
sudo mv nomad /usr/local/bin/

# Verify
nomad version
```

## License

Nomad is licensed under the [BSL 1.1](https://github.com/hashicorp/nomad/blob/main/LICENSE)
(v1.7.0+). Building and distributing unofficial musl binaries is permitted
under the Additional Use Grant — this is not a competitive offering.

## Setup your own fork

1. Create a GitHub repo
2. Copy `.github/workflows/build.yml` into it
3. Go to **Settings → Actions → General → Workflow permissions**
   and enable **Read and write permissions**
4. Done. Builds run every 12 hours and on manual trigger.

To backfill older versions, trigger the workflow manually (`workflow_dispatch`)
with the desired version tag.

## Manual trigger

```
gh workflow run build.yml -f version=v2.0.4
```
