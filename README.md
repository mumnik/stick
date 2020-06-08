Stick
=====

[![Build Status](https://travis-ci.org/tyler-sommer/stick.svg?branch=master)](https://travis-ci.org/tyler-sommer/stick)
[![GoDoc](https://godoc.org/github.com/mumnik/stick?status.svg)](https://godoc.org/github.com/mumnik/stick)

A Go language port of the [Twig](http://twig.sensiolabs.org/) templating engine. 


Overview
--------

This project is split over two main parts.

Package
[`github.com/mumnik/stick`](https://github.com/mumnik/stick)
is a Twig template parser and executor. It provides the core
functionality and offers many of the same extension points as Twig like
functions, filters, node visitors, etc.

Package
[`github.com/mumnik/stick/twig`](https://github.com/mumnik/stick/tree/master/twig)
contains extensions to provide the most Twig-like experience for
template writers. It aims to feature the same functions, filters, etc.
to be closely Twig-compatible.

### Current status

##### Stable, mostly feature complete

Stick itself is mostly feature-complete, with the exception of
whitespace control, and better error handling in places.

Stick is made up of three main parts: a lexer, a parser, and a template
executor. Stick's lexer and parser are complete. Template execution is
under development, but essentially complete.

See the [to do list](#to-do) for additional information.


Installation
------------

Stick is intended to be used as a library. The recommended way to install the library is using `go get`.

```bash
go get -u github.com/mumnik/stick
```


Usage
-----

Execute a simple Stick template.

```go
package main

import (
	"log"
	"os"
    
	"github.com/mumnik/stick"
)

func main() {
	env := stick.New(nil)
	if err := env.Execute("Hello, {{ name }}!", os.Stdout, map[string]stick.Value{"name": "Tyler"}); err != nil {
		log.Fatal(err)
	}
}
```

See [godoc for more information](https://godoc.org/github.com/mumnik/stick).


To do
-----

- [x] Autoescaping (see: https://github.com/mumnik/stick/blob/master/twig)
- [ ] Whitespace control
- [ ] Improve error reporting

##### Further
- [ ] Improve test coverage (especially error cases)
- [ ] Custom operators and tags
- [ ] Sandbox
- [ ] Generate [native Go code from a given parser tree](https://github.com/tyler-sommer/go-stickgen)
