go-radix [Godoc](http://pkg.go.dev/github.com/mkeeler/go-radix)
=========

Provides the `radix` package that implements a [radix tree](http://en.wikipedia.org/wiki/Radix_tree).
The package only provides a single `Tree` implementation, optimized for sparse nodes.

As a radix tree, it provides the following:
 * O(k) operations. In many cases, this can be faster than a hash table since
   the hash function is an O(k) operation, and hash tables have very poor cache locality.
 * Minimum / Maximum value lookups
 * Ordered iteration

This repo is a fork of github.com/armon/go-radix updated to use generics.

Documentation
=============

The full documentation is available on [Godoc](http://pkg.go.dev/github.com/mkeeler/go-radix).

Example
=======

Below is a simple example of usage

```go
// Create a tree
r := radix.New[int]()
r.Insert("foo", 1)
r.Insert("bar", 2)
r.Insert("foobar", 2)

// Find the longest prefix match
m, _, _ := r.LongestPrefix("foozip")
if m != "foo" {
    panic("should be foo")
}
```

