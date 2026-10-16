# Root-Cause Analysis — Evidence and Hypotheses

**Root cause: NOT CONFIRMED.** This document is a hypothesis log, not a definitive RCA.

## Observed sequence
1. Viewer download button activated.
2. Download-related endpoint returned HTTP 200 and JSON metadata with `download_url`.
3. PDF content endpoint returned HTTP 200 and attachment headers.
4. Edge Downloads showed no entry for the attempted viewer download.
5. Direct conversation link downloaded successfully.

## Competing hypotheses
| Hypothesis | Supporting evidence | Missing test |
|---|---|---|
| Viewer does not complete browser save initiation | Valid API and PDF responses, no Downloads entry | Browser-side event / download initiation tracing |
| Browser policy blocks the viewer's save flow | No Downloads entry | Edge download policy, extension, and console correlation tests |
| Returned URL not followed as intended | JSON provides URL; save absent | Correlate exact subsequent request to the URL without exposing it |
| File corruption or missing file | Contradicted by successful direct download | None currently indicated |
| Unrelated 403s cause failure | No direct evidence | Request dependency tracing |

## Confidence statement
The evidence supports a failure in the **end-to-end viewer download workflow**, not a confirmed bug in any particular JavaScript function or service. HTTP 200 alone cannot prove that the intended browser save action completed.

## Suggested next tests
- Reproduce with a fresh Edge profile or InPrivate window if permitted.
- Test the viewer control in a second browser.
- Capture a tightly scoped Network trace and check whether the returned download URL is followed.
- Compare Edge Downloads and browser policies.
- Share sanitized evidence with product support.

## Security considerations
No security vulnerability was established. HTTP 403 responses indicate denied requests, not authorization bypass. Avoid testing other users' files or exposing tokens.
