# personal scoop bucket

Personal, private [Scoop](https://scoop.sh) bucket for apps that are not published
in the official Scoop buckets.

## Usage

```powershell
scoop bucket add personal git@github.com:idlercloud/scoop-bucket.git
scoop install personal/gooey-pi
```

HTTPS works too, as long as Git Credential Manager is set up:

```powershell
scoop bucket add personal https://github.com/idlercloud/scoop-bucket.git
```

## Apps

| App | Version | Upstream |
| --- | --- | --- |
| `gooey-pi` | 1.1.16 | [am-will/gooey-pi](https://github.com/am-will/gooey-pi) |

`gooey-pi` is packaged from the upstream Windows ZIP (`GooeyPi-<version>-win-x64.zip`),
which unpacks `GooeyPi.exe` at the archive root, so the manifest needs no `extract_dir`.
The ZIP build is the portable one, so in-app auto-update does not apply — upgrades come
from bumping this manifest.

## Updating a manifest

1. Edit `bucket/<app>.json` — bump `version`, the `url`, and the `hash`
   (upstream publishes `SHA256SUMS.txt` next to each release).
2. Commit and push.
3. On every machine: `scoop update` (refreshes buckets) then `scoop update <app>`.

## Notes

- Scoop only searches buckets you have added, so a manifest that lives here is
  findable by `scoop search` only after `scoop bucket add` (as above).
- Scoop shells out to plain `git`, so a private bucket works as long as git can
  authenticate. Use SSH or Git Credential Manager; never embed a token in the
  remote URL, because git stores it in plaintext in
  `~/scoop/buckets/<bucket>/.git/config`.
- `checkver` / `autoupdate` query the *upstream* repository's GitHub API, so they
  are unaffected by this bucket being private.
