---
layout: default
title: Using Markdown for Code Snippets
nav_order: 7
parent: Forum Help
---

# Using Markdown for Code Snippets
{: .no_toc }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}


To display code directly in your post, use Discourse's Markdown syntax:

### Inline Code

To format a short piece of code inline with your text, just wrap the code with single backticks (\`).

For example:

Use the `print()` function to display output.

<img src="../assets/images/forum/inline_code_example.png" alt="inline code example screenshot" width="60%">


### Code Blocks

For larger code blocks, use triple backticks (\`\`\`) before and after the code.

For example:


<img src="../assets/images/forum/code_blocks_example.png" alt="code blocks example screenshot" width="60%">

**Tips**: To enable syntax highlighting, specify the language after the opening triple backticks. Discourse supports popular languages like Python, JavaScript, HTML, and more.

For example:

```python
def add(a, b):
    return a + b
```

<img src="../assets/images/forum/syntax_highlighting_example.png" alt="syntax highlighting example screenshot" width="60%">
