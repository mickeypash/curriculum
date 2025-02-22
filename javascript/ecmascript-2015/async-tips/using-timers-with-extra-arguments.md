---
author: WebReflection
type: normal
category: must-know
tags:
  - introduction
  - workout
  - deep
links:
  - >-
    [W3C HTML5
    Timers](https://dev.w3.org/html5/spec-LC/timers.html#timers){documentation}
---

# Using timers with extra arguments


---

## Content

Both `setTimeout` and `setInterval` are a *W3C HTML5* specification, available as global methods in both client and server engines.

```plain-text
// signature for both methods
const uid = setTimeout(
  handler,    // Function
  optMsDelay, // usually a number
  ...optArgs  // any value
);
```

These methods allow authors to schedule timer-based callbacks.

```javascript
function chrono(start) {
  // same start value is passed each time
  // the scheduled interval runs
  console.log((Date.now() - start) / 1000);
}
let t = setInterval(chrono, 0, Date.now());
```

It is possible to cancel a scheduled interval or timeout using respectively `clearInterval` or `clearTimeout`

```plain-text
// to stop previous chronometer
clearInterval(t);
```

Please note this API does not guarantee that timers will fire exactly on schedule.

Delays due to CPU load, other tasks, etc, are to be expected.


---

## Practice

How to prevent the `shutdown` to happen?

```plain-text
let task = setTimeout(shutdown, 5000);
if (confirm('cancel shutdown?')) {
  ???
}
```

- `clearTimeout(task)`
- `task = null;`
- `delete task;`


---

## Revision

What log is shown each second?

```plain-text
let t = setInterval(
  (a, b) => {
    ++a;
    console.log(a + b);
    // ???
  },
  1000, // delay
  0,    // a
  10    // b
);
```

- `always 11`
- `10 then 11 then 12`
- `NaN`
- `11 then 12 then 13`
