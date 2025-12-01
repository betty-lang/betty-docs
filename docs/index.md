---
hide:
    - navigation
    - toc
---

Welcome to the Betty programming language documentation. Explore the language through examples, or dive into the comprehensive reference and understand the technical foundations.

!!!warning
    This documentation is still a work in progress and may not cover all language features yet. Please check back for future updates!

<div class="grid cards" markdown>

- :material-lightbulb-on: [__Examples__](examples/index.md)

    ---

    Practical examples demonstrating Betty's features and capabilities, from basic syntax to advanced programming concepts.

- :material-book-open-variant: [__Reference__](reference/index.md)

    ---

    Comprehensive documentation of Betty's syntax, keywords, data types, and standard library functions.

</div>

## Getting Started

### Download Pre-built Binaries

Betty now has automated releases with pre-built binaries for Windows, macOS, and Linux!

**[Download the latest release](https://github.com/betty-lang/betty/releases/latest)** :material-download:

Choose the appropriate binary for your platform:

- **Windows**: `betty-windows-x64.zip`
- **Linux**: `betty-linux-x64.tar.gz`
- **macOS (Intel)**: `betty-macos-x64.tar.gz`
- **macOS (Apple Silicon)**: `betty-macos-arm64.tar.gz`

Extract the archive and add the executable to your PATH.

### Build from Source

Alternatively, you can clone the repo and build the binaries yourself:

```bash
git clone https://github.com/betty-lang/betty.git
cd betty
dotnet build Betty.sln --configuration Release
```