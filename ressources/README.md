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
- Specify the size of your timeframe you are willing to accept via `setTimeFrameMS(yourMS)`
- Use it to create a validatabletimestamp via `create()`
- Use it to validate said timestamp via `assertValidity(stamp)`
  
```coffee
import { setTimeFrameMS, create, assertValidity } from "validatabletimestamp"

# setting the timeFrame to 20s - default is 180s
setTimeFrameMS(20000)

# create the timestamp
stamp = create()

# validate it - definitely is fine here
assertValidity(stamp)

## wait 20s

# validate it - also should be fine here
assertValidity(stamp)

## wait 20s

# validate it - now throws "Invalid Timestamp!"
assertValidity(stamp)


```

---

# Further steps

- Waiting for ideas on improvement


All sorts of inputs are welcome, thanks!

---

# License
[Unlicense JhonnyJason style](https://hackmd.io/nCpLO3gxRlSmKVG3Zxy2hA?view)