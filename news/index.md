# Changelog

## rcites 1.3.0

CRAN release: 2023-02-12

- [`set_token()`](https://docs.ropensci.org/rcites/reference/set_token.md)
  now keeps prompting a message as long as the token is an empty
  character string and it also indicates when a token might not be
  valid.
- Minor code reformatting throughout the code.
- Cassettes are now recorded in JSON (see
  [\#66](https://github.com/ropensci/rcites/issues/66)).

## rcites 1.2.0

CRAN release: 2021-11-04

- Default branch is now set to `main`.
- `synonyms` are properly formatted (see
  [\#65](https://github.com/ropensci/rcites/issues/65)).
- [`print()`](https://rdrr.io/r/base/print.html) methods are tested (see
  [\#57](https://github.com/ropensci/rcites/issues/57)).
- `curl::curl_escape(x)` is used to encode some URL parts (see
  [\#63](https://github.com/ropensci/rcites/issues/63)).
- Consistently uses [`message()`](https://rdrr.io/r/base/message.html)
  for console (see
  [\#60](https://github.com/ropensci/rcites/issues/60)).
- Vignettes are not precomputed (see
  [\#58](https://github.com/ropensci/rcites/issues/58)).
- Tests now uses `vcr` (now listed in `Suggests`, see
  [\#56](https://github.com/ropensci/rcites/issues/56)).
- Classes are now tested properly (see
  [\#54](https://github.com/ropensci/rcites/issues/54)).
- `rcites_res()` gains arguments `verbose` and `raw` (see
  [\#43](https://github.com/ropensci/rcites/issues/43) and
  [\#62](https://github.com/ropensci/rcites/issues/62)).
- Request status now are reported by `warn_for_status()` rather than by
  `stop_for_status()`, this prevents fast-failing in batch mode (see
  [\#62](https://github.com/ropensci/rcites/issues/62)).

## rcites 1.1.0

CRAN release: 2020-07-01

- Internal function `rcites_simplify_distributions()` has been
  re-written to fix a bug that made
  [`spp_distributions()`](https://docs.ropensci.org/rcites/reference/spp_distributions.md)
  throw an error for `taxon_id` with only one distribution entry (see
  [\#53](https://github.com/ropensci/rcites/issues/53)).
- `spp_*()` functions gain an argument `pause` (see
  [\#50](https://github.com/ropensci/rcites/issues/50) and
  [\#51](https://github.com/ropensci/rcites/issues/51) following the
  issue reported by [@fleurhierink](https://github.com/fleurhierink) in
  [\#49](https://github.com/ropensci/rcites/issues/49)).
- Minor text editions through the documentation.
- Return an empty data frame when there is no listing available for a
  given species (fix
  [\#47](https://github.com/ropensci/rcites/issues/47) reported by
  [@eveskew](https://github.com/eveskew)).

## rcites 1.0.1

CRAN release: 2019-05-24

#### New features 🎨

- rcites now imports [cli](https://github.com/r-lib/cli) 📦 to:
  1.  clarify notes reported when downloading material;
  2.  color titles in the default print methods.

#### Bugs fixed 🐛

- Fix a bug that prevented
  [`spp_taxonconcept()`](https://docs.ropensci.org/rcites/reference/spp_taxonconcept.md)
  from downloading all the taxon concepts, see
  [\#42](https://github.com/ropensci/rcites/issues/42).

- Fix a bug that generated infinte recursion error when using
  non-interactively without token, see
  [\#44](https://github.com/ropensci/rcites/issues/44).

## rcites 1.0.0

CRAN release: 2018-11-17

#### New features 🎨

- [`spp_taxonconcept()`](https://docs.ropensci.org/rcites/reference/spp_taxonconcept.md)
  now includes an auto-pagination that allows to retrieve all entries
  for queries that have more than 500 results;
- [`spp_taxonconcept()`](https://docs.ropensci.org/rcites/reference/spp_taxonconcept.md),
  [`spp_eu_legislation()`](https://docs.ropensci.org/rcites/reference/spp_eu_legislation.md),
  [`spp_cites_legislation()`](https://docs.ropensci.org/rcites/reference/spp_cites_legislation.md)
  and
  [`spp_references()`](https://docs.ropensci.org/rcites/reference/spp_references.md)
  now supports vectors as `taxon_id` argument which allows bulk
  analysis.
- Functions `spp_*` now returns S3 objects:
  - [`spp_taxonconcept()`](https://docs.ropensci.org/rcites/reference/spp_taxonconcept.md)
    returns an object of class `spp_taxon`;
  - [`spp_cites_legislation()`](https://docs.ropensci.org/rcites/reference/spp_cites_legislation.md)
    returns an object of class `spp_cites_leg` or `spp_cites_leg_multi`;
  - [`spp_eu_legislation()`](https://docs.ropensci.org/rcites/reference/spp_eu_legislation.md)
    returns an object of class `spp_eu_leg` or `spp_eu_leg_multi`;
  - [`spp_distributions()`](https://docs.ropensci.org/rcites/reference/spp_distributions.md)
    returns an object of class `spp_distr` or `spp_distr_multi`;
  - [`spp_references()`](https://docs.ropensci.org/rcites/reference/spp_references.md)
    returns an object of class `spp_refs` or `spp_refs_multi`;
- Moreover:
  - `spp_raw` class is defined for all functions including the argument
    `raw`, it returns the parsed output from the API as a list object.

#### New function arguments

- `taxonomy`, `with_descendants`, `language`, `updated_since`,
  `per_page`, `seq_page`, `raw`, `verbose` in
  [`spp_taxonconcept()`](https://docs.ropensci.org/rcites/reference/spp_taxonconcept.md);
- `scope`, `language` and `raw` to
  [`spp_cites_legislation()`](https://docs.ropensci.org/rcites/reference/spp_cites_legislation.md);
- `scope`, `language` and `raw` to
  [`spp_eu_legislation()`](https://docs.ropensci.org/rcites/reference/spp_eu_legislation.md);
- `language` and `raw` to
  [`spp_distributions()`](https://docs.ropensci.org/rcites/reference/spp_distributions.md).

#### Function renamed

- [`set_token()`](https://docs.ropensci.org/rcites/reference/set_token.md)
  instead of `sppplus_login()`;
- [`spp_taxonconcept()`](https://docs.ropensci.org/rcites/reference/spp_taxonconcept.md)
  instead of `sppplus_taxonconcept()`;
- [`spp_cites_legislation()`](https://docs.ropensci.org/rcites/reference/spp_cites_legislation.md)
  instead of `taxon_cites_legislation()`;
- [`spp_eu_legislation()`](https://docs.ropensci.org/rcites/reference/spp_eu_legislation.md)
  instead of `taxon_eu_legislation()`;
- [`spp_distributions()`](https://docs.ropensci.org/rcites/reference/spp_distributions.md)
  instead of `taxon_distribution()`;
- [`spp_references()`](https://docs.ropensci.org/rcites/reference/spp_references.md)
  instead of `taxon_references()`;
- `rcites_simplify()` instead of `sppplus_simplify()`;
- `rcites_` instead of `sppplus_` for helper functions.

#### Using [goodpractice](https://github.com/MangoTheCat/goodpractice)

- use ‘\<-’ for assignment instead of ‘=’,
- omit “Date” in DESCRIPTION,
- avoid `1:length(...)`, `1:nrow(...)`, `1:ncol(...)`.

## rcites 0.1.0

CRAN release: 2018-08-11

#### NB: this was the first release 1️⃣

#### Features 🎨

- spp_taxonconcept( ): [access the Speciesplus taxon
  concept](https://api.speciesplus.net/documentation/v1/taxon_concepts/index.html)
- spp_cites_legislation( ): [access CITES legislation
  data](https://api.speciesplus.net/documentation/v1/cites_legislation/index.html)
- spp_eu_legislation( ): [access EU legislation
  data](https://api.speciesplus.net/documentation/v1/eu_legislation/index.html)
- spp_distributions( ): [access a taxon distribution
  data](https://api.speciesplus.net/documentation/v1/distributions/index.html)
- spp_references( ): [access a listing reference
  data](https://api.speciesplus.net/documentation/v1/references/index.html)
