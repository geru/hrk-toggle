# hrk-toggle

hrk-toggle is a CSS-only library to generate responsive multi-level menus and tree-navigation structures. This means that it requires no Javascript, no Javascript libraries, no Jquery, no nothing to work.

What it does take to work is HTML that is structured just so with classes in the right spots.

hrk-toggle uses opener's and closers for each level and allows the parent item for each level to be accessed independently of the opening of its children.

hrk-toggle has one single media query and is strictly css with no SASS, no SCSS, no LESS, no npm, no Bower, no Grunt, no nodejs task-runners, no Yarn, no Ruby gems.

hrk-toggle uses CSS Flex constructs and plays nicely with Flex-based CSS frameworks such as [UIkit](https://getuikit.com)

## Licensing



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

Structure each parent item like this (the formatting shown is just a shorthand CSS for reading only. You will have to format the HTML properly):

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

The following is verbatim HTML that describes a responsive menu structure using hrk-toggle. The UIkit CSS framework is used for some extra formatting in the example:

~~~
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/uikit/3.0.3/css/uikit.min.css" />
    <link rel="stylesheet" href="css/hrk-toggle/hrk-toggle.css">
</head>
<body>
<nav class="uk-navbar-container hrk-navbar-container">
    <input class="hrk-toggle hrk-navbar-toggle" type="checkbox" id="hrk-MenuToggle">
    <label class="hrk-navbar-toggle-label hrk-toggle-fmt-divburger" for="hrk-MenuToggle">
        <div class="hrk-burger-bar"></div>
        <div class="hrk-burger-menu">menu</div>
        <div class="hrk-burger-bar"></div>
    </label>
    <div class="navbar-brand uk-flex hrk-navbar-perm uk-margin-small-left">
        <div class="brand-logo"><img src="https://cdn.pixabay.com/photo/2011/12/13/14/31/earth-11015__180.jpg" alt="hrk-toggle"
                                     title="Put your logo here" id="logo" width="64px" height="64px"></div>
        <div class="uk-flex uk-flex-column">
            <div class="brand-sitename">hrk-toggle</div>
        </div>
    </div>
    <div class="hrk-navbar-perm navbar-extramenu uk-flex uk-flex-row uk-flex-center@l">

        <a class="uk-margin-right" href="/search" aria-expanded="false">
            <svg width="20" height="20" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg" data-svg="search">
                <circle fill="none" stroke="#000" stroke-width="1.1" cx="9" cy="9" r="7"></circle>
                <path fill="none" stroke="#000" stroke-width="1.1" d="M14,14 L18,18 L14,14 Z"></path>
            </svg>
        </a>
        <div uk-dropdown="" class="uk-dropdown">
            <form class="search-form" action="/search" method="post" id="search-form" accept-charset="UTF-8">
                <div>Example spot for search form</div>
            </form>
        </div>
        <a href="/user" aria-expanded="false">
            <div uk-tooltip="logged in user" title="" aria-expanded="false">
                <svg width="20" height="20" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg" data-svg="user">
                    <circle fill="none" stroke="#000" stroke-width="1.1" cx="9.9" cy="6.4" r="4.4"></circle>
                    <path fill="none" stroke="#000" stroke-width="1.1"
                          d="M1.5,19 C2.3,14.5 5.8,11.2 10,11.2 C14.2,11.2 17.7,14.6 18.5,19.2"></path>
                </svg>
            </div>
        </a>
        <div uk-dropdown="" class="uk-dropdown">
            <ul class="extra-nav">
                <li class="menu-2 first"><a href="/user">My account</a></li>
                <li class="menu-15 last"><a href="/user/logout">Log out</a></li>
            </ul>
        </div>
    </div>
    <div class="hrk-navbar-responsive">
        <div class="first expanded uk-margin-small-right hrk-tree-container"><input class="hrk-toggle" type="radio"
                                                                                    id="hrk-cid-459"
                                                                                    name="hrk-navbar"><label
                class="hrk-toggle-label" for="hrk-cid-459"></label>
            <div class="hrk-tree-node"><a href="/projects" title="These are my published projects">Projects</a>
                <div class="hrk-tree-children">
                    <div class="first last leaf uk-margin-small-right hrk-tree-leaf"><a href="/hrk-toggle" title="hrk-toggle is a non-javascript CSS library that implements multi-level responsive menus and expandable tree-structures in HTML with no dependencies.
">hrk-toggle</a></div>
                    <div class="hrk-toggle-close-menu"><input class="hrk-toggle" type="radio" id="hrk-cid-459-close"
                                                              name="hrk-navbar"><label
                            class="hrk-toggle-label hrk-toggle-fmt-x" for="hrk-cid-459-close"></label></div>
                </div>
            </div>
        </div>
        <div class="leaf uk-margin-small-right hrk-tree-leaf"><a href="/diy" title="Do it yourself">DIY</a></div>
        <div class="leaf uk-margin-small-right hrk-tree-leaf"><a href="/0.02"
                                                                 title="My two cents on anything and everything. All opinions are simply the personal opinions of the writer and nothing more.">$0.02</a>
        </div>
        <div class="last expanded uk-margin-small-right hrk-tree-container"><input class="hrk-toggle" type="radio"
                                                                                   id="hrk-cid-463"
                                                                                   name="hrk-navbar"><label
                class="hrk-toggle-label" for="hrk-cid-463"></label>
            <div class="hrk-tree-node"><a href="/website" title="Website technology">website</a>
                <div class="hrk-tree-children">
                    <div class="first expanded uk-margin-small-right hrk-tree-container"><input class="hrk-toggle"
                                                                                                type="checkbox"
                                                                                                id="hrk-cid-464"><label
                            class="hrk-toggle-label" for="hrk-cid-464"></label>
                        <div class="hrk-tree-node"><a href="/drupal" title="Drupal is a content management system.">drupal</a>
                            <div class="hrk-tree-children">
                                <div class="first last expanded uk-margin-small-right hrk-tree-container"><input
                                        class="hrk-toggle" type="checkbox" id="hrk-cid-465"><label
                                        class="hrk-toggle-label" for="hrk-cid-465"></label>
                                    <div class="hrk-tree-node"><a href="/website/front-end"
                                                                  title="Front end website technologies involve: HTML, CSS, and Javascript components that comprise the end-user's experience.">Front
                                        end</a>
                                        <div class="hrk-tree-children">
                                            <div class="first leaf uk-margin-small-right hrk-tree-leaf"><a
                                                    href="/drupal/theme/uk-flex"
                                                    title="UK Flex is a Drupal theme that uses the UI-kit CSS &amp; Javascript framework and the hrk-toggle responsive menu library.">UK
                                                Flex</a></div>
                                            <div class="last leaf uk-margin-small-right hrk-tree-leaf"><a
                                                    href="/taxonomy/term/27" title="ukflex">ukflex</a></div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="last expanded uk-margin-small-right hrk-tree-container"><input class="hrk-toggle"
                                                                                               type="checkbox"
                                                                                               id="hrk-cid-468"><label
                            class="hrk-toggle-label" for="hrk-cid-468"></label>
                        <div class="hrk-tree-node"><a href="/taxonomy/term/28" title="theming">theming</a>
                            <div class="hrk-tree-children">
                                <div class="first leaf uk-margin-small-right hrk-tree-leaf"><a href="/taxonomy/term/20"
                                                                                               title="CSS">CSS</a></div>
                                <div class="leaf uk-margin-small-right hrk-tree-leaf"><a href="/taxonomy/term/23"
                                                                                         title="HTML">HTML</a></div>
                                <div class="leaf uk-margin-small-right hrk-tree-leaf"><a href="/taxonomy/term/21"
                                                                                         title="no Javascript">no
                                    Javascript</a></div>
                                <div class="leaf uk-margin-small-right hrk-tree-leaf"><a href="/taxonomy/term/24"
                                                                                         title="responsive menu">responsive
                                    menu</a></div>
                                <div class="last leaf uk-margin-small-right hrk-tree-leaf"><a href="/taxonomy/term/26"
                                                                                              title="uikit">uikit</a>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="hrk-toggle-close-menu"><input class="hrk-toggle" type="radio" id="hrk-cid-463-close"
                                                              name="hrk-navbar"><label
                            class="hrk-toggle-label hrk-toggle-fmt-x" for="hrk-cid-463-close"></label></div>
                </div>
            </div>
        </div>
    </div>
</nav>
</body>
</html>
~~~
