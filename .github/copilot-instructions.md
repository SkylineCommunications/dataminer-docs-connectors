# DataMiner Docs Connectors Repository

This is a documentation-only repository containing documentation related to specific DataMiner connectors. It uses Docfx format with YAML TOC files.

## Repository Structure

The main documentation folder in this repository is the `connector` folder. Its `doc` subfolder contains all documentation for the different DataMiner connectors. The `images` subfolder contains the images for this documentation.

### File Patterns

- All content files use `.md` format with YAML front matter.
- TOC files use `.yml` format with a specific structure for defining the table of contents.
- Content files require `uid:` in front matter for cross-referencing. This is followed by a unique identifier that must not contain any spaces. Ideally, the unique identifier is identical to the file name, preceded by `Connector_help_`.
- Standard format:

  ```md
  ---
  uid: Connector_help_File_Name
  ---
  
  # Title
  
  Content...
  ```

## Key Guidelines

1. Each `connector/doc/**/*.md` file must have proper front matter including a unique `uid`.
2. Each `connector/doc/**/*.md` file must have a corresponding entry in the appropriate `toc.yml` file using the matching `topicUid`. The same file must never be added to more than one `toc.yml` file.
3. Do not use spaces in file and folder names.
4. One `connector/doc/**/*.md` file must never contain more than 64000 characters.
5. If changes are implemented that remove all references to a specific image, that image must be removed.
6. Ensure that all cross-references are accurate and up to date.
7. Follow the house style defined in `.github/instructions/dataminer-docs-house-style.instructions.md`.
