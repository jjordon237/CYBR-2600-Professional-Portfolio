# Lessons Learned

1. **Separate delivery from completion.** A 200 response and attachment header do not guarantee a user-visible saved file.
2. **Use a control path.** A direct conversation link working against the same file helped isolate the viewer-specific behavior.
3. **Distinguish observations and hypotheses.** The evidence narrows possibilities without proving a frontend root cause.
4. **Avoid noisy correlations.** Other 403 errors, CSP warnings, and CSS issues were visible but not shown to cause the download failure.
5. **Protect evidence.** Crop/redact URLs, identifiers, tokens, and unrelated personal content before publishing.
6. **Document an operational workaround.** Direct links restored the ability to retrieve the file while the issue remained unresolved.
7. **Escalate accurately.** A reproducible functionality defect belongs in a support report; no security bounty claim is justified on this evidence alone.

## Portfolio reflection prompt
What did you initially suspect? Which network observations changed your hypothesis? What further evidence would be required before claiming root cause? Answer in your own words before publishing.
