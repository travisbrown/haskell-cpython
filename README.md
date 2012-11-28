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

The Python 2.7 support is still mostly untested.

