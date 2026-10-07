# holiday data 0.2.1

Source-cited public holiday data for Austria, Belgium, Germany, France, the United Kingdom, Hungary, Ireland, Liechtenstein, Luxembourg, Poland, covering
2007–2035. The release is an independently generated data
projection; it does not contain the private development history, generators or
archived source material.

## Files

- `dist/holidays.csv`, `.json` and `.xml` contain the same holiday records,
  including their machine-readable `legal_status`, `applicability` and
  `confirmation`.
- `dist/jurisdictions.json` contains the time-versioned public jurisdiction
  catalogue needed to resolve country, regional and local codes.
- `dist/ics/` contains the standalone country, regional and local calendars
  listed in `RELEASE.json`. CSV, JSON and XML are the complete record set; the
  absence of a standalone calendar for a historic or very granular code does
  not remove that record from those complete exports.
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
Historic Austrian Good Friday is conditional through 2018 because it applied
only to employees belonging to one of the four churches named in the former
§ 7(3) Arbeitsruhegesetz. That rule was repealed in March 2019.

## Consumer semantics

Consumers should select records by jurisdiction and date, then keep the three
independent dimensions intact:

- `legal_status` states the legal effect, for example a statutory day off, a
  public rest day, a bank holiday or an observance. It must not be inferred
  from the display name or `kind`.
- `applicability = "conditional"` requires the localized `condition_*` to be
  evaluated for the user, workplace or municipality. An unchecked condition
  is not a generally applicable holiday.
- `confirmation = "projected"` is planning information, not an enacted or
  officially appointed date. Applications should distinguish it visibly from
  `confirmed` records and refresh it when a new release becomes available.

The same calendar date may legitimately have multiple records with different
identities or legal effects. Do not deduplicate records by date alone.

## Confirmed and projected dates

`confirmation = "confirmed"` means that the date follows from law already in
force or from an official instrument that has appointed it. `projected` marks
an evidence-based future planning date where the holiday has legal authority
but its exact appointment still depends on a later official instrument. A
projected record must not be presented as enacted or officially appointed.

iCalendar exposes the same distinction as
`X-HOLIDAY-CONFIRMATION:CONFIRMED` or
`X-HOLIDAY-CONFIRMATION:PROJECTED`.

## Licence

Generated holiday data is licensed under CC BY 4.0. Attribute it as:
“holiday by schukai, CC BY 4.0”. Documentation and metadata are provided under
MIT. Current legal provider details are maintained in the
[schukai imprint](https://www.schukai.com/de/impressum). See `LICENSES.md`,
`LICENSE-DATA`, `LICENSE` and `ATTRIBUTIONS.md`.

This data is supplied for general informational and software use and is not
legal advice. Check the cited official source when legal consequences depend
on a date.
