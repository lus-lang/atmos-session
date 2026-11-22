# session

`session` keeps per-client state for `web` applications and identifies each client with a signed cookie.

The following example counts the visits of each client.

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

The package requires Lus 2.0 and declares no permissions. It never calls `pledge`, so the program that loads it keeps control of its permissions.

The reference is in the doc comments of `session.lus`, which `lus doc session.lus` prints.
