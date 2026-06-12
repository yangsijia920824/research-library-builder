# Exploratory Tool Learning

Use this workflow when the software version, menu layout, or file format is unfamiliar.

## Safe Feedback Loop

1. State the immediate outcome, such as "import one RIS record with an abstract."
2. Inventory visible controls, file metadata, help text, and previews.
3. Form the smallest testable hypothesis.
4. Test in a disposable library, copy, or small batch.
5. Inspect the output rather than trusting a success message.
6. Record what changed and why the result passed or failed.
7. Repeat with one changed variable.

## Evidence Hierarchy

Prefer:

1. actual imported/exported output;
2. file headers and structured tags;
3. live interface labels and previews;
4. current official documentation;
5. remembered instructions from another version.

## Experiment Log

| Goal | Hypothesis | Change | Observed output | Decision |
|---|---|---|---|---|

## Escalate Carefully

Seek documentation or expert help when:

- a test could overwrite or delete the only copy;
- licensing or permissions block the operation;
- metadata loss is silent and difficult to detect;
- the number of options makes exhaustive testing costly;
- the workflow involves private or regulated data.

Exploration is not random clicking. It is controlled experimentation with reversible
actions and explicit observations.
