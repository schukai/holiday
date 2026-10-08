# holiday data 0.4.0

Source-cited public holiday data for Austria, Belgium, Germany, Finland, France, the United Kingdom, Hungary, Ireland, Italy, Liechtenstein, Luxembourg, Norway, Poland, Portugal, Sweden, the United States, covering
2007–2035. The release is an independently generated data
projection; it does not contain the private development history, generators or
archived source material.

## Country coverage

`high` means the declared scope is backed by official sources, cleared rights
and provenance, at least twenty historic calendar years, country test vectors
and all local repository gates. A narrower declared scope can be `high` without
claiming legal effects that sit outside that scope.

| Country | Quality | Released coverage | Notes |
|---|---|---|---|
| Austria (AT) | high | 2007–2035 | Nationwide statutory layer and all nine states; historic Good Friday is conditional through 2018 |
| Belgium (BE) | high | 2007–2035 | National private-sector layer, regions and provinces |
| Germany (DE) | high | 2007–2035 | All states and evidence-backed local branches |
| Finland (FI) | high | 2007–2035 | Named national holidays, all first-order regions, Åland and historic Eastern Uusimaa |
| France (FR) | high | 2007–2035 | FR legal regime including FR-971–978; NC, PF and WF are not included |
| United Kingdom (GB) | high | 2007–2035 | Four nations; appointment-dependent dates after 2028 are marked `projected` |
| Hungary (HU) | high | 2007–2035 | Statutory layer, Budapest and all nineteen counties |
| Ireland (IE) | high | 2007–2035 | National rules and all 26 county jurisdictions |
| Italy (IT) | high | 2007–2035 | National layer, all twenty regions and Rome's evidenced patronal exception; other municipal patronal holidays are outside scope |
| Liechtenstein (LI) | high | 2007–2035 | Statutory layer and all eleven municipalities |
| Luxembourg (LU) | high | 2007–2035 | Statutory layer and all cantons; bank-sector extension is outside scope |
| Norway (NO) | high | 2007–2035 | Mainland named-holiday layer; Svalbard and Jan Mayen are outside the declared scope |
| Poland (PL) | high | 2007–2035 | Statutory layer and all sixteen voivodeships |
| Portugal (PT) | high | 2007–2035 | National layer, all eighteen mainland districts, Azores and Madeira; municipal holidays are outside scope |
| Sweden (SE) | high | 2007–2035 | Thirteen named holidays and all twenty-one counties; ordinary weekly Sundays are outside the event catalogue |
| United States (US) | high | 2007–2035 | Federal statutory employee calendar; state holidays and territories are outside the declared scope |

The following programme countries are deliberately not part of this release:

| Country | Current quality | Remaining blocker |
|---|---|---|
| Switzerland (CH) | current | Bern's historic Article 20a classification remains unresolved |
| Netherlands (NL) | current | Official classification evidence for 2007–2015 remains unavailable |
| Monaco (MC) | research / rights-blocked | Official reuse permission is still required |
| Andorra (AD) | research / evidence-and-model-blocked | Historic annual and parish instruments plus a sector-calendar variant model are still required |
| Spain (ES) | research | First-order calendars are normalized through 2026, but 2027–2035 have not yet been officially appointed |
| Vatican City (VA) | research / rights-and-evidence-blocked | Reusable evidence for a general civil calendar has not been established |
| Canada (CA) | research overall; CA-FED, CA-AB, CA-BC and CA-MB high | The remaining provincial and territorial employment-standards calendars are not yet complete |

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
- `RELEASE.json` marks a final projection as `published`, records its release
  date and names both the content checksum file and the archive checksum
  sidecar.

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
