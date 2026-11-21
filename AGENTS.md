# AGENTS.md

This repository, `lus-lang/atmos-session`, is the `session` package of the atmosphere registry. Programs load it with `require("https://atmosp.here/2.0/session.lus")`.

## Scope

Keeps per-client state for `web` applications behind a signed cookie. The public API is every function that `session.lus` returns in its module table. A change to that API needs a new entry in `CHANGELOG.md` and a version change in the header.

## Layout

- `session.lus` is the whole package. Its header doc comment carries the package metadata and the declared permissions.
- `tests/*_test.lus` are the tests. They load the package from the parent directory through `TEST_DIR`.

## Dependencies

- cookie, by its atmosphere URL
- web, for the plugin
- the stdlib `crypto` module, for identifiers and signatures

The tests load `cookie` from a checkout of `lus-lang/atmos-cookie` next to this repository, so clone it into the same parent directory first.

## Commands

```sh
lus test tests          # run the tests
lus check session.lus     # lint
lus doc session.lus       # print the reference
```

## Rules

- Every public function has a doc comment that states each result and each error, following `spec/design/style.md` of the Lus repository.
- The package never calls `pledge`. A new permission is declared in the header and in the README.
- Prose has no dashes and no semicolons, and never names the Roblox Lua dialect.
- Every bug fix comes with a test that fails without it.
