# Buildkite Golang Example

[![Build status](https://badge.buildkite.com/aab023f2f33ab06766ed6236bc40caf0df1d9448e4f590d0ee.svg?branch=main)](https://buildkite.com/buildkite/golang-example)
[![Add to Buildkite](https://buildkite.com/button.svg)](https://buildkite.com/new)

This repository is an example of testing a [Golang](https://go.dev) project using [Buildkite](https://buildkite.com), **without using Docker**.

👉 **Live Pipeline:** [buildkite.com/buildkite/golang-example](https://buildkite.com/buildkite/golang-example)

## How it works

This example:
- Includes a basic main.go file that prints a message (tested via `main_test.go`)
- Uses Go’s built-in `testing` package with [Testify](https://github.com/stretchr/testify) for assertions.
- Includes a `.buildkite/pipeline.yml` that runs `go test` and `go vet`.
- Uses a Buildkite-hosted agent with Go preinstalled (via a custom image).

<a href="https://buildkite.com/buildkite/golang-example/builds?branch=main">
  <img width="1491" alt="Screenshot of Buildkite Golang example pipeline" src="./assets/golang-example-build-page.png" />
</a>

> 🐳 Interested in a Docker-based Go example instead?
> Check out [buildkite/golang-docker-example](https://github.com/buildkite/golang-docker-example)

## Requirements
- A Buildkite agent with Go installed
  _(or use a hosted agent image like this repo does. See [Buildkite Hosted Agents](https://buildkite.com/docs/pipelines/hosted-agents))_

## To try it yourself

Clone the repo and run:

```bash
go test ./...

# Or run the program directly:
go run .

```

## License

See [Licence.md](Licence.md) (MIT)
