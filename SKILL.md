---
name: research-library-builder
description: Build, migrate, deduplicate, audit, and maintain reproducible research literature libraries from scholarly search results. Use when Codex needs to export records from databases such as Web of Science, Scopus, PubMed, or other indexes; choose record fields and exchange formats; batch large exports; import records into EndNote, Zotero, or another reference manager; diagnose format or field-mapping failures; configure and verify duplicate detection; reconcile search, export, and import counts; preserve provenance; create search alerts; or design an incremental literature-library update workflow.
---

# Research Library Builder

Treat literature collection as a controlled data pipeline:

```text
search set -> staged export -> validated import -> deduplication -> reconciliation -> updates
```

The goal is not merely to move files. Build a library whose coverage, fields,
duplicates, omissions, and update history can be explained.

## Establish The Library Contract

Before operating, record:

1. research purpose and downstream use;
2. database, collection, query, filters, and search date;
3. observed search-result count;
4. destination reference manager and version when known;
5. mandatory fields, usually title, authors, source, year, identifiers, abstract,
   keywords, and cited references when needed;
6. acceptable duplicate policy;
7. whether the task is a new library, migration, merge, repair, or incremental update.

Do not assume current database limits, menu locations, available formats, or default
fields from old instructions. Verify unstable details from the live interface or
current official documentation when they matter.

## Separate Search Diagnosis From Collection

During query testing, inspect only enough titles and targeted abstract passages to
judge retrieval quality. Do not require full-text downloading or deep reading before
collecting records.

Once the search is accepted:

1. preserve the exact query and result count;
2. save the result set or search history when the platform supports it;
3. create an alert if continuing surveillance is useful;
4. export the accepted records into a staging area;
5. postpone detailed screening and classification until after the records are safely
   inside the literature library.

This separation prevents query testing, reading, downloading, and library maintenance
from becoming one slow and irreproducible activity.

## Design The Export

Read [references/export-import-checklist.md](references/export-import-checklist.md)
when choosing formats, fields, and batches.

1. Choose an exchange format supported by both source and destination.
2. Include abstracts explicitly; many databases omit them by default.
3. Include identifiers and keywords where available.
4. Include cited references only when they serve a defined downstream use and the
   added size is acceptable.
5. If the platform limits each export, divide records into non-overlapping,
   gap-free batches.
6. Give every batch a manifest entry containing database, query ID, record range,
   export date, format, selected fields, expected count, and filename.
7. Keep raw export files unchanged as provenance artifacts.

Never report an export as complete merely because files were downloaded. Confirm that
all intended ranges exist and that their expected counts sum to the search count.

## Validate With A Pilot Import

Unknown software options should be tested, not guessed.

1. Create a disposable test library or backup the destination.
2. Import a small representative batch.
3. Match the import filter to the actual file format, not to a superficially similar
   product name.
4. Inspect several records for title, authors, source, year, abstract, identifiers,
   keywords, and reference type.
5. Diagnose missing or shifted fields before importing the full collection.
6. Change one import variable at a time and log the result.
7. Proceed to full import only after the pilot is structurally correct.

Use the file extension, file header, metadata tags, and destination preview as
evidence. If no import option works, reconsider the source export format rather than
repeating the same failed mapping.

## Configure Deduplication Deliberately

Read [references/deduplication-and-reconciliation.md](references/deduplication-and-reconciliation.md)
before deleting or discarding records.

1. Inspect the destination's duplicate-matching fields and normalization behavior.
2. Prefer stable identifiers when coverage is adequate, but retain a metadata-based
   fallback for records lacking identifiers.
3. Pilot the rule on a sample with known duplicates and near-duplicates.
4. Review false-positive risks such as editorials, corrections, conference and journal
   versions, early-access and final records, translated titles, and reused titles.
5. Quarantine or group uncertain duplicates before irreversible deletion.
6. Record the rule used for each import or merge.

Deduplication is both a cleaning step and an error-control mechanism: idempotent
imports make accidental repeated batches less harmful and make missing batches easier
to detect.

## Reconcile Counts

Track at least:

```text
search count
expected exported count
actual exported records
raw imported count
duplicates rejected or merged
failed or malformed records
final unique count
```

Explain every difference. A valid reconciliation usually follows:

```text
raw imported = final unique + duplicates removed + failed/quarantined records
```

Counts alone do not prove coverage, but unexplained differences are a strong warning.
Check batch boundaries, repeated files, omitted files, database-side duplicates,
import-filter failures, and records without mandatory fields.

## Maintain Incrementally

1. Save the query and create a database alert when available.
2. Accumulate updates into sensible batches instead of importing every notification.
3. Label each update with source query and date window.
4. Import with the same validated format, field set, and duplicate policy.
5. Reconcile each update independently.
6. Avoid re-screening records already processed by preserving status, groups, tags,
   or an external screening ledger.

## Learn Changed Or Unknown Tools

Read [references/exploratory-tool-learning.md](references/exploratory-tool-learning.md)
when menus, versions, formats, or software differ from prior examples.

Use a feedback loop:

```text
observe -> form a small hypothesis -> test safely -> inspect output -> update the model
```

Do not hide the reasoning behind a successful option when transferability matters.
Document rejected options and the evidence that selected the working one.

## Deliver A Reproducible Build Report

Unless the user requests another format, provide:

1. library purpose and scope;
2. source databases, exact searches, filters, and dates;
3. export format and selected fields;
4. batch manifest;
5. import mapping and pilot validation;
6. deduplication rule and audit findings;
7. count reconciliation;
8. unresolved anomalies and quarantine list;
9. update and alert plan;
10. paths or links to raw exports, destination library, and logs when available.

## Guardrails

- Do not fabricate search counts, export limits, menu locations, or format support.
- Do not delete suspected duplicates without a reviewable rule and recovery path.
- Do not overwrite the only copy of a library during migration or testing.
- Do not silently omit abstracts or other mandatory downstream fields.
- Do not mix raw exports with modified files without preserving provenance.
- Do not claim full coverage until batches and counts have been reconciled.
- Treat article-specific software instructions as examples, not timeless facts.
