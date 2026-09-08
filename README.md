# idler scoop bucket

Personal [Scoop](https://scoop.sh) bucket for apps that are not published in the
official Scoop buckets.

## Usage

```powershell
scoop bucket add idler C:/Idler/Code/lab/dsh_playground/scoop-bucket
scoop install idler/gooey-pi
```

## Apps

| App | Version | Upstream |
| --- | --- | --- |
| `gooey-pi` | 1.1.16 | [am-will/gooey-pi](https://github.com/am-will/gooey-pi) |

`gooey-pi` is packaged from the upstream Windows ZIP (`GooeyPi-<version>-win-x64.zip`),
which unpacks `GooeyPi.exe` at the archive root, so the manifest needs no `extract_dir`.

## Updating a manifest

1. Edit `bucket/<app>.json` — bump `version`, the `url`, and the `hash`
   (upstream publishes `SHA256SUMS.txt` next to each release).
2. Commit the change.
3. Run `scoop update <app>`.

## Notes

- Scoop only searches buckets you have added, so a manifest that lives here is
  findable by `scoop search` only after `scoop bucket add` (as above).
- The bucket is a plain git repository. It works as a local path, and pushing it
  to GitHub makes it usable from other machines without changing the workflow.
