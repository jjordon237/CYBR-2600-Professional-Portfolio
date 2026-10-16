# Evidence Index

These are **cropped, partially redacted** captures from the October 16, 2026 Edge Developer Tools investigation. Before publishing, inspect every screenshot at full resolution for residual account identifiers, session data, and private URLs.

| File | Purpose | Interpretation |
|---|---|---|
| `01-network-successful-requests.png` | Network request list | Download-related and content requests show successful statuses |
| `02-download-json-metadata.png` | Download API response | Shows JSON property names and PDF metadata; URL and identifier masked |
| `03-pdf-response-headers.png` | PDF content response headers | Shows `Content-Type: application/pdf` and `Content-Disposition: attachment` |

**Not pictured:** Edge Downloads panel had no corresponding item after viewer button click, as observed during the test. This is a documented observation, not a screenshot-backed claim.

The screenshots are supporting evidence, not proof of an exact software root cause. Do not publish raw HAR exports or authorization headers.
