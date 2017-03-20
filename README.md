# Pretty
[![Build Status](https://img.shields.io/travis/tidwall/pretty.svg?style=flat-square)](https://travis-ci.org/tidwall/prettty)
[![Coverage Status](https://img.shields.io/badge/coverage-100%25-brightgreen.svg?style=flat-square)](http://gocover.io/github.com/tidwall/pretty)
[![GoDoc](https://img.shields.io/badge/api-reference-blue.svg?style=flat-square)](https://godoc.org/github.com/tidwall/pretty) 


Pretty is a Go package that provides [fast](#performance) methods for formatting JSON for human readability, or to compact JSON for smaller payloads.

Getting Started
===============

## Installing

To start using Pretty, install Go and run `go get`:

```sh
$ go get -u github.com/tidwall/pretty
```

This will retrieve the library.

## Pretty

Using this example:

```json
{"name":  {"first":"Tom","last":"Anderson"},  "age":37,
"children": ["Sara","Alex","Jack"],
"fav.movie": "Deer Hunter", "friends": [
    {"first": "Janet", "last": "Murphy", "age": 44}
  ]}
```

The following code:
```go
result = pretty.Pretty(example)
```

Will format the json to:

```json
{
  "name": {
    "first": "Tom",
    "last": "Anderson"
  },
  "age": 37,
  "children": ["Sara", "Alex", "Jack"],
  "fav.movie": "Deer Hunter",
  "friends": [
    {
      "first": "Janet",
      "last": "Murphy",
      "age": 44
    }
  ]
}
```

## Ugly

The following code:
```go
result = pretty.Ugly(example)
```

Will format the json to:

```json
{"name":{"first":"Tom","last":"Anderson"},"age":37,"children":["Sara","Alex","Jack"],"fav.movie":"Deer Hunter","friends":[{"first":"Janet","last":"Murphy","age":44}]}```
```

## Performance

Benchmarks of Pretty alongside the builtin `encoding/json` Indent/Compact methods.
```
BenchmarkPretty-8         1000000     1080 ns/op     720 B/op      2 allocs/op
BenchmarkUgly-8           3000000      419 ns/op     240 B/op      1 allocs/op
BenchmarkUglyInPlace-8    5000000      348 ns/op       0 B/op      0 allocs/op
BenchmarkJSONIndent-8      300000     4715 ns/op    1069 B/op      4 allocs/op
BenchmarkJSONCompact-8     500000     2424 ns/op     758 B/op      4 allocs/op
```

*These benchmarks were run on a MacBook Pro 15" 2.8 GHz Intel Core i7 using Go 1.7.*

## Contact
Josh Baker [@tidwall](http://twitter.com/tidwall)

## License

Pretty source code is available under the MIT [License](/LICENSE).

