# Contributing

Thanks for helping improve this dataset.

## What contributions are welcome

- Fixing province naming or codes (`PROVINSI`, `KODE_PROV`)
- Boundary corrections (geometry fixes, missing/extra features)
- Documentation improvements (examples, metadata)
- Adding validation tooling (optional scripts) without inflating the repository

## Before you open a PR

- Check the dataset still contains **38** provinces.
- Keep property fields consistent:
  - `PROVINSI`: string province name
  - `KODE_PROV`: string province code
  - GeoJSON `id`: should match `KODE_PROV` when present
- Prefer minimal diffs (only change what is necessary).

## Reporting an issue

When reporting a data problem, include:

- Province name(s) impacted
- What’s wrong (name/code/geometry)
- Reference link(s) (official source, credible dataset, or announcement)
- Optional: screenshot or map link demonstrating the mismatch

## Submitting a pull request

- Describe the change and link the issue (if any).
- Include references for administrative changes.
- If you changed geometry, mention the tool and process used (e.g., QGIS, mapshaper).

## Licensing

By contributing, you agree that your contributions may be published under:

- `LICENSE` (for documentation/scripts)
- `DATA_LICENSE.md` (for dataset files)

