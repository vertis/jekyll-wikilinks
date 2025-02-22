## [0.0.12] - 2022-05-07
### Changed
- Update nokugiri version.
## [0.0.11] - 2022-01-27
### Added
- Wikilink text can now contain an absolute file path to the desired file.
### Fixed
- Fixed internal title references in parser (Addresses [#28](https://github.com/manunamz/jekyll-wikilinks/issues/28)).
## [0.0.10] - 2022-01-24
### Changed
- Block Wikilinks now allow for partial lists; missing files are stored in the 'missing' attribute.
## [0.0.9] - 2022-01-20
### Fixed
- Liquid filter (also see below).
### Changed
- 'rel_type' -> 'link_type' liquid filter.
## [0.0.8] - 2021-11-23
### Fixed
- Fix square brackets in label text (e.g. labels with three right square brackets in a row [[now|[work]]]). (Fixes [issue #23](https://github.com/manunamz/jekyll-wikilinks/issues/23)).
- Filter fixes.
- Make header matching case insensitive ([[link#to header]] -> # To Header will work, etc.).
### Changed
- Invalid/missing block wikilinks' filenames are added to `missing` metadata instead of wiki-text.
- Refactored block wikilink regex and handling to be cleaner.
- Downcase filenames and headers in rendered wikitext.

## [0.0.7] - 2021-11-01
### Added
- "typed" css class can now be configured.
### Fixed
- Order inline wikilinks such that the replacement of typed wikilinks doesn't clobber untyped wikilinks.

## [0.0.6] - 2021-09-17
### Added
- `missing` frontmatter metadata attribute.
- Allow css class names to be customized in configs.
- Remove `title` attribute from invalid wiki-links -- allow user to append whatever they want via css class names.
- Add converter to insert `web-link` to `a` elements that are not wiki-links.
- Add `css.exclude` list in configs: Any `a` tag with those css classes will not have either `web-link` or `wiki-link` added to it.
### Changed
- LOTS of refactors and project reorganization (esp. adding `patch`, `plugins`, and `util` directories).
- Frontmatter metadata no longer stores jekyll documents, only jekyll document urls.
- Default css class name for typed wikilink renamed `link-type` -> `typed`.
### Removed
- Graph functionality (moved to [jekyll-graph](https://github.com/manunamz/jekyll-graph/)).
### Fixed
- Pages weren't being detected properly.
- Square brackets in label text.

## [0.0.5] - 2021-07-03
### Fixed
- Add block level links to graph via 'attributes' instead of 'attributed'.
- Fix how filename extensions were being detected.
- Sluggify header url fragments in wikilinks. (ex: [[file#with a header]] -> "with a header" -> "with-a-header").

## [0.0.4] - 2021-06-23
### Added
- Syntax:
  - Header level wikilinks: `[[filename#header txt]]`
  - Block level wikilinks: `[[filename#^block_id]]`
  - Labelling support for new wikilink levels.
  - Single file embeds (without internal wikilink processing): `![[filename]]`
  - Image embeds: `![[image.png]]`
  - Typed wikilinks: `link-type::[[filename]]`
    - Two types: block-level and inline-level.
    - Works for all wikilink levels.
  - Embedded typed wikilinks: `!link-type::[[filename]]`
- Metadata:
  - `attributed` (block-level typed backlinks)
  - `attributes` (block-level typed forelinks)
  - `forelinks` ('forward' links)
- Configs:
  - `assets_rel_path`: Set custom assets relative path location in project.
### Changed
- Metadata:
  - ⚠️ `backlinks`: array -> hash with keys `types` and `doc`.
### Removed
- ❗️ Left-side labelling/aliasing.

## [0.0.3] - 2021-05-21
### Added
- `enable` config.
- `exclude` config; user may exclude jekyll types: "pages", "posts", or collection types (ex: "notes").
- d3 graph data generation for network graphs.
- `enable` config for graph data generation.
- `exclude` config for graph data generation (works similarly to above).
- `backlinks` metadata added to each item processed.
- `backlink_type` liquid template filter added.
### Changed
- All markdown files (jekyll types: pages, posts, and collections) are processed by default.

## [0.0.2] - 2021-05-07
- Bumpbed version because yank.

## [0.0.1] - 2021-05-07
- Initial release
- A collection defined in config.yml (`wikilinks_collection: <collection-name>`) will be targetted for processing \[\[wikilinks]], which are parsed and replaced with `a` html elements with a an `href` pointing to the note's url.
