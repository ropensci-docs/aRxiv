# Open abstract for results of arXiv search

Open, in web browser, the abstract pages for each of set of arXiv search
results.

## Usage

``` r
arxiv_open(search_results, limit = 20)
```

## Arguments

- search_results:

  Data frame of search results, as returned from
  [`arxiv_search()`](https://docs.ropensci.org/aRxiv/reference/arxiv_search.md).

- limit:

  Maximum number of abstracts to open in one call.

## Value

(Invisibly) Vector of character strings with URLs of abstracts opened.

## Details

There is a delay between calls to
[`utils::browseURL()`](https://rdrr.io/r/utils/browseURL.html), with the
amount taken from the R option `"aRxiv_delay"` (in seconds); if missing,
the default is 3 sec.

## See also

[`arxiv_search()`](https://docs.ropensci.org/aRxiv/reference/arxiv_search.md)

## Examples

``` r
# \donttest{
if(interactive()) {
    z <- arxiv_search('au:"Peter Hall" AND ti:deconvolution')
    arxiv_open(z)
} # }
```
