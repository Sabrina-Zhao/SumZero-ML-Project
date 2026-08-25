# Public data previews

This directory contains short, anonymized previews of the tables used in the original analysis. The source data was provided under confidentiality restrictions and is not included in this repository.

## What these files are for

- Illustrating the categories of data used by the project.
- Documenting the expected source-table inventory at a high level.
- Allowing reviewers to inspect the repository without exposing proprietary records.

## Important limitations

- The previews contain only a small number of rows.
- Field names and values have been anonymized.
- The files do not preserve the complete executable source schema.
- The two notebooks cannot be rerun end to end from these previews alone.

The repository intentionally retains the notebooks' original saved outputs so that the archived analysis remains reviewable.

## Included table categories

The sample files cover investment ideas, comments, updates, views, likes, follows, attachments, catalysts, author ratings, consensus responses, security identifiers, price history, and prepared modeling datasets.

Do not commit raw or confidential exports to this directory. The repository's `.gitignore` is configured to ignore non-sample CSV files under `data/`.
