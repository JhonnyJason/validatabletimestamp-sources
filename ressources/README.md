# validatabletimestamp 

# Background
Very frequently we have the situation that we want to validate a unix timestamp.
Validating here means that it is recognizable as being within an accepted timeFrame.

Therefore we need to round it to such a specific (definable) timeFrame, and accept some inaccurracy.
Here we accept the next and the previous timeFrame as well.

This package does exactly this.

# Usage

Requirements
------------
- ESM importability

Installation
------------
Current git version:
```
npm install git+https://github.com/JhonnyJason/validatabletimestamp-output.git
```

Npm Registry
```
npm install validatabletimestamp
```

Use
-----------
- Specify the size of your timeframe you are willing to accept via `setTimeFrameMS(yourMS)` -> If you set this, make sure that you do this on both sides to keep compatibility. A reasonable default is 180s = 3m
- Use it to create a validatabletimestamp via `create()`
- Use it to validate said timestamp via `checkValidity(stamp)` or `assertValidity(stamp)`
- Be aware: `checkValidity(stamp)` returns falsy when being valid and the truly string `"invalid"` when being invalid
- Be aware: `assertValidity(stamp)` throws an error when being invalid
  
```coffee
import { setTimeFrameMS, create, checkValidity, assertValidity } from "validatabletimestamp"

# setting the timeFrame to 20s - default is 180s
setTimeFrameMS(20000)

# create the timestamp
stamp = create()

# err should be undefined here
err = checkValidity(stamp)
# validate it - definitely is fine here
assertValidity(stamp)


## wait 20s

# err should still be undefined here
err = checkValidity(stamp)
# validate it - also should be fine here
assertValidity(stamp)


## wait 20s

# err should be "invalid" now
err = checkValidity(stamp)
# validate it - now throws "Invalid Timestamp!"
assertValidity(stamp)


```

---

# Further steps

- Waiting for ideas on improvement


All sorts of inputs are welcome, thanks!

---

# License
[CC0](https://creativecommons.org/publicdomain/zero/1.0/)