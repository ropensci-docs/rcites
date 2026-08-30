# Get taxon concepts for a search term

Retrieve the taxon concept of a specific taxon (scientific name).

## Usage

``` r
spp_taxonconcept(
  query_taxon,
  taxonomy = "CITES",
  with_descendants = FALSE,
  language = NULL,
  updated_since = NULL,
  per_page = 500,
  pages = NULL,
  raw = FALSE,
  token = NULL,
  verbose = TRUE,
  pause = 1,
  ...
)
```

## Arguments

- query_taxon:

  a character string containing the query (e.g. species). Scientific
  taxa only (max 255 characters).

- taxonomy:

  filter taxon concepts by taxonomy, accepts either 'CITES' or 'CMS' as
  its value. Default sets to 'CITES'.

- with_descendants:

  a logical. Should the search by name be broadened to include higher
  taxa?

- language:

  filter languages returned for common names. Value should be a vector
  of character strings including one or more country codes (two-letters
  country code [ISO 3166-1
  alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)). Default
  is set to `NULL`, showing all available languages.

- updated_since:

  a timestamp. Only entries updated after (and including) this timestamp
  will be pulled.

- per_page:

  an integer that indicates how many objects are returned per page for
  paginated responses. Default set to 500 which is the maximum.

- pages:

  a vector of integer that contains page numbers. Default is set to
  `NULL`, i.e. all pages are accessed.

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

If `raw = TRUE`, then a object of class `spp_raw` is returned, which is
a list of lists. If `raw = FALSE`, then an object of class `spp_taxon`
is returned, it is a collection of seven data frames:

1.  `all_id`: general information for all entries, including non-active
    taxon concepts,

2.  `general`: includes general information for active taxon concepts,

3.  `higher_taxa`: includes taxonomy information,

4.  `accepted_names`: list of accepted names (only for synonyms),

5.  `common_names`: list of common names (only for accepted names),

6.  `synonyms`: list of synonyms (only for accepted names),

7.  `cites_listing`: list of current CITES listings with annotations
    (missing if `taxonomy == 'CMS'`).

## References

<https://api.speciesplus.net/documentation/v1/taxon_concepts/index.html>

## Examples

``` r
if (FALSE) { # \dontrun{
# this calls will only work if a token is set and valid
res1 <- spp_taxonconcept(query_taxon = 'Loxodonta africana')
res2 <- spp_taxonconcept(query_taxon = 'Amazilia versicolor', raw = TRUE)
res3 <- spp_taxonconcept(query_taxon = '', taxonomy = 'CMS', pages = c(1, 3),
 language = 'EN', config = httr::progress())
res4 <- spp_taxonconcept(query_taxon = '', per_page = 20, pages = 44)
} # }
```
