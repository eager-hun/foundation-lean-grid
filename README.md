# Foundation Lean Grid


## Introduction

This project aims to offer the possibility to use [Zurb Foundation's float-based
grid system][Foundation-grid-docs] outside Foundation projects.

Additionally, it aims to replace Foundation's approach of **pre-generating**
large sets of HTML classes, with a mostly mixin-based, **on-demand-grid**
approach.

This fork might not offer all the functionality that Foundation grids might
have.

Documenting feature parity and including working demos of supported features
are TODO.

### Modifications to original Foundation code

This repo was started out based on code from the [6.3.0 release of Zurb
Foundation][Foundation-6.3.0]. Whereever I modified the code, it is marked with
`CUSTOMIZED PART!` inline comments.

To find out how many places are altered, run `grep -r 'CUSTOMIZED PART!' .` in
the root directory in the project.

### Planned modifications

I currently tend to use overrides to Foundation grids such ways that make the
end result [work like Bootstrap 3's grid does][Bootstrap-3-grid-explained], in
other words, I use structures equivalent to `.container > .row > .column`,
where all `.row`s, even outermost ones behave as if they were a) Bootstrap's
rows, or b) in Foundation methodology, "nested rows". This means `max-width:
none;` and half-gutter-sized negative side margins for every row, out of the
box.

I'm pondering over including these modifications to this library so that the
act of overriding would not have to be done in the browser upon every page
load.

Perhaps I could look into providing both behaviors based on setting an option
variable.


## Usage

- Add the `foundation-lean-grid/scss` path to your `includePaths` sass compiler
  option, then
- `@import 'foundation-lean-grid';` in your master stylesheet, then
- read on about importing the dependencies too:

### Including dependencies

TLDR:
If you are using this project in a non-Foundation environment, then you need to
import not only the primary `_foundation-lean-grid.scss` file, but before it,
the `_foundation-lean-grid-deps.scss` file too.

Reasoning:

This lib is currently being developed in and tested against a project that is
a non-Foundation environment. Here, I have to provide copies of additional
utility files from the Foundation project that the grid system depends on.

Yet, I aim to not rule out the possibility of using this grid fork even within
Foundation environments. (I however haven't yet tested how many obstacles to
that would exist.)

In the meantime, I separated the primary functionality and the copied
dependencies into separate master files, so that omitting the inclusion of the
copies of dependencies would be possible when using this lib in a Foundation
environment (where Foundation itself will have provided all the dependencies).

## Credits and license

Most of the code and work this repository contains is coming from the Zurb
Foundation project, which is MIT licensed.

This repository is also MIT licensed.

[Foundation-grid-docs]: http://foundation.zurb.com/sites/docs/grid.html
[Foundation-6.3.0]: https://github.com/zurb/foundation-sites/tree/v6.3.0
[bootstrap-3-grid-explained]: http://www.helloerik.com/the-subtle-magic-behind-why-the-bootstrap-3-grid-works

