# Deduplication And Reconciliation

## Duplicate Rule Design

Use identifiers when reliable:

```text
normalized DOI OR PMID OR stable accession ID
```

Use a metadata fallback for records without identifiers:

```text
normalized title + first author + source + year
```

The exact rule depends on library purpose and metadata quality. Normalize case,
spacing, punctuation, DOI prefixes, and obvious Unicode variants before comparison
when the tool permits it.

## Cases Requiring Review

Do not merge automatically without inspection when records may be:

- early-access and final versions;
- conference and journal versions;
- preprint and published versions;
- corrections, retractions, or editorials sharing titles;
- translated or abbreviated titles;
- same title but different authors or years;
- records with truncated titles or author lists.

Keep uncertain pairs in a quarantine group with the evidence for and against merging.

## Reconciliation Ledger

| Stage | Count | Evidence |
|---|---:|---|
| Search results | | |
| Expected exports | | |
| Actual exported records | | |
| Raw imports | | |
| Exact duplicates | | |
| Probable duplicates | | |
| Failed/malformed | | |
| Final unique | | |

Investigate:

- gaps or overlaps between batch ranges;
- a file imported twice or never imported;
- different database counts on different dates;
- source records duplicated as early-access/final entries;
- import filters dropping unsupported record types;
- missing abstracts or identifiers;
- deduplication rules that are too broad or too narrow.

Preserve logs and rejected-record files whenever the software provides them.
