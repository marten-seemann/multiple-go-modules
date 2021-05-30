# GitHub Action: multiple-go-modules

Go allows a Git repository to contain multiple Go modules (i.e. multiple directory trees that have their own `go.mod` file).
When running Go tools like `go test ./...` or `go vet ./...` from the parent directory, it will only recurse into directories belonging to the same Go module.
In order to run the command in all subdirectories, no matter which module they belong to, the command has to be invoked separately for every Go module.

This GitHub Action makes it easy to do this.

## Usage

Take the following example, running a command (or multiple commands) directly:

```yml
steps:
  - name: Code Quality Checks
    run: go vet ./...
```

Using this action, this would run the same command(s) in all Go modules:

```yml
steps:
  - name: Code Quality Checks
    uses: protocol/multiple-go-modules@master
    with:
      run: go vet ./...
```
