# session

Keeps per-client state for `web` applications behind a signed cookie.

```lus nocheck
local web = require("https://atmosp.here/2.0/web.lus")
local session = require("https://atmosp.here/2.0/session.lus")

local app = web.app()
app:register(session, { secret = "a long random secret" })
app:post("/visit", function(req)
    req.session.visits = (req.session.visits or 0) + 1
    return { visits = req.session.visits }
end)
```

The package requires Lus 2.0. It declares no permissions. It calls no `pledge` of its own, so the program that loads it keeps control of its permissions.

The reference is in the doc comments of `session.lus`. Run `lus doc session.lus` to print it.
