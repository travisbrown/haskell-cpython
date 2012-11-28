CPython bindings for Haskell
============================

This is a fork of [John Millikin](https://john-millikin.com/)'s
[`cpython`](http://hackage.haskell.org/package/cpython) package,
adapted by Travis Brown to work with Python 2.7.

Usage
-----

A simple example from [this blog post](https://john-millikin.com/articles/ride-the-snake/)
by John Millikin:

    importmport qualified CPython as Py
    Prelude T Py> import qualified Data.Text.IO as T
    Prelude T Py> Py.initialize >> Py.getVersion >>= T.putStrLn
    2.7.3 (default, Apr 24 2012, 00:00:54) 
    [GCC 4.7.0 20120414 (prerelease)]

And a slightly more complex example, using [BeautifulSoup](http://www.crummy.com/software/BeautifulSoup/):

    {-# LANGUAGE OverloadedStrings #-}
    module Main where

    import qualified CPython as Py
    import qualified CPython.Protocols.Object as Py
    import qualified CPython.Types as Py
    import qualified CPython.Types.Module as Py
    import qualified Data.Text as T

    main = do
      Py.initialize
      doc <- fmap Py.toObject $ Py.toUnicode "<html><body><span>foo"
      bs4 <- Py.importModule "bs4"
      soup <- Py.getAttribute bs4 =<< Py.toUnicode "BeautifulSoup"
      print =<< Py.fromUnicode =<< Py.string =<< Py.callArgs soup [doc]

This will print the following:

    "<html><body><span>foo</span></body></html>"

The Python 2.7 support is still mostly untested.

