# clawhub

ClawHub CLI layer for OpenCharly images.

The `clawhub` candy installs the `clawhub` npm package globally (via
`package.json`, requiring `nodejs`), landing the commander-based `clawhub` CLI on
the npm global bin path at `~/.npm-global/bin` (npm also creates the `clawdhub`
alias). The CLI searches, installs, and updates OpenClaw skills from the ClawHub
registry.

`clawhub --cli-version` reports its version offline, so the install and bin
wiring are verifiable without network access.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `clawhub` |
| Requires | `layer-nodejs` |
| Binary | `${HOME}/.npm-global/bin/clawhub` (alias `clawdhub`) |
| Install files | `charly.yml`, `package.json` |
| Service / port | none |

## How to use it

Compose the layer by pinning this repo in a box's `candy:` list:

```yaml
my-box:
  candy:
    base: fedora
    candy:
      - '@github.com/opencharly/layer-clawhub:v2026.243.0408'
```

After the image is built:

```bash
~/.npm-global/bin/clawhub --cli-version
~/.npm-global/bin/clawhub --help      # search, install, ...
```

## Layout

- `charly.yml` — the `clawhub:` candy entity: the `nodejs` require and the
  `check:` assertions, plus the embedded `skill:` entity.
- `package.json` — pins the `clawhub` npm package the build installs globally.
- `CHANGELOG/` — per-CalVer release notes.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skill: `/charly-openclaw:clawhub` — the ClawHub skill-registry CLI
- Runtime parent: `/charly-coder:nodejs`
- Bundled by: `/charly-openclaw:openclaw-full` (metalayer)
- Gateway that consumes installed skills: `/charly-openclaw:openclaw`
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
