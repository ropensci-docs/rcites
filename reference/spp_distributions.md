# Get distributions data available for a given taxon concept

Retrieve distributions data available for a given taxon concept for
which the the taxon identifier is known.

## Usage

``` r
spp_distributions(
  taxon_id,
  language = "en",
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

- language:

  vector of character strings indicating the language for the names of
  distributions, values are taken among `en` (English), `fr` (French)
  and `es` (Spanish). Default is `en`.

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
`spp_raw_multi` if `length(taxon_id)>1`) is returned which is
essentially a list of lists (see option `as = 'parsed'` in
[`httr::content()`](https://httr.r-lib.org/reference/content.html)).
Otherwise, an object of class `spp_distr` (or `spp_distr_multi` if
`length(taxon_id) > 1`) is returned which is a list of two data frames:

1.  `distributions`: lists distributions for a given taxon concept,

2.  `references`: lists the corresponding references. In case `taxon_id`
    includes several elements

## References

<https://api.speciesplus.net/documentation/v1/distributions/index.html>

## Examples

``` r
if (FALSE) { # \dontrun{
 # this calls will only work if a token is set and valid
 res1 <- spp_distributions(taxon_id = '4521')
 res2 <- spp_distributions(taxon_id = c('4521', '3210', '10255'))
 res3 <- spp_distributions(taxon_id = '4521', raw = TRUE)
 res4 <- spp_distributions(taxon_id = '4521', language = 'fr',
 verbose = FALSE, config = httr::progress())
} # }
```
