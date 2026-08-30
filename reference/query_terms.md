# arXiv query field terms

Possible terms that correspond to different fields in arXiv searches.

## Usage

``` r
data(query_terms)
```

## Format

A data frame with two columns: the `term` and corresponding
`description`.

## Source

<https://info.arxiv.org/help/api/user-manual.html>

## Author

Karl W Broman

## Examples

``` r
query_terms
#>               term                                      description
#> 1               ti                                            Title
#> 2               au                                           Author
#> 3              abs                                         Abstract
#> 4               co                                          Comment
#> 5               jr                                Journal Reference
#> 6              cat                                 Subject Category
#> 7               rn                                    Report Number
#> 8              all                                 All of the above
#> 9    submittedDate Date/time of initial submission, as YYYYMMDDHHMM
#> 10 lastUpdatedDate        Date/time of last update, as YYYYMMDDHHMM
```
