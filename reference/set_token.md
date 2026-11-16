# Login helper function

Set and forget the authentification token for the current session.

## Usage

``` r
set_token(token = NULL)

forget_token()
```

## Arguments

- token:

  a character string (with quotes) containing your token. If `NULL`,
  then the token can be passed without quotes (not as a character
  string) after a prompt.

## Functions

- `set_token()`: set the environment variable `SPECIESPLUS_TOKEN`.

- `forget_token()`: forget the environment variable `SPECIESPLUS_TOKEN`.

## References

<https://api.speciesplus.net/documentation>

## Examples

``` r
if (FALSE) { # \dontrun{
# NB: the token below is not working and should not be used
set_token("8QW6Qgh57sBG2k0gtt")
} # }
```
