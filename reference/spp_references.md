# Get references for a given taxon concept

Retrieve available references for a given taxon concept.

## Usage

``` r
spp_references(
  taxon_id,
  raw = FALSE,
  token = NULL,
  verbose = TRUE,
  pause = 1,
  ...
)
```

## Arguments

- taxon_id:

  a vector of character strings containing species' taxon concept
  identifiers (see
  [`spp_taxonconcept()`](https://docs.ropensci.org/rcites/reference/spp_taxonconcept.md)).

- raw:

  a logical. Should raw data be returned?

- token:

  a character string containing the authentification token, see
  <https://api.speciesplus.net/documentation>. Default is set to `NULL`
  and requires the environment variable `SPECIESPLUS_TOKEN` to be set
  directly in `Renviron`. Alternatively,
  [`set_token()`](https://docs.ropensci.org/rcites/reference/set_token.md)
  can be used to set `SPECIESPLUS_TOKEN` for the current session.

- verbose:

  a logical. Should extra information be reported on progress?

- pause:

  a duration (in second) to suspend execution for (see
  [`Sys.sleep()`](https://rdrr.io/r/base/Sys.sleep.html)). This was
  added cause the web API returns a 404 error too many requests in a
  short time interval.

- ...:

  Further named parameters, see
  [`httr::GET()`](https://httr.r-lib.org/reference/GET.html).

## Value

If `raw` is set to `TRUE` then an object of class `spp_raw` (or
`spp_raw_multi` if `length(taxon_id) > 1`) is returned which is
essentially a list of lists (see option `as = 'parsed'` in
[`httr::content()`](https://httr.r-lib.org/reference/content.html)).
Otherwise, an object of class `spp_refs` (or `spp_refs_multi` if
`length(taxon_id) > 1`) is returned which is a list of one data frame:

- `references` that includes the identifier of the reference and the
  corresponding citation.

## References

<https://api.speciesplus.net/documentation/v1/references/index.html>

## Examples

``` r
if (FALSE) { # \dontrun{
# this calls will only work if a token is set and valid
res1 <- spp_references(taxon_id = '4521')
res2 <- spp_references(c('4521', '3210', '10255'))
res3 <- spp_references(taxon_id = '4521', raw = TRUE, verbose = FALSE,
 config = httr::progress())
} # }
```
