# v2.2.2
## 05/25/2021

1. [](#bugfix)
    * `|raw` missing in JSON template

# v2.2.1
## 12/02/2020

1. [](#new)
    * Require Grav 1.6.0+
    * Added autoloader
    * Pass phpstan level 3 tests
1. [](#bugfix)
    * Fixed `header_keys_ignored` configuration option not taking effect

# v2.2.0
## 09/14/2020

1. [](#improved)
    * Added config option to choose keys to ignore when searching header
    * Added ability to opt-out of page search by setting: `simplesearch: process: false` in page header
    * Added `form` and `forms` to default list of ignores in page header searches
1. [](#bugfix)
    * Fix issue to ensure matching ignore keys only checked at root level
    * Fix issue where searchable header content was growing exponentially

# v2.1.0
## 05/27/2020

1. [](#new)
    * Added ability to search page headers (excluding title, taxonomy, content)

# v2.0.0
## 05/13/2020

1. [](#new)
    * Allow searching the content of modular pages [#170](https://github.com/getgrav/grav-plugin-simplesearch/pull/170)
    * Allow configuration of Title/Content/Taxononmy searchable types [#184](https://github.com/getgrav/grav-plugin-simplesearch/pull/184)
1. [](#improved)
    * Improved default vs custom search page functionality [#186](https://github.com/getgrav/grav-plugin-simplesearch/pull/186)
    * Add field label for screen reader accessibility [#171](https://github.com/getgrav/grav-plugin-simplesearch/pull/171)
    * Added Traditional Chinese [#169](https://github.com/getgrav/grav-plugin-simplesearch/pull/169)
    * Updated Russian and English [#165](https://github.com/getgrav/grav-plugin-simplesearch/pull/165)
    * Added Galacian [#155](https://github.com/getgrav/grav-plugin-simplesearch/pull/155)
1. [](#bugfix)
    * Fixed input attribute [#165](https://github.com/getgrav/grav-plugin-simplesearch/pull/165)

# v1.14.2
## 12/07/2018

1. [](#improved)
    * Optimize, cleanup and remove typos [#163](https://github.com/getgrav/grav-plugin-simplesearch/pull/163)
    * Removed `blog` as default filter [#166](https://github.com/getgrav/grav-plugin-simplesearch/pull/166)
    * Polish translation [#144](https://github.com/getgrav/grav-plugin-simplesearch/pull/144)
    * Kazakh translation [#153](https://github.com/getgrav/grav-plugin-simplesearch/pull/153)
    * Spelling corrections [#145](https://github.com/getgrav/grav-plugin-simplesearch/pull/145)
1. [](#bugfix)
    * Fix JS to work with IE11 [#161](https://github.com/getgrav/grav-plugin-simplesearch/pull/161)
    * Updated javascript to be compatible with IE11 [#161](https://github.com/getgrav/grav-plugin-simplesearch/pull/161)
    * Ensure `$values` is an array to prevent PHP error on implode [#146](https://github.com/getgrav/grav-plugin-simplesearch/pull/146)

# v1.14.1
## 01/11/2018

1. [](#bugfix)
    * Fix for Gantry5 themes

# v1.14.0
## 01/08/2018

1. [](#new)
    * Added Danish translations [#127](https://github.com/getgrav/grav-plugin-simplesearch/pull/127)
1. [](#improved)
    * New option to disable built-in JS [#130](https://github.com/getgrav/grav-plugin-simplesearch/pull/130)
    * Changed elipsis from `...` to `…` [#133](https://github.com/getgrav/grav-plugin-simplesearch/pull/133)
    * Added missing French translations [#136](https://github.com/getgrav/grav-plugin-simplesearch/pull/136)
    * Added missing German translations [#128](https://github.com/getgrav/grav-plugin-simplesearch/pull/128)
1. [](#bugfix)
    * Escaped `query` in Twig templates for XSS protection

# v1.13.0
## 07/26/2017

1. [](#improved)
    * Support for multiple forms and fields in the same page
1. [](#bugfix)
    * Fix typo in `SEARCH_FIELD_MINIUMUM_CHARACTERS` translation string
    * Fixed validation and JS submission
    * Separated JS from inline to file
    * Fixed issue with min query length always enforced. It is now possible to have no minimum length by setting to `false` or `0`

# v1.12.0
## 05/31/2017

1. [](#new)
   * Added option to switch between Rendered HTML and Raw Markdown content searching. Raw Markdown is faster than default.

# v1.11.0
## 05/29/2017

1. [](#new)
    * Allow to use "@none"/"none@" in the "Category filter" in Admin to allow removing the filter

# v1.10.2
## 04/19/2017

1. [](#bugfix)
    * Only check ACL if the Login plugin is installed [#112](https://github.com/getgrav/grav-plugin-simplesearch/pull/112)

# v1.10.1
## 04/11/2017

1. [](#new)
    * Added Portuguese translation
    * Add hint when the minimum search field length is not matched
1. [](#bugfix)
    * Default `ignore_accented_characters` to false
    * Fallback to regular search if searching with `ignore_accented_characters` on an unsupported charset raises an exception [#107](https://github.com/getgrav/grav-plugin-simplesearch/issues/107)
    * Check ACL before listing a page in the search results [#102](https://github.com/getgrav/grav-plugin-simplesearch/pull/102)
    * Fix with ignoring `min_query_length` when using the button [#99](https://github.com/getgrav/grav-plugin-simplesearch/issues/99)

# v1.10.0
## 01/23/2017

1. [](#new)
    * Added spanish translation
    * Added japanese translation
    * Added persian translation
1. [](#improved)
    * Added option to switch between Rendered HTML and Raw Markdown content searching.  Raw Markdown is faster than default.
    * Removed jQuery dependency, fixes issue when jQuery is loaded in the footer [#57](https://github.com/getgrav/grav-plugin-simplesearch/pull/57)
    * Added option to ignore accents when searching [#89](https://github.com/getgrav/grav-plugin-simplesearch/pull/89)
1. [](#bugfix)
    * Remove unpublished and un-routable pages from the result set
    * Fixed issue when using @self as route
    * Fix overloaded property issue when searching on a page with simplesearch header [#80](https://github.com/getgrav/grav-plugin-simplesearch/issues/80)
    * Fix issue with empty string and leading commas [#71](https://github.com/getgrav/grav-plugin-simplesearch/issues/71)

# v1.9.3
## 10/19/2016

1. [](#bugfix)
    * Fixed an issue with invalid syntax in `route: @self` logic

# v1.9.2
## 09/19/2016

1. [](#bugfix)
    * Reverted change in events - causing problems
    * Reverted fix for `route: @self`, breaking `filter: @self` (used in getgrav.org)

# v1.9.1
## 09/08/2016

1. [](#bugfix)
    * Fixed logic to use `onPageInitialized` event

# v1.9.0
## 09/06/2016

1. [](#new)
    * Multiple search boxes support [#52](https://github.com/getgrav/grav-plugin-simplesearch/pull/52)
    * Added Croatian and Russian translation
1. [](#improved)
    * Added support for Grav's autoescape twig setting
1. [](#bugfix)
    * Fix searching on `@self  `[#53](https://github.com/getgrav/grav-plugin-simplesearch/pull/53)

# v1.8.0
## 07/14/2016

1. [](#new)
    * Added dutch and romanian
1. [](#bugfix)
    * Fix translating the search input placeholder

# v1.7.1
## 05/03/2016

1. [](#new)
    * Added configurable `min length` option for how many characters needed before you can search

# v1.7.0
## 04/30/2016

1. [](#new)
    * Added support for taxonomy searching in regular searches (not just on-page searches as was the case previously)
    * Added support for `route: '@self'` to use the route of the current page without specifying it.
    * Added display search button option - #33
    * Refactored code for clarity

# v1.6.2
## 01/06/2016

1. [](#improved)
    * Improved the README instructions on how to save all pages

# v1.6.1
## 11/11/2015

1. [](#improved)
    * Strip HTML tags from title and content before searching

# v1.6.0
## 11/11/2015

1. [](#new)
    * Removing `filter:` from configuration will search **ALL** pages

# v1.5.1
## 10/15/2015

1. [](#improved)
    * Minor performance fix
    * Updated README.md with more help
1. [](#bugfix)
    * Fix for special character searches

# v1.5.0
## 10/07/2015

1. [](#new)
    * Allow simplesearch to work with on-page collections

# v1.4.1
## 08/31/2015

1. [](#improved)
    * Fixed some blueprint issues

# v1.4.0
## 08/25/2015

1. [](#improved)
    * Added blueprints for Grav Admin plugin
    * Added results sorting

# v1.3.0
## 07/21/2015

1. [](#new)
    * Added support for modular pages in results

# v1.2.7
## 07/17/2015

1. [](#bugfix)
    * Fixed "Undefined index: extension" error

# v1.2.6
## 07/14/2015

1. [](#bugfix)
    * Fixed URL issue that showed up with multi-languages

# v1.2.5
## 04/24/2015

1. [](#bugfix)
    * Fixed issue with broken image

# v1.2.4
## 02/19/2015

2. [](#improved)
    * Implemented new `param_sep` variable from Grav 0.9.18

# v1.2.3
## 01/06/2015

1. [](#improved)
    * Improved `README.md` file with more information

# v1.2.2
## 12/21/2014

1. [](#bugfix)
    * Fix for invalid base_url in some instances

# v1.2.1
## 11/30/2014

1. [](#new)
    * ChangeLog started...
