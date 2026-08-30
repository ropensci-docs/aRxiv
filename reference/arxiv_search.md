# The main search function for aRxiv

Allows for progammatic searching of the arXiv pre-print repository.

## Usage

``` r
arxiv_search(
  query = NULL,
  id_list = NULL,
  start = 0,
  limit = 10,
  sort_by = c("submitted", "updated", "relevance"),
  ascending = TRUE,
  batchsize = 100,
  force = FALSE,
  output_format = c("data.frame", "list"),
  sep = "|"
)
```

## Arguments

- query:

  Search pattern as a string; a vector of such strings also allowed, in
  which case the elements are combined with `AND`.

- id_list:

  arXiv doc IDs, as comma-delimited string or a vector of such strings

- start:

  An offset for the start of search

- limit:

  Maximum number of records to return (must be \> 0).

- sort_by:

  How to sort the results (ignored if `id_list` is provided)

- ascending:

  If TRUE, sort in ascending order; else descending (ignored if
  `id_list` is provided)

- batchsize:

  Maximum number of records to request at one time

- force:

  If TRUE, force search request even if it seems extreme

- output_format:

  Indicates whether output should be a data frame or a list.

- sep:

  String to use to separate multiple authors, affiliations, DOI links,
  and categories, in the case that `output_format="data.frame"`.

## Value

If `output_format="data.frame"`, the result is a data frame with each
row being a manuscript and columns being the various fields.

If `output_format="list"`, the result is a list parsed from the XML
output of the search, closer to the raw output from arXiv.

The data frame format has the following columns.

|         |                  |                       |
|---------|------------------|-----------------------|
| \[,1\]  | id               | arXiv ID              |
| \[,2\]  | submitted        | date first submitted  |
| \[,3\]  | updated          | date last updated     |
| \[,4\]  | title            | manuscript title      |
| \[,5\]  | summary          | abstract              |
| \[,6\]  | authors          | author names          |
| \[,7\]  | affiliations     | author affiliations   |
| \[,8\]  | link_abstract    | hyperlink to abstract |
| \[,9\]  | link_pdf         | hyperlink to pdf      |
| \[,10\] | link_doi         | hyperlink to DOI      |
| \[,11\] | comment          | authors' comment      |
| \[,12\] | journal_ref      | journal reference     |
| \[,13\] | doi              | published DOI         |
| \[,14\] | primary_category | primary category      |
| \[,15\] | categories       | all categories        |

The contents are all strings; missing values are empty strings (`""`).

The columns `authors`, `affiliations`, `link_doi`, and `categories` may
have multiple entries separated by `sep` (by default, `"|"`).

The result includes an attribute `"search_info"` that includes
information about the details of the search parameters, including the
time at which it was completed. Another attribute `"total_results"` is
the total number of records that match the query.

## See also

[`arxiv_count()`](https://docs.ropensci.org/aRxiv/reference/arxiv_count.md),
[`arxiv_open()`](https://docs.ropensci.org/aRxiv/reference/arxiv_open.md),
[`query_terms()`](https://docs.ropensci.org/aRxiv/reference/query_terms.md),
[`arxiv_cats()`](https://docs.ropensci.org/aRxiv/reference/arxiv_cats.md)

## Examples

``` r
# \donttest{
if(interactive()) {
    # search for author Peter Hall with deconvolution in title
    z <- arxiv_search(query = 'au:"Peter Hall" AND ti:deconvolution', limit=2)
    attr(z, "total_results") # total no. records matching query
    z$title

    # search for a set of documents by arxiv identifiers
    z <- arxiv_search(id_list = c("0710.3491v1", "0804.0713v1", "1003.0315v1"))
    # can also use a comma-separated string
    z <- arxiv_search(id_list = "0710.3491v1,0804.0713v1,1003.0315v1")
    # Journal references, if available
    z$journal_ref

    # search for a range of dates (in this case, one day)
    z <- arxiv_search("submittedDate:[199701010000 TO 199701012359]", limit=2)
} # }
```
