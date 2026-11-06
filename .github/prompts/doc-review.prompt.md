---
agent: 'agent'
description: 'This prompt is used to review a connector documentation page and make sure it meets the required standards and guidelines.'
---

Review this entire page without making any changes, based on the steps below.

**Completion gate:** Before evaluating the page, read all three sources listed below. Do not mark the review complete or state that the page meets the standards until you have read and applied all accessible guidance and performed every applicable check. If you cannot access or read a source, stop and report which source is unavailable; do not present the review as complete.

1. Fetch the markdown instructions from <https://docs.dataminer.services/contributing/CTB_Markdown_Syntax.html>.
1. Fetch the general house style instructions from <https://docs.dataminer.services/contributing/CTB_Docs_house_style.html>.
1. Fetch the repository-specific house style instructions from `.github/instructions/dataminer-docs-house-style.instructions.md`. Any contradictions with the general house style instructions should be resolved in favor of the repository-specific instructions.
1. Check if the page complies with the fetched instructions and guidelines.
1. Check if the file name contains no spaces. Spaces are not allowed in file names.
1. Check if all headings use title case.
1. Check if US English spelling and grammar are used consistently.
1. Check if the text is easily readable and consistent.
1. Check if there is an empty line between sections.
1. List any issues found, mentioning the exact line number when relevant, along with suggestions for correction.

Only list the issues you actually find. For items that are not applicable, do not mention them. If no issues are found, please state that the page meets all the required standards and guidelines.
