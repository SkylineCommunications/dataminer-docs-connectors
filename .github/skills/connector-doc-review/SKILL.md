---
name: connector-doc-review
description: 'Use whenever the docs-review-assistant is asked to review, audit, or check a connector documentation page or section, including when the user says "review". Verify the page against the required DataMiner documentation standards and report actionable findings.'
---

# Connector Documentation Review

Use this workflow for every connector documentation review request. This skill is the single source of truth for review standards, workflow, constraints, and output.

## Review Procedure

1. Ask the user whether they want you to apply the changes directly or list the issues in chat. Use their answer to determine the output mode.
2. Before evaluating the page, retrieve and read all three sources:
   - Markdown instructions: <https://docs.dataminer.services/contributing/CTB_Markdown_Syntax.html>
   - General house style: <https://docs.dataminer.services/contributing/CTB_Docs_house_style.html>
   - Repository-specific house style: `.github/instructions/dataminer-docs-house-style.instructions.md`

   If the repository-specific instructions conflict with the general house style, follow the repository-specific instructions.
3. Read the entire target page or section, including its front matter, and check it against the sources and standards below.
4. Prioritize issues that affect readability, consistency, and navigation.
5. Follow the selected output mode:
   - To apply changes, edit only the relevant content and summarize the changes in a concise bullet list.
   - To list issues, report every issue found with its line number and a correction suggestion.

## Review Standards

- Use US English spelling and grammar consistently.
- Follow the Markdown conventions and house style in the three required sources. Do not invent repository conventions beyond those sources and the explicit checks below.
- Ensure the file name contains no spaces.
- Use title case in headings.
- Use descriptive alt text for images.
- Ensure the page metadata/front matter has a `description` value between 100 and 155 characters.
- Keep the tone formal, simple, and focused on quickly informing technical users. Avoid contractions and address the reader directly as `you` unless describing another user role.
- Ensure the content has a logical structure with meaningful headings.
- Ensure images in procedures are indented correctly so numbering does not restart.
- Ensure there is an empty line between sections.
- Use DocFX `xref` links for cross-references to pages in this repository.
- Follow repository Markdown conventions for formatting, procedure structure, alert blocks, and punctuation.

## Constraints

- Do not rewrite the whole page unless the user explicitly asks for a full rewrite.
- Keep feedback concise, actionable, and specific.
- Report only issues that are present. Do not mention checks that are not applicable.
- If a line number cannot be determined, say the location is approximate and reference the nearest heading.
- If no issues are found, state that the page meets all required standards and guidelines.

## Output Format

When listing issues, use this format:

- `Line <number>`: `<issue>`
  - `Suggestion:` `<how to correct it>`