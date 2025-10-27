# Contributing to Awesome A2A

First off, thank you for considering contributing! Your help is essential for keeping this list valuable and up-to-date for the community interested in the Agent2Agent (A2A) Protocol. 🎉

This document provides guidelines for contributing to this list.

## Table of Contents

*   [Code of Conduct](#code-of-conduct)
*   [How Can I Contribute?](#how-can-i-contribute)
    *   [Suggesting Resources](#suggesting-resources)
    *   [Adding Resources (Pull Requests)](#adding-resources-pull-requests)
    *   [Reporting Issues](#reporting-issues)
*   [Contribution Guidelines](#contribution-guidelines)
    *   [What to Add](#what-to-add)
    *   [Quality Standards](#quality-standards)
    *   [Formatting](#formatting)
*   [Pull Request Process](#pull-request-process)
*   [Language Considerations (English & Chinese)](#language-considerations-english--chinese)
*   [Questions?](#questions)

## Code of Conduct

This project and everyone participating in it are governed by the [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior.

## How Can I Contribute?

There are several ways you can contribute:

### Suggesting Resources

*   If you find a great A2A-related resource but don't want to create a Pull Request yourself, feel free to [open an Issue](https://github.com/ai-boost/awesome-a2a/issues/new?assignees=&labels=suggestion&template=resource-suggestion.md&title=Suggest%3A+%5BResource+Name%5D) suggesting it. Please provide the link and a brief description.

### Adding Resources (Pull Requests)

*   This is the preferred method! If you want to add a resource directly, please follow the [Pull Request Process](#pull-request-process) outlined below. Ensure your addition meets the [Contribution Guidelines](#contribution-guidelines).

### Reporting Issues

*   Found a broken link? Is a description inaccurate or misleading? Please [open an Issue](https://github.com/ai-boost/awesome-a2a/issues/new?assignees=&labels=bug%2C+maintenance&template=bug_report.md&title=Fix%3A+%5BBrief+Description%5D) to report it.
*   Have ideas for new sections or improvements to the list structure? Open an Issue to discuss!

## Contribution Guidelines

### What to Add

We are looking for resources specifically related to the **Google Agent2Agent (A2A) Protocol**. This includes:

*   **Implementations:** Server or client libraries in various languages/frameworks.
*   **Tools:** Validation tools, discovery services, monitoring adapters, etc.
*   **Tutorials & Articles:** Blog posts, guides, conceptual explanations focused on A2A.
*   **Demos & Examples:** Working applications or code snippets showcasing A2A features.
*   **Framework Integrations:** How specific AI/Agent frameworks support or integrate with A2A.
*   **Related Protocols:** Directly complementary protocols (like MCP) with clear explanations of their relation to A2A.

**Please do NOT add:**

*   General AI/Agent resources not specifically mentioning or using A2A.
*   Vague or overly broad links.
*   Broken links or resources that are no longer maintained/relevant.
*   Promotional content disguised as a resource.

### Quality Standards

*   **Relevance:** The resource must be directly related to the A2A protocol.
*   **Value:** It should provide useful information, code, or tools for someone learning or working with A2A.
*   **Maintenance:** Links should work, and code repositories should ideally show signs of recent activity or be considered stable/complete.
*   **Clarity:** Descriptions should be clear, concise, and accurate.

### Formatting

*   Use the following format for list items:
    ```markdown
    *   🔗/📄/⚙️/etc. [Resource Title](link-to-resource) - A brief, informative description (usually one sentence). Keep it objective.
    ```
*   Choose an appropriate emoji to start the line (use existing ones as a guide).
*   Ensure the link is direct and works correctly.
*   Add the item to the **most relevant section** in the README.
*   Within a section, you can add new items to the end, or maintain alphabetical order if you prefer (not strictly enforced, but appreciated).
*   Check your spelling and grammar.

## Commit Message Guidelines

We use a standardized commit message format to keep the project history clean and readable:

### Format

```
[Emoji] [Action] [Object]
```

### Examples

*   ✨ Add new A2A implementation in Rust
*   🐛 Fix broken link to official documentation
*   📝 Update README with new community tool
*   🌐 Add Japanese translation for getting started guide

### Using the Commit Template (Optional)

To use the provided commit message template:

```bash
git config commit.template .gitmessage
```

After this, running `git commit` (without `-m`) will open your editor with helpful examples and emoji references.

### Common Emojis

*   ✨ `:sparkles:` - New resource/implementation/tool
*   🐛 `:bug:` - Fix broken links/incorrect info
*   📝 `:memo:` - Documentation updates
*   🌐 `:globe_with_meridians:` - Translations/i18n
*   🔗 `:link:` - Update links/references
*   📦 `:package:` - Add SDKs/libraries
*   🎨 `:art:` - Formatting/structure improvements
*   🔥 `:fire:` - Remove outdated resources

See `.gitmessage` for the full list of recommended emojis.

## Pull Request Process

1.  **Fork the repository:** Click the "Fork" button on the [awesome-a2a repository page](https://github.com/ai-boost/awesome-a2a).
2.  **Clone your fork:** `git clone https://github.com/YOUR_FORK_USERNAME/awesome-a2a.git`
3.  **Create a new branch:** `git checkout -b add-my-awesome-resource` (use a descriptive branch name).
4.  **Make your changes:**
    *   Add your link(s) to the relevant section(s) in `README.md` following the [Formatting](#formatting) guidelines.
    *   **Crucially, also add the corresponding entry to `README_zh.md`** (see [Language Considerations](#language-considerations-english--chinese)).
5.  **Commit your changes:** Follow the [Commit Message Guidelines](#commit-message-guidelines) above. Example: `git commit -am '✨ Add: Resource Title to [Section Name]'`
6.  **Push to your fork:** `git push origin add-my-awesome-resource`
7.  **Open a Pull Request:** Go to the original `awesome-a2a` repository on GitHub and click the "New pull request" button. Ensure the base repository is the original and the head repository is your fork/branch.
8.  **Describe your PR:** Explain what you've added and why it's relevant. Link to an Issue if applicable.
9.  **Wait for review:** Maintainers will review your PR, provide feedback if needed, and merge it if everything looks good.

## Language Considerations (English & Chinese)

This repository aims to maintain parallel content in English (`README.md`) and Simplified Chinese (`README_zh.md`).

*   **When adding a new resource:** Please add the entry to **both** `README.md` and `README_zh.md`.
    *   Keep the resource title and link the same in both files.
    *   Provide an appropriate, concise description in both English and Chinese.
*   **If you can only provide one language:** That's okay too! Please add the entry to the relevant language file and make a note in your Pull Request description (e.g., "Added entry to English README, needs Chinese translation"). Maintainers or other contributors can help with the translation.
*   **When fixing links or typos:** Please try to fix them in both files if applicable.

## Questions?

If you have questions about the contribution process or whether a resource is suitable, feel free to [open an Issue](https://github.com/ai-boost/awesome-a2a/issues) with the label `question`.

---

Thank you for contributing! ❤️
