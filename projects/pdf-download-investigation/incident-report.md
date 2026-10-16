# Incident-style Troubleshooting Report

**Case ID:** WEB-PDF-2026-10-16  
**Classification:** Application functionality defect / user-facing download failure  
**Status:** Reproduced; workaround identified; root cause unresolved

## Problem statement
The ChatGPT PDF viewer's download control did not save a generated PDF. A direct link to the same file in the conversation worked.

## Environment and prerequisites
Microsoft Edge on Windows; user-generated PDF in ChatGPT; browser Developer Tools Network and Console panels.

## Reproduction procedure
1. Open the generated PDF in the viewer.
2. Start recording in Edge Network; optionally clear existing entries.
3. Enable Keep log and Disable cache.
4. Click the viewer download control once.
5. Inspect requests named `download?download_intent=...` and `content?id=file_...`.
6. Open Edge Downloads with Ctrl+J.
7. Try the direct conversation download link as a control test.

## Actual versus expected
**Expected:** Viewer button initiates an Edge download for the PDF.  
**Actual:** No corresponding item appears in Edge Downloads, while the direct link succeeds.

## Technical evidence
- Download API: HTTP 200, JSON with `download_url` and PDF metadata.
- Content request: HTTP 200, `Content-Type: application/pdf`, `Content-Disposition: attachment`.
- Some other requests showed 403 Forbidden, but no causal relationship to the PDF failure was demonstrated.

## Impact
User cannot reliably retrieve generated documents through the viewer, increasing friction and requiring alternative links.

## Mitigation
Provide a direct Markdown sandbox link to the file in the conversation.

## Escalation recommendation
Submit sanitized screenshots and reproduction steps to OpenAI Support. Do not include raw authenticated URLs, cookies, authorization headers, or session identifiers. No internal support ticket was submitted by the authoring assistant.
