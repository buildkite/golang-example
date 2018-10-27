# Buildkite Golang Example

[![Add to Buildkite](https://buildkite.com/button.svg)](https://buildkite.com/new)

This repository is an example on how to test a Golang project using Buildkite.

Interested in using Docker instead? _(which is way mega simpler than this)_ Check
out https://github.com/buildkite/golang-docker-example

## Using in your own build pipelines

This uses our [gopath-checkout](https://github.com/buildkite-plugins/gopath-checkout-buildkite-plugin) which does all the heavy lifting of setting up a correct `GOPATH` for you.

You just need to provide it with your go package in the `import` setting and the go commands or scripts you want to run.

```yaml
steps:
  - name: ":golang:"
    command: "./scripts/test.sh"
    plugins:
      gopath-checkout#v1.0.1:
        import: github.com/keithpitt/project/sub-package
```

## License

See [Licence.md](Licence.md) (MIT)
