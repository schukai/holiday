# holiday data 0.1.0

Source-cited public holiday data for Austria and France, covering
2007–2031. The release is an independently generated data
projection; it does not contain the private development history, generators or
archived source material.

## Files

- `dist/holidays.csv`, `.json` and `.xml` contain the same holiday records.
- `dist/ics/` contains country and regional iCalendar files.
- `provenance/sources.json` summarizes the official sources and preserved
  evidence hashes used for this release.
- `ATTRIBUTIONS.md` records the required source credits.
- `SHA256SUMS` covers every other file in the projection.

Verify the downloaded projection with:

```text
sha256sum -c SHA256SUMS
```

## Conditional holidays

Records with `applicability = "unconditional"` apply directly to their named
jurisdiction. Records marked `conditional` are candidates whose localized
`condition_*` text must be resolved, for example through a location check or
an explicit checkbox. They must not be presented as applying throughout the
broad region.

French Good Friday is conditional in Moselle, Bas-Rhin and Haut-Rhin because
it applies only in qualifying municipalities under the stated local rule.

## Licence

Generated holiday data is licensed under CC BY 4.0. Attribute it as:
“holiday by schukai GmbH, CC BY 4.0”. Documentation and metadata are provided
under MIT. See `LICENSES.md`, `LICENSE-DATA`, `LICENSE` and
`ATTRIBUTIONS.md`.

This data is supplied for general informational and software use and is not
legal advice. Check the cited official source when legal consequences depend
on a date.
