# Check for connection to arXiv API

Check for connection to arXiv API

## Usage

``` r
can_arxiv_connect(max_time = 5)
```

## Arguments

- max_time:

  Maximum wait time in seconds

## Value

Returns TRUE if connection is established and FALSE otherwise.

## Examples

``` r
# \donttest{
if(interactive()) {
    can_arxiv_connect(2)
} # }
```
