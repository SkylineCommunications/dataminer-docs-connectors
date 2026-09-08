---
description: "Guidelines for writing and structuring DataMiner connector documentation, ensuring consistency, clarity, and user-focused technical content."
applyTo: "**/*.md"
---

# DataMiner Connector Docs house style

When creating or editing connector documentation pages, apply the following rules.

## General

- Fetch the Markdown conventions from <https://docs.dataminer.services/contributing/CTB_Markdown_Syntax.html> and make sure these are followed.
- Fetch the house style instructions from <https://docs.dataminer.services/contributing/CTB_Docs_house_style.md> and make sure these are followed, except if this conflicts with the guidelines provided in this instructions file.
- Use title case in headers.
- Use a formal but simple technical style that helps users find information quickly.
- Address the reader directly as `you` and avoid third-person references to the user, unless describing a different user role (e.g., an operator).
- For cross-references to pages within this repository, use DocFX `xref` links instead of hard links to local Markdown files.
- Only use backticks for references to code, file paths, or user input, not for emphasis. File names (without file path) can also be written in italics.
- Use plain text in headers, avoiding italics, bold, and backticks.
- HTML comments must never be used.

## Procedure Formatting

- Write procedures as numbered lists.
- Use one logical action per numbered step.
- An exception to the above is procedures consisting of a single step, which do not require numbering.
- Keep instruction lines short and easy to scan.
- Put any additional information about a step in a separate, indented paragraph below that step.
- Put the result of a step in an indented paragraph below that step, and use future tense (e.g., "A new window will open" instead of "A new window opens").
- If a step contains an image, indent it correctly so list numbering does not restart.
- For complex procedures that include indented lines, place a blank line between each paragraph or list item. This prevents possible spacing issues.

## Alert Blocks

- Only use the following alert types: `> [!NOTE]`, `> [!TIP]`, `> [!IMPORTANT]`, `> [!CAUTION]`, and `> [!WARNING]`. No other alert type (e.g., `> [!ALERT]`) is supported. Before adding or editing an alert, verify the type against <https://docs.dataminer.services/contributing/CTB_Markdown_Syntax.html>.
- Never place two or more alert blocks of the same type directly after one another. Combine their content into a single alert block using a bulleted list instead.
- Avoid long alert blocks. If an alert block would be long, move its content to a regular text section instead.
- Avoid using a large number of alert blocks in the same section. If a more readable alternative exists, weave the content of some or all of the alerts into the regular text instead.
- Use `> [!CAUTION]` only for information about the possible negative consequences of an action.
- Use `> [!WARNING]` only for information about actions that could have far-reaching, dangerous consequences, such as breaking the DataMiner software.
- Use `> [!IMPORTANT]` for information a user must notice that has no direct negative or dangerous consequence.

## AI-Friendly Writing

- Use descriptive alt text for images.
- Ensure each page has a `description` value in its metadata/front matter, and ensure it is between 100 and 155 characters.
- Always make sure the text is structured logically, with meaningful headers that clearly indicate what each subsection is about.

## Punctuation

- Use single quotation marks in headers, as double quotation marks can cause formatting issues there.
- Use single quotation marks to indicate quoted material within a quotation (i.e., a nested quote); otherwise, use double quotation marks.
- Avoid em dashes on technical pages.
