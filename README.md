# Apostrophe converter

A single page tool that finds the apostrophes in your text and replaces each one with `&#8217;`, the numeric entity for a curly apostrophe.

Paste text into the box or upload a file, press convert, then copy the result. The heading above the output tells you how many apostrophes it changed.

`&#8217;` is the most portable way to write the character. It works in HTML, and in plain XML with no DTD, which covers RSS, SVG and XHTML. Named entities like `&rsquo;` do not.

Everything happens in the browser. Nothing you paste or upload is sent anywhere.

## What it converts

- Apostrophes inside contractions: `don't`, `it's`, `you're`, `shouldn't've`
- Apostrophes inside possessives: `Russ's`, `the page's code`
- Apostrophes inside words: `o'clock`, `ne'er`, `Hallowe'en`, `O'Neill`
- Words with a dropped opening letter: `'til`, `'tis`, `'twas`, `'em`, `'cause`, `'bout`, `'round`
- Shortened decades: `'90s`, `'20s`
- `rock 'n' roll`

It does not matter how the apostrophe is written in the source. All eight spellings are recognised, and every one of them ends up as `&#8217;`:

| Written as | What it is |
| --- | --- |
| `'` | straight apostrophe |
| `&#39;` | straight, decimal entity |
| `&#x27;` | straight, hex entity |
| `&apos;` | straight, named entity |
| `’` | curly apostrophe |
| `&#8217;` | curly, decimal entity, already correct |
| `&#x2019;` | curly, hex entity |
| `&rsquo;` | curly, named entity |

The four curly spellings are swapped for `&#8217;` wherever they appear, since they are already the right character and only the spelling differs. The four straight ones are only converted where they are doing an apostrophe's job, never where they are acting as a quotation mark.

Running the tool twice changes nothing the second time.

## What it leaves alone

- Fenced code blocks and inline code in markdown
- The contents of `script`, `style`, `code` and `pre`
- HTML comments
- Everything inside an HTML tag, so quotes around attribute values are never touched
- Quotation marks: `he said 'yes'` is left as it is
- Plural possessives with a trailing apostrophe: `the dogs' bowls`

The last two are the same shape as each other. A straight quote before a space could be closing a quotation or marking a plural possessive, and nothing in the text says which. Rather than guess and get it wrong, the tool leaves both, so those are worth a manual check.

A leading apostrophe has the same problem, which is why dropped letters are handled from a known list of words rather than a general rule.

## Accepted files

`.md`, `.markdown`, `.txt`, `.html`, `.htm` and `.xml`.

## Repo structure

```
index.html          the converter itself, self contained, no dependencies
README.md
LICENSE
```
