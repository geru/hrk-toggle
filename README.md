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

  - .hrk-toggle
  - .hrk-navbar-toggle
  - .hrk-navbar-toggle-label
  - .hrk-navbar-responsive
  - .hrk-navbar-perm
  - .hrk-navbar-container
  - .hrk-tree-container
  - .hrk-toggle-label
  - .hrk-tree-node
  - .hrk-tree-leaf

#### Toggle formatting classes

  - .hrk-toggle-fmt-divburger
  - .hrk-toggle-fmt-x

#### Extra formatting classes (for the Navbar burger icon)
  - .hrk-burger-bar
  - .hrk-burger-menu

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