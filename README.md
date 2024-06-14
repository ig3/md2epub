# @ig3/md2epub

A program to generate epub files from Markdown files.

## Install

$ npm install -g @ig3/md2epub

## Generating an epub

Add 1 markdown file for each chapter.

Add images, including cover.jpeg and any images referred to from the
markdown files.

Run `md2epub`

### metadata.json

`md2epub` gets meta-data from a file: `metadata.json`.

If there is no metadata.json, then `md2epub` will generate one.

You can edit metadata.json and re-run `md2epub` to regenerate the epub file
with revised metadata.

The default metadata.json is:

```
{
  "title": "<the name of the containing folder>",
  "cover_image": "cover.jpg"
}
```

While the title is the name of the directory in which md2epub was run.

### epub book

`md2epub` creates an epub book from the files in the directory.

There should be one markdown file per chapter. Each markdown file is
converted into an xhtml file and added to the epub, in directory sort
order. The chapter title is taken from the first top level heading in the
file.

If there is a corresponding image file: an image file with the same
name as the chapter markdown file but with extension jpg, jpeg or png, and
this image file is not already included in the chapter, then it is added
before the chapter title.

### Configuration

Defaults can be set in:
 * /etc/md2epub.json
 * ~/.md2epub.json
 * ~/.config/md2epub.json

For example:
```
{
  "defaultAuthor": "Ano Nymous",
  "defaultCover": "cover.png",
  "defaultDescription": "An epub from Markdown files",
  "defaultLanguage": "EN",
  "defaultTags": [
    "Private",
    "English"
  ],
  "defaultTitle": "An Untitled Work",
  "defaultVerbose": true
}
```

If multiple configuration files exist, they will be merged in the order
they are listed above with values from the latter overriding former values.


## Motivation

I wrote this for a fairly trivial reason: I was using
[pandoc](https://pandoc.org/) to make epub books from Markdown files. It
worked well enough but I wanted to put images before the first header of a
chapter and I couldn't find an easy way to do that with pandoc. At each
level 1 header it starts a new chapter. Anything and everything before a
level 1 header is part of the preceding chapter(s). I may have been able to
do it if I messed with the pandoc templates. I liked the idea of using a
generic tools. But it seemed less work to write this.

This might not follow the epub v3 standard very closely. I'm not familiar
with it. It is written in the cryptic style of all standards written by
companies competing and protecting their profits. No doubt technically
correct if something goes to court and one has a few decades and millions
of dollars to debate the details, but obscuring the essence. I expect
profit security by obscurity. If one can't make sense of the standard, then
there will be less competition. At least, that's how I see it.

But epub books are simple. I didn't read the standard. I copied examples. A
bit of XML composed by string concatenation. Some xhtml files (I wish it
was HTML 5). And it works well enough for
[Calibre](https://calibre-ebook.com/),
[Calibre-web](https://github.com/janeczku/calibre-web) and
[@ig3/calibre-web](https://www.npmjs.com/package/@ig3/calibre-web)

I'm not publishing epub books. I'm composing them purely for my own use.
It's an easy way to turn Markdown into epub that I can consume in my
browser.
