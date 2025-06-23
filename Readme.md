# Buildkite Golang Example

[![Build status](https://badge.buildkite.com/aab023f2f33ab06766ed6236bc40caf0df1d9448e4f590d0ee.svg?branch=main)](https://buildkite.com/buildkite/golang-example)
[![Add to Buildkite](https://buildkite.com/button.svg)](https://buildkite.com/new)

This repository is an example on how to test a [Golang](https://go.dev) project using Buildkite (without using Docker).
👉 **Pipeline:** [buildkite.com/buildkite/golang-example](https://buildkite.com/buildkite/golang-example)


## How it works

This example project:
- Includes a basic `main.go` file that prints a message.
- Uses Go’s built-in `testing` package with `testify` to assert output.
- Includes a `.buildkite/pipeline.yml` that runs tests and `go vet`.


Interested in using [Docker](https://www.docker.com/) instead? _(which is more flexible than this)_ Check
out https://github.com/buildkite/golang-docker-example

**Note:** this example assumes your Buildkite Agent machine has the Go Toolchain installed.

## Requirements

- A Buildkite agent with Go installed (Go 1.21+ recommended)

## To try it yourself

Clone the repo and run:

```bash
go test ./...

## License

See [Licence.md](Licence.md) (MIT)
