---
agent: 'agent'
description: 'This prompt is used to review a connector documentation page and make sure it meets the required standards and guidelines.'
---

Can you review this page without making any changes, and list the line numbers where issues are found, along with your suggestion to correct them? If no line number can be determined, make sure the location can be found in a different manner.

Follow all instructions in `.github/instructions/dataminer-docs-house-style.instructions.md` in addition to the checks below.

Please check the following things:

- The file name must never contain a space, e.g., if a file is named "My file.md", it should be renamed to "My_File.md".
- US English must be used, with correct spelling and grammar.
- The text must be easily readable and consistent.
- There must be an empty line between sections.

Only list the issues you actually find. For items that are not applicable, do not mention them. If no issues are found, please state that the page meets all the required standards and guidelines.
