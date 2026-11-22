# AGENTS.md

`lus-lang/atmos-session` is the repository of the `session` package of the atmosphere registry. Programs load the package with `require("https://atmosp.here/2.0/session.lus")`.

## Scope

`session` keeps per-client state for `web` applications and identifies each client with a signed cookie. The public API is every function that `session.lus` returns in its module table. A change to that API needs a new entry in `CHANGELOG.md` and a version change in the header.

## Layout

- `session.lus` is the whole package. Its header doc comment contains the package metadata and the declared permissions.
- `tests/*_test.lus` are the tests. They load `session.lus` from the parent of `TEST_DIR`, the directory that holds the test file.

## Dependencies

- `cookie`, which `session.lus` loads by its atmosphere URL
- `web`, for the plugin
- the standard library `crypto` module, for identifiers and signatures

The tests load `cookie` from a checkout of `lus-lang/atmos-cookie` next to this repository, so clone it into the same parent directory first.

## Commands

Run these commands from the root of the repository.

```sh
lus test tests          # run the tests
lus check session.lus     # lint
lus doc session.lus       # print the reference
```

## Rules

- Every public function has a doc comment that states each result and each error, following `spec/design/style.md` of the Lus repository.
- The package never calls `pledge`. A new permission is declared in the header and in the README.
- Prose follows the `lus-writing` skill, which `lus agents init` installs and https://lus.dev/agents/skills/lus-writing/SKILL.md serves. In particular, prose has no dashes or semicolons and never names the Roblox Lua dialect.
- Every bug fix comes with a test that fails without it.
