# Get current EU annex listings, SRG opinions, and EU suspensions

Retrieve current EU annex listings, SRG opinions, and EU suspensions for
a given taxon concept (identifier must be known).

## Usage

``` r
spp_eu_legislation(
  taxon_id,
  scope = "current",
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

- scope:

  vector of character strings indicating the time scope of legislation,
  values are taken among `current`, `historic` and `all`. Default is set
  to `current`.

- language:

  vector of character strings indicating the language for the text of
  legislation notes, values are taken among `en` (English), `fr`
  (French) and `es` (Spanish). Default is `en`.

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
Otherwise, an object of class `spp_eu_leg` (or `spp_eu_leg_multi` if
`length(taxon_id)>1`) is returned which is a list of two data frames:

1.  `eu_listings`: lists EU annex listings EU suspensions,

2.  `eu_decisions`: lists EU decisions

## References

<https://api.speciesplus.net/documentation/v1/eu_legislation/index.html>

## Examples

``` r
if (FALSE) { # \dontrun{
# this calls will only work if a token is set and valid
res1 <- spp_eu_legislation(taxon_id = '4521')
res2 <- spp_eu_legislation(taxon_id = c('4521', '3210', '10255'))
res3 <- spp_eu_legislation(taxon_id = '4521', scope = 'historic')
res4 <- spp_eu_legislation(taxon_id = '4521', scope = 'all', language='fr',
 verbose = FALSE, config=httr::verbose())
} # }
```
