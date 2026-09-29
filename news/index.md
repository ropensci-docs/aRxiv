# Changelog

## aRxiv 0.21-1

### MINOR CHANGES

- Remove changes to `aRxiv_delay` in examples.

## aRxiv 0.20

CRAN release: 2026-06-17

### BUG FIXES

- arXiv is now sometimes giving empty results rather than an error.
  Revised `result2list()` to accommodate this.

- Increased `aRxiv_delay` in vignette and tests to 3 sec; continually
  getting “too many requests” errors otherwise.

## aRxiv 0.18

CRAN release: 2025-12-13

### MINOR CHANGES

- Avoid running examples on CRAN, to avoid `R CMD check` failures.
  They’re already in `\donttest{ }`, but now also put them within
  `if(interactive()) { }`.

## aRxiv 0.16

CRAN release: 2025-12-08

### BUG FIXES

- Got `clean_links()` working again, so abstract, pdf and doi links are
  included in the search results. \[Issue
  [\#68](https://github.com/ropensci/aRxiv/issues/68)\]

- Capture result that looks blank but contains the error “Rate
  exceeded.” \[Issue
  [\#66](https://github.com/ropensci/aRxiv/issues/66)\]

- `sort_by` in
  [`arxiv_search()`](https://docs.ropensci.org/aRxiv/reference/arxiv_search.md)
  is working again. \[Issue
  [\#70](https://github.com/ropensci/aRxiv/issues/70)\]

## aRxiv 0.14

CRAN release: 2025-11-14

### MINOR CHANGES

- Small changes to aRxiv vignette to avoid errors if we cannot connect
  to the arXiv API.

- In the vignette: the arXiv API no longer allows you to search on
  `lastUpdatedDate`.

### BUG FIXES

- The arXiv API no longer seems to allow `max_results == 0`, so in
  [`arxiv_search()`](https://docs.ropensci.org/aRxiv/reference/arxiv_search.md)
  we now require `limit>0`, and in
  [`arxiv_count()`](https://docs.ropensci.org/aRxiv/reference/arxiv_count.md)
  and
  [`can_arxiv_connect()`](https://docs.ropensci.org/aRxiv/reference/can_arxiv_connect.md)
  we use `max_results=1`.

- Skipping tests of `sort_by` in
  [`arxiv_search()`](https://docs.ropensci.org/aRxiv/reference/arxiv_search.md);
  the arXiv API seems to be ignoring it.

## aRxiv 0.12

CRAN release: 2025-07-29

### BUG FIXES

- The package had totally stopped working. Got it working again by using
  `GET` rather than `POST`, and `query` rather than `body`.

- Fixed a typo in
  [`arxiv_count()`](https://docs.ropensci.org/aRxiv/reference/arxiv_count.md)
  that had been introduced way back in December, 2014.

## aRxiv 0.10

CRAN release: 2024-02-29

### BUG FIXES

- Small revision to aRxiv vignette to deal with the change in the
  structure of the `arxiv_cats` dataset.

## aRxiv 0.8

CRAN release: 2024-01-22

### MINOR CHANGES

- Update arxiv_cats, datasets with category information, and the scripts
  to build that and the dataset query_terms.

## aRxiv 0.6

CRAN release: 2021-12-06

### MINOR CHANGES

- For testing, switch to use of github actions rather than appveyor and
  travis.

### BUG FIXES

- Partial fix of a case with a corrupt record. Was getting an error if
  you search multiple batches and later ones were NULL.

## aRxiv 0.5.20

### MINOR CHANGES

- Small fixes regarding use of class(), in particular changing
  class(x)==“blah” to inherits(x, “blah”).

## aRxiv 0.5.19

CRAN release: 2019-08-08

### MINOR CHANGES

- Add ORCIDs

- Update vignette

## aRxiv 0.5.18

### MINOR CHANGES

- Convert documentation to markdown

## aRxiv 0.5.17

### MINOR CHANGES

- Two small fixes to the vignette.

## aRxiv 0.5.16

CRAN release: 2017-04-28

### BUG FIXES

- To eliminate continued pain over empty search queries, just trap them
  in advance and don’t send them to arXiv.

## aRxiv 0.5.15

CRAN release: 2017-04-05

### BUG FIXES

- Results for empty search queries seems to have changed; fixed to give
  appropriate return values.

## aRxiv 0.5.10

CRAN release: 2015-05-27

### BUG FIXES

- Fix a small problem related to a new behavior in a pre-release version
  of the httr package. (httr is no longer dropping NULLs from the POST
  search body.)

- Fix a test error, that arose due to a change in the order of records
  returned by a query.

## aRxiv 0.5.8

CRAN release: 2014-12-28

### BUG FIXES

- arXiv connection errors was causing test errors. Added a function to
  test connection to arXiv; tests are skipped if we can’t connect.

- try to avoid many of the tests on CRAN, where intermittent test errors
  will cause universal headaches.

## aRxiv 0.5.5

CRAN release: 2014-11-07

### BUG FIXES

- Fix mistakes in the table in the help for arxiv_search that describes
  the output.

- When searching in batches, arxiv_search could return more than the
  requested limit.

- Fix tests of date range; a new 2013 arXiv manuscript changed the
  expected count.

## aRxiv 0.5.2

CRAN release: 2014-09-18

### NEW FEATURES

- released to CRAN
