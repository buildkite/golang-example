# Buildkite Golang Example

This repository is an example on how to test a Golang project using Buildkite.
Interested in using Docker instead? Check out
https://github.com/buildkite/golang-docker-example

[Add this example to your Buildkite organization](https://buildkite.com/new)

## Using in your own Build Pipelines

We've wrapped up the `$GOPATH` wrangling required to get Golang projects to run
into a `pre-command` hook which you can see here:
https://github.com/buildkite/golang-example/blob/master/.buildkite/hooks/pre-command

To use in your own build pipelines:

1. Copy the `pre-command` hook into your project:

   ```sh
   cd /your/golang/repo
   mkdir -p .buildkite/hooks
   curl -o .buildkite/hooks/pre-command https://raw.githubusercontent.com/buildkite/golang-example/master/.buildkite/hooks/pre-command
   chmod +x .buildkite/hooks/pre-command
   ```

2. Add `BUILDKTE_GOLANG_IMPORT_PATH` to your build steps. If your import path in Golang looks like this:

   ```go
   import (
     "github.com/keithpitt/project/sub-package"
   )
   ```

   Then your `BUILDKTE_GOLANG_IMPORT_PATH` would be `github.com/keithpitt/project`
   (we don't include the `sub-package` part of the import). This path should also match
   the directory structure within the `$GOPATH` on your own development machine.

   You can add the `$BUILDKITE_BUILD_CHECKOUT_PATH` to your `.pipeline.yml` file like this:

   ```yml
   steps:
     - command: "./scripts/test.sh"
       env:
         BUILDKTE_GOLANG_IMPORT_PATH: "github.com/buildkite/golang-example"
   ```

## How does it work?

Testing Golang projects can be tricky due to how Golang handles it's `$GOPATH`.
What our `pre-command` hook does, is create an entirely new `$GOPATH` tree
within the current build directory (under `tmp/go`), and symlink the current
build directory to the desired go import path location. So the new build
directory would look something like this:

`$BUILDKITE_BUILD_CHECKOUT_PATH/tmp/go/src/github.com/buildkite/golang-example`

The hook then changes the working directory to this new folder, so all of your
build commands happen within the directory.

## Docker

To see how to run your Golang projects through Docker and Buildkite, see

## License

See [Licence.md](Licence.md) (MIT)
