# ln-style-guide

Nothing to see here for now. Eventually I will generate styled haskell code using hindent --style adarqui, and combine it all into this README.md

TODO

Just to have something here.. taken from Chris Done's style guide & modified for my own style.

## Indentation

Indent two spaces. No tabs.

## Line length

Prefer 120 character columns. Most code fits cleanly.
If not, break it up appropriately.

## Modules

Always document the module header:

``` haskell
-- | What this module does.

module LN.Foo where
```

Put the `where` on the same line unless there are exports.

## Exports

If there are exports then write them like this:

``` haskell
module LN.Foo (
    a
  , b
  , c
) where
```

## Imports

Specify imports 3 lines after the module declaration.
Put imports one empty line after the module header.
Make sure the import module Name has 11 chars in between,
unless "qualified" is used.  Always put imports on separate lines,
and sort them alphabetically:

``` haskell
module LN.Foo where



import           X
import qualified Y
```

Always group import lists ending with your own project-local imports. Start
with common imports:

``` haskell
module LN.Foo.Bar where



import           Control.Monad
import           Data.Text
import           Data.List
import           Data.Maybe
import           System.IO
import           System.Process

import           LN.Foo.Zot
import           LN.Foo.Bob

```

Write import lists like this:

``` haskell
import           X (foo, bar)
```

And if they don't fit on one line, like this:

``` haskell
import           X ( foo
                   , bar)
```

If you have many imports, prefer explicit qualification:

``` haskell
import qualified X as Z
```

Prefer to import types unqualified:

``` haskell
import qualified Data.Text as Text
import           Data.Text (Text)
```

We can then use functions within Text such as `Text.pack`, and
refer to Text itself like so: `function :: Text -> Text`.
