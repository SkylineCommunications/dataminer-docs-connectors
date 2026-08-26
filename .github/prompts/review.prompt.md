---
agent: 'agent'
description: 'This prompt is used to review a connector documentation page and make sure it meets the required standards and guidelines.'
---

Can you review this page without making any changes, and list the line numbers where issues are found, along with your suggestion to correct them? If no line number can be determined, make sure the location can be found in a different manner.

Please check the following things:

- The file name must never contain a space, e.g., if a file is named "My file.md", it should be renamed to "My_File.md".
- US English must be used, with correct spelling and grammar.
- The text must be easily readable and consistent.
- There must be an empty line between sections.
- Use `e.g., ` and `i.e., ` must be used instead of `e.g. ` and `i.e. `.
- Title case must be used in headers.
- Descriptive alt text must be used for images.
- The reader must be addressed directly with `you`, avoiding third-person references to the user.
- For cross-references to pages within this repository, use DocFX `xref` links instead of hard links to local Markdown files.
- Use backticks for references to code, file paths, and user input, but not for emphasis.
- Do not place two note blocks immediately after one another. When that would occur, combine the content into a single note block that uses a bulleted list.

Only list the issues you actually find. For items that are not applicable, do not mention them. If no issues are found, please state that the page meets all the required standards and guidelines.
