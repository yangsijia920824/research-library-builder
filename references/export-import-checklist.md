# Export And Import Checklist

## Source Snapshot

Record:

```text
database:
collection/index:
query:
filters:
search date:
search count:
saved search or query ID:
```

## Field Selection

Prefer:

- title;
- authors and affiliations when needed;
- journal or source;
- year, volume, issue, and pages or article number;
- DOI, PMID, accession number, or other identifiers;
- abstract;
- author and indexed keywords;
- document and reference type;
- cited references when required for citation-network work.

Do not trust database defaults. Inspect the export-field selection explicitly.

## Format Selection

Select a format that the destination can map correctly. Typical candidates include
RIS, BibTeX, EndNote tagged formats, MEDLINE/NBIB, CSV, and database-specific tagged
text.

Validate by checking:

1. extension and file header;
2. source documentation or live export label;
3. destination import-filter name;
4. a pilot record after import.

## Batch Manifest

| Batch | Source | Record range/date window | Expected | Format | Fields | Filename | Exported |
|---|---|---|---:|---|---|---|---:|

Batch ranges must be non-overlapping and gap-free. Preserve the raw files.

## Pilot Import Inspection

Check at least one ordinary article plus difficult record types such as a conference
paper, early-access item, book chapter, correction, or record without a DOI.

| Field | Expected | Imported | Pass |
|---|---|---|---|
| Title | | | |
| Authors | | | |
| Source | | | |
| Year | | | |
| Abstract | | | |
| Identifier | | | |
| Keywords | | | |
| Reference type | | | |

If fields are shifted or empty, stop the full import and change one variable at a
time: export format, exported fields, import filter, encoding, or destination mapping.
