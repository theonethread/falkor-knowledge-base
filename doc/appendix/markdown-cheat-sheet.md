# **Markdown Cheat Sheet**

[Markdown Documentation](https://daringfireball.net/projects/markdown/ "Visit")

## **Table of Contents**

1. [Syntax](#syntax "View")
1. [Lists](#lists "View")
1. [Tables](#tables "View")
1. [Heading ID Generation](#heading-id-generation "View")

## **Syntax**

| Scenario | Syntax | Note |
| :-- | :-- | :-- |
| heading | `# Single Heading 1` | must be on new line, document should only contain a single root heading 1 |
|  | `## Heading 2` | belongs to parent in the hierarchy |
|  | `## Other Heading 2` |  |
|  | `###… Heading N` |  |
| paragraph | `Paragraph one↳` | don't indent paragraphs, unless in a list |
|  | `↳` | note empty line between texts |
|  | `Paragraph two` |  |
| line break | `line one··` | middot represents space |
|  | `line two` |  |
| bold | `**bold text**` |  |
| italic | `_italic text_` |  |
| strike through | `~~strike through text~~` |  |
| monospace | `` `monospace` `` | you can add further formatting to monospace |
| code block | ` ```shell ` | add language for syntax highlighting |
|  | `$ git fetch` |  |
|  | ` ``` ` |  |
| blockquote | `> blockquote` | can be nested, can contain other markdown formatted elements |
| horizontal ruler | `---` | must be on new line |
| link | `[link text](https://url "title")` | since the title appears as a tooltip hovering the link, we usually identify external links with `"Visit"`, internal links with `"View"`, and links to project files, such as JSONs with `"Open"` |
|  | `[link text](#-replaced-heading "title")` | link to a heading in the document, IDs are [generated](#heading-id-generation "View") from the heading's text |
|  | `[link text](local/file.md#-replaced-heading "title")` | link to a heading in another file |
| image | `![alt text](url "title")` |  |
|  | `[![image alt text](url "image title")](https://url "link title")` | you can add links to images |
| escaping reserved characters | `here are some \*\* stars` |  |

## **Lists**

### Unordered list

```shell
- item                              # list items start with dash and space
- item
- item
  - item                            # hierarchy achieved with indenting the enclosed
  - item                            # dash over the parent's first space after its dash
    - item
    …
```

### Ordered list

```shell
1. item 1.                          # list items start with "1." (while it is possible to
1. item 2.                          # use exact list numbers, it is cumbersome, and the
1. item 3.                          # language processor we do it for us anyway
1. item 4.
   1. item 4.1.                     # hierarchy achieved with indenting the enclosed
   1. item 4.2.                     # number over the parent's first space after its number
      1. item 4.2.1.
    …
```

## **Tables**

```shell
| head 1 | head 2 | head 3 |        # note enclosing vertical bars
| :-- | --: | :-: |                 # alignment: left, right, center
| value 1 | value 2 | value 3 |
```

## **Heading ID Generation**

IDs are generated from the heading text in the following order:

1. convert to lowercase
1. non-word text (punctuation, HTML, etc.) is removed
1. spaces are converted to hyphens
1. two or more hyphens in a row are converted to one
1. if ID is taken, a unique incrementing number is appended (starting at 1)

##

---

_©2020-2023 Barnabas Bucsy - All rights reserved._
