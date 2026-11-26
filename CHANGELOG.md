# Changelog

## 1.0.0

**Release date:** TBD

Version 1.0.0 is the first release of `session`.

- Added the `session` package.
  - `session.register`: Registers the session plugin on a `web` scope, which gives every request a `req.session` table.
  - `session.memory`: Returns a store that keeps sessions in memory.
  - `session.regenerate`: Replaces the session identifier of a request with a new one and keeps the data.
  - `session.destroy`: Ends the session of a request.
  - `session.id`: Returns the session identifier of a request.
