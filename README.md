# Haskell iexcloud client

# This project is based on the legacy iex API client [stocks](https://github.com/dabcoder/stocks)

[![Build Status](https://travis-ci.org/dabcoder/stocks.svg?branch=master)](https://travis-ci.org/dabcoder/stocks)

Haskell library for the IEX trading API.

Example:

```haskell
stack build && stack ghci

getQuote :: AuthAndSymbol -> IO (Maybe IEXQuote.Quote)
> getQuote ("pk_myAPItoken", "msft")

Just (Quote {symbol = "MSFT",
             companyName = "Microsoft Corp.",
             primaryExchange = Nothing,
             sector = Nothing,
             calculationPrice = "tops",
             open = 128.9,
             ...
             })

getCompany :: AuthAndSymbol -> IO (Maybe IEXCompany.Company)
> getCompany ("pk_myAPItoken", "aapl")

Just (Company {symbol = "AAPL",
               companyName = "Apple Inc.",
               exchange = "Nasdaq Global Select",
               industry = "Computer Hardware",
               website = "http://www.apple.com",
               description = "Apple Inc is designs ...",
               ceo = "Timothy D. Cook",
               issueType = "cs",
               sector = "Technology"})

getPrice :: AuthAndSymbol -> IO (Maybe Double)
> getPrice ("pk_myAPItoken", "msft")

Just 131.56
```

Please see the HUnit test for a complete example
of all API calls.

## How to run test suite
```
stack test
```

## Contribute

For any problems, comments, or feedback please create an
issue [here on GitHub](https://github.com/dabcoder/stocks/issues).

### Attribution
If you redistribute our API data:

* Cite IEX using the following text and link: “Data provided for free by [IEX](https://iextrading.com/developer).”
* Provide a link to https://iextrading.com/api-exhibit-a in your terms of service.

# Before uploading to hackage

* Make sure that all dependencies in 'iexcloud.cabal' are version bound. Also:

1. Hackage is intended to be a permanent record.  Therefore uploads cannot be changed or removed.
2. Only upload things that work, are useful to other people, and that you intend to maintain.
3. Use `cabal gen-bounds` to put PVP-compliant version bounds (lower AND upper) on ALL your unique dependencies so your package will still be buildable years down the road.  One important thing to note is that you only need to include version bounds once.  For example, if you depend on the same package in your library and your test suite, you only need to put the version bounds for that dependency in one place.  This keeps the dependency bounds information DRY.
4. Package candidates CAN be changed, so use them to test things out and get everything right before you publish permanently to the main index.
