# Contributing to CHIKVnext

Thank you for your interest in contributing to the CHIKVnext project! This document provides guidelines for contributing to this Nextstrain community build.

## How to Contribute

### Reporting Issues

If you encounter any issues or have questions about the build:

1. Check existing [issues](https://github.com/ViennaRNA/CHIKV/issues) to see if your concern has already been addressed
2. If not, open a new issue with:
   - A clear, descriptive title
   - Detailed description of the issue or question
   - Any relevant context (e.g., which version of the build, what you were trying to do)

### Suggesting Enhancements

We welcome suggestions for improving the build! To suggest an enhancement:

1. Open an issue with the tag "enhancement"
2. Describe the enhancement and why it would be valuable
3. If possible, provide examples or references

### Contributing Data

If you have CHIKV sequence data that you would like to see included in future builds:

1. Ensure your sequences are deposited in [NCBI GenBank](https://www.ncbi.nlm.nih.gov/genbank/)
2. Open an issue to notify us of the new sequences
3. Provide accession numbers and any relevant metadata

### Contributing Code or Analysis

If you would like to contribute to the build workflow or analysis:

1. Fork the repository
2. Create a new branch for your feature
3. Make your changes
4. Submit a pull request with:
   - Clear description of the changes
   - Rationale for the changes
   - Any relevant tests or validation

## Getting Help

### Build Process Questions

If you need help understanding or reproducing the build:

- Review the [BUILD.md](BUILD.md) documentation
- Check the [Nextstrain documentation](https://docs.nextstrain.org/)
- Post in the [Nextstrain discussion forum](https://discussion.nextstrain.org/)
- Open an issue in this repository

### Scientific Questions

For questions about the scientific interpretation of results or CHIKV biology:

- Refer to the [publications](README.md#citation) associated with this work
- Consider reaching out to the authors directly

### Technical Support

For technical issues with Nextstrain tools (Augur, Auspice):

- Visit the [Nextstrain documentation](https://docs.nextstrain.org/)
- Search the [Nextstrain discussion forum](https://discussion.nextstrain.org/)
- Check the GitHub repositories for [Augur](https://github.com/nextstrain/augur) and [Auspice](https://github.com/nextstrain/auspice)

## Development Workflow

### Setting Up Your Environment

1. Fork and clone the repository:
   ```bash
   git clone https://github.com/YOUR-USERNAME/CHIKV.git
   cd CHIKV
   ```

2. Install Nextstrain dependencies (see [BUILD.md](BUILD.md#dependencies))

3. Create a branch for your work:
   ```bash
   git checkout -b feature/your-feature-name
   ```

### Making Changes

1. Make your changes following the existing code style
2. Test your changes thoroughly
3. Update documentation as needed

### Submitting Changes

1. Commit your changes with clear, descriptive commit messages:
   ```bash
   git commit -m "Add feature: description of what changed"
   ```

2. Push to your fork:
   ```bash
   git push origin feature/your-feature-name
   ```

3. Open a pull request on GitHub

## Code of Conduct

Please note that this project follows standard open-source community guidelines:

- Be respectful and inclusive
- Provide constructive feedback
- Focus on what is best for the community
- Show empathy towards other community members

## Questions?

If you have questions about contributing that aren't covered here, please open an issue or contact the maintainers.

## Acknowledgments

This project builds on the work of many contributors in the Nextstrain community and CHIKV researchers worldwide. We gratefully acknowledge:

- The [Nextstrain team](https://nextstrain.org/team) for creating and maintaining the platform
- Researchers who have shared CHIKV genome sequences publicly
- Contributors to the scientific publications associated with this work

## License

By contributing to this project, you agree that your contributions will be made available under the same license terms as the rest of the project.
