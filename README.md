# hrk-toggle

_hrk-toggle_ is a CSS-only library to generate responsive multi-level menus and tree-navigation structures. This means that it requires no Javascript, no Javascript libraries, no Jquery, no nothing to work.

What it does take to work is HTML that is structured just so with classes in the right spots.

_hrk-toggle_ uses opener's and closers for each level and allows the parent item for each level to be accessed independently of the opening of its children.

_hrk-toggle_ has one single media query and is strictly css with no SASS, no SCSS, no LESS, no npm, no Bower, no Grunt, no nodejs task-runners, no Yarn, no Ruby gems.

_hrk-toggle_ uses CSS Flex constructs and plays nicely with flexbox-based CSS frameworks such as [UIkit](https://getuikit.com)

## Licensing

MIT as shown in LICENSE.md

## How to install

Download the file hrk-toggle.css and include it as a css file in the header of your html.

## How to use

To use this library, you will set certain HTML elements with particular classes and IDs.

### CSS Classes

#### Primary behavior classes

  - hrk-bar: a responsive element
  - hrk-navbar: a horizontal element (navigation bar) with a responsive menu that is horizontal at high res, and vertical at low resolutions
  - hrk-bar-perm: a non-responsive part of a navigation bar
  - hrk-bar-extramenu: a set of non-responsive menu elements in a navigation bar
  - hrk-bar-item: a single non-responsive element in a navigation bar
  - hrk-bar-last: the last element of a navigation bar

  - hrk-toggle: an <input toggle for a toggleable element. An hrk-toggle should always be followed by a visual <label element
  - hrk-bar-toggle: an <input toggle for a responsive menu (.hrk-menu)
  - hrk-toggle-label: left-standout for a toggle label
  - hrk-toggle-close-menu: a label to add to a a toggle closing <input element when the original toggle is a radio rather than a checkbox toggle
  
  - hrk-menu: a responsive menu associated with an .hrk-bar or .hrk-navbar that is responsive and vertical at low resolutions. Must be associated with an <input-<label combination with the input having both .hrk-toggle and .hrk-bar-toggle classes
  - hrk-leaf: one of two primary elements of a menu. A leaf is a tip of the branch.
  - hrk-tree: the second of two primary menu elements. A tree will have one or more branches below it. The tree must be structured with a checkbox <input toggle element and its associated toggle <label, and then a <div.hrk-tree-node with a top-level title or link for the set of branches, and then any children elements within a <div.hrk-tree-children. The child elements are .hrk-leaf or .hrk-tree elements as descending from the original .hrk-menu
  - hrk-tree-node: a sub-structure of .hrk-tree described in .hrk-tree
  - hrk-tree-children: a sub-structure of a .hrk-tree-node described in .hrk-tree
  - hrk-menu-active: formatting for an active element
  
#### Toggle formatting classes

  - hrk-toggle-fmt-x: a general-purpose toggle that allows any icon as its trigger and puts an X to close ?? check this
  - hrk-toggle-fmt-caret: show opener closer caret symbols
  - hrk-toggle-fmt-plusminus: toggle with + and - symbols
  - hrk-toggle-fmt-ellipsis: toggle with ... and X
  - hrk-toggle-fmt-onoff: a general-purpose toggle that allows any icons as its trigger openers and closers. Opener will need to be classed as .hrk-toggle-fmt-onoff-on. Closer classed as .hrk-toggle-fmt-onoff-off
  - hrk-toggle-fmt-paginav: a navigation icon for responsive page navigation

#### Extra formatting classes (for the Navbar burger icon)

  - .hrk-burger-bar
  - .hrk-burger-menu
  
#### General purpose classes

  - hrk-float-left: float a block structure left
  - hrk-float-right: float a block structure right
  - hrk-display-inlineblock: display as inline-block
  - hrk-flex-row: set a flex element with row direction
  - hrk-margin-none: no margins
  - hrk-margin-medium: medium-size margin all around  
  - hrk-a: a class to add to a <span to have it appear with similar formatting as an <a link element

#### Optional toggle formatting classes

There are several Font-Awesome-based classes that format opener-closers using the Font-Awesome free icon library. They are:

  - .hrk-toggle-fmt-facaret -- the opener/closer uses the sideways and downwards caret icons
  - .hrk-toggle-fmt-faplusminust -- the opener/closer uses the plus and minus icons
  - .hrk-toggle-fmt-faburgermenu -- the opener/closer uses the burger and X icons
  - .hrk-toggle-fmt-faextramenut -- the opener/closer uses the vertical ellipsis and X icons

These classes are commented by default because one of the guiding principles of this project is that it HAS NO DEPENDENCIES. You can install it and use it without further ado.

### HTML

The formatting shown below is just a shorthand pseudo-CSS for reading only. HTML must be properly formatted.

#### Responsive Navbar

The HTML to use this must be structured as follows:

~~~
  .hrk-navbar-container
    input#responsiveMenuID.hrk-navbar-toggle.hrk-navbar-toggle type="checkbox"
    label.hrk-navbar-toggle-label hrk-toggle-fmt-divburger for="responsiveMenuID"
    .hrk-navbar-perm // use this for all navbar sections that do not collapse for small screens
    .hrk-navbar-responsive // use this for all navbar sections that should collapse for small screens
~~~

#### Menu and tree structures

Structure each parent item like this:

~~~
  .hrk-tree-container
    input#parentID.hrk-toggle type="radio" name="topnavbarname"
    label.hrk-toggle-label for="parentID"
    div.hrk-tree-node
      a link information
      div.hrk-tree-children
        div.hrk-tree-leaf
          a link information
        div.hrk-toggle-close-menu
          input#closerID.hrk-toggle type="radio" name="topnavbarname"
          label.hrk-toggle-label.hrk-toggle-fmt-x for="closerID"
      div.hrk-tree-leaf
        a link information
      div.hrk-tree-leaf
        a link information
~~~

## Example

See __example.html__ for an example of usage.