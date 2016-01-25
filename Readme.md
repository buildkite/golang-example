# Buildkite Golang Example

This repository is an example on how to test a Golang program using Buildkite.

Testing Golang projects can be a bit tricky due to how Golang handles it's
$GOPATH. The best way we've found so far is to create an entirely new $GOPATH
within the build folder, and symlink the current build folder to the desired go
import path location. This is all done within
https://github.com/buildkite/golang-example/blob/master/.buildkite/hooks/pre-command

To use the hook in your build pipelines, copy the `pre-command` file into the
Buildkite hooks directory within your repository `.buildkite/hooks/`. Then
define an environment variable `BUILDKTE_GOLANG_IMPORT_PATH` that contains the
import path to your current repository, i.e:

```bash
steps:
  - command: "./scripts/test.sh"
    env:
      BUILDKTE_GOLANG_IMPORT_PATH: "github.com/buildkite/golang-example"
```

[Add this pipeline to your Buildkite organization](https://buildkite.com/new)

## Docker

To see how to run your Golang projects through Docker and Buildkite, see https://github.com/buildkite/golang-docker-example

## License

See [Licence.md](Licence.md) (MIT)
