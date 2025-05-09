# Contributing to DNSimple/Go

The main `dnsimple` package is defined in the `/dnsimple` subfolder of the `dnsimple/dnsimple-go` repository. Therefore, please note that you will need to move into the subfolder to run any `go` command that assumes the current directory to be the package root.

## Getting started

### 1. Clone the repository

Clone the repository [in your workspace](https://go.dev/doc/code#Organization) and move into it:

```shell
git clone git@github.com:dnsimple/dnsimple-go.git
cd dnsimple-go
```

### 2. Build and test

[Run the test suite](#testing) to check everything works as expected.

## Testing

Submit unit tests for your changes. You can test your changes on your machine by running the test suite (see below).

When you submit a PR, tests will also be run on the [continuous integration environment via GitHub Actions](https://github.com/dnsimple/dnsimple-go/actions).

### Test Suite

To run the test suite:

```shell
go test -v ./...
```

To run the test suite in a live environment (integration):

```shell
export DNSIMPLE_TOKEN="some-token"
go test -v ./...
```

## Releasing

The following instructions uses `$VERSION` as a placeholder, where `$VERSION` is a `MAJOR.MINOR.BUGFIX` release such as `1.2.0`.

1. Run the test suite and ensure all the tests pass.

2. Set the version in `dnsimple.go`:

    ```go
    Version = "$VERSION"
    ```

3. Run the test suite and ensure all the tests pass.

4. Finalize the `## main` section in `CHANGELOG.md` assigning the version.

5. Commit and push the changes

    ```shell
    git commit -a -m "Release $VERSION"
    git push origin main
    ```

6. Wait for CI to complete.

7. Create a signed tag.

    ```shell
    git tag -a v$VERSION -s -m "Release $VERSION"
    git push origin --tags
    ```
