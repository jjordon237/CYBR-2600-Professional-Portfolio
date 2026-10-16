# ChatGPT PDF Viewer Download Failure — Browser Network Investigation

**Type:** Web application troubleshooting case study  
**Date:** October 16, 2026  
**Environment:** Microsoft Edge on Windows; ChatGPT web application  
**Outcome:** Reproducible viewer download failure; direct conversation-link workaround confirmed; underlying root cause **not established**.

## Executive summary
A PDF generated in ChatGPT could be downloaded from a direct link in the conversation, but clicking the download control inside the document viewer did not create an entry in Edge Downloads. Browser Developer Tools were used to compare requests and response metadata. The download-related API returned HTTP 200 with JSON containing a `download_url`; a PDF content request returned HTTP 200 with `Content-Type: application/pdf` and `Content-Disposition: attachment`. Despite those successful responses, the viewer control did not result in a browser download. The discrepancy points to a possible issue in the client-side download workflow, but browser policy and other causes have not been excluded.

## Objective and scope
Determine whether the failure was attributable to a missing/corrupt PDF, failed HTTP request, or a later step in the browser download workflow. Testing was limited to the investigator's own generated file and ordinary browser diagnostics. No authorization bypass or third-party file access was attempted.

## Method
1. Reproduce the failure with the PDF viewer download control.
2. Verify the same PDF downloads through a direct conversation link.
3. Open Edge Developer Tools → Network; enable recording, **Keep log**, and **Disable cache**.
4. Observe the `download?download_intent=...` response and inspect its JSON property names.
5. Observe the `content?id=file_...` response and inspect its status and headers.
6. Check Edge Downloads (Ctrl+J) after using the viewer button.
7. Separate unrelated console errors from evidence directly linked to the download.

## Verified observations
| Observation | Result |
|---|---|
| Viewer download control | Did not produce a visible saved download |
| Edge Downloads after viewer click | No corresponding entry |
| Direct Markdown conversation link | Download succeeded |
| Download-related API response | HTTP 200; JSON with `download_url` and file metadata |
| PDF content response | HTTP 200; `application/pdf` |
| PDF content-disposition | `attachment` with matching filename |
| Unrelated console requests | Some HTTP 403 responses; causal connection unproven |

## Interpretation and limits
Successful network responses support that the file was available and that the server returned download metadata and PDF content. They **do not prove** the browser completed the save operation or establish exactly which component failed. A frontend download initiation issue is a working hypothesis, not a confirmed root cause. The observed 403 console messages and accessibility/CSP warnings should not be described as the cause without further evidence.

## Workaround
Use a direct Markdown link to the generated file in the conversation rather than the viewer's download control.

## Evidence
See [`evidence/README.md`](evidence/README.md). Screenshots are cropped/redacted for public sharing; review them again before publication.

## Professional relevance
Demonstrates controlled reproduction, browser network inspection, HTTP status and header interpretation, evidence preservation, hypothesis management, and honest reporting of uncertainty. This is an **application troubleshooting case**, not a confirmed security incident, exploit, or vulnerability disclosure.

## Related documents
- [`incident-report.md`](incident-report.md)
- [`root-cause-analysis.md`](root-cause-analysis.md)
- [`lessons-learned.md`](lessons-learned.md)

## Authorship and AI disclosure
The investigator performed the browser tests and supplied screenshots. ChatGPT assisted in organizing and drafting this case study based on those observations. Verify the screenshots and wording before publishing; no tool execution or network test is claimed beyond the documented actions.
