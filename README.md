# remark-wiki-link-plus

Parse and render wiki-style links in markdown especially Obsidian style links.

## What is this ?

Using obsidian, when we type in wiki link syntax for eg. `[[wiki_link]]` it would parse them as anchors.

## Features supported

- [x] Support `[[Internal link]]`
- [x] Support `[[Internal link|With custom text]]`
- [x] Support `[[Internal link#heading]]`
- [x] Support `[[Internal link#heading|With custom text]]`
- [x] Support `![[Image.png]]`
  - supported formats included are jpg, jpeg, png, apng, webp, gif, svg, bmp, ico
- [x] Support `![[Document.pdf]]

> Note: if unspported image format is provided (eg. `![[Image.xyz]]`) a display warning is rendered instead as below:
> `Document type XYZ is not yet supported for transclusions`

Future support:
- [ ] Support `![[Embed note]]`
- [ ] Support `![[Embed note#heading]]`

## Installation

```bash
npm install remark-wiki-link-plus
```

## Usage

```javascript
const unified = require('unified')
const markdown = require('remark-parse')
const wikiLinkPlugin = require('remark-wiki-link-plus');

let processor = unified()
    .use(markdown, { gfm: true })
    .use(wikiLinkPlugin)
```

### Configuration options

* `options.markdownFolder [String]`: A string that points to the content folder.

  The default `hrefTemplate` is:
  
```javascript
(permalink) => `/${permalink}`
```

## Running the tests

```bash
npm run test
```

# Change Log

## [1.1.0] - 2022-08-11

### Added

- Add support for more image formats
  - apng, webp, gif, svg, bmp, ico
- Add support for PDF documents
- Add warning for unsupported image formats

## [1.0.2] - 2022-08-11
 
### Added

- Add support for transclusion links / image links
 - png, jpg, jpeg
 
## [1.0.1] - 2022-08-04

### Changed

- permalink for folders with an index file will tranform to folder name onlu. 
For example, if the wikilink is [[docs/index]] the href will be '/docs'.

### Fixed

- broken links to filenames that matched the markdown folder name.
  
