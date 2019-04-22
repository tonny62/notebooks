# Markdown Cheatsheet

## Syntax

### Headings

```markdown
    * H1
    ...
    ****** H6
```

### Text

```markdown
    *italic*
    **bold**
    ***bold-italic***
    \~\~strike through\~\~
```

### Images

```markdown
    ![alt](http://example.com)
```

### Lists

```markdown
    * Item
    * Item
        * Nested Item
```

```markdown
    1. item 1
    2. item 2
    3. item 3
```

### Quotes

```markdown
> This is a quote.
```

### Highlight

```markdown
    ==Highlighted==
```

### Horizontal Rule (hr)

```markdown
    ---
```

\* MarkdownLint `MD035` - warn not to use `___` as horizontal rule

### Code

````markdown
    ```

        code block

    ```
````

or

````markdown
    ``` inline code ```
````

### Reference & Footnote

```markdown
    [text to reference][1]
    Some text to footnote[^1]

    [1]: http://example.com/ "alt text"
    [^1]: Footnote explanation
```

### Escape

```markdown
    \* this star is escaped
```

---

## Notes

Using VS Code
    - format document with [yzhang.markdown-all-in-one](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
    - lint with [davidanson.vscode-markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)
    - preview with [shd101wyy.markdown-preview-enhanced](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced)
    - [light theme](https://marketplace.visualstudio.com/items?itemName=ms-vscode.Theme-MarkdownKit) + zen mode `cmd + k` + `z` = :joy:
    - check [this gist](https://gist.github.com/rxaviers/7360908) for emojis

---

## Source

[Ghost Documentation](https://blog.ghost.org/markdown/) - Main source of this document, also provides lists of tools and softwares
[VS Code Markdown](https://code.visualstudio.com/docs/languages/markdown) - VS Code official guide to using markdown with VS Code

---

Compiled by **Kriddanai Roonguthai**