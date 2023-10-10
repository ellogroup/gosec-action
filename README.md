# GitHub Action for gosec

GitHub Action for [gosec](https://github.com/securego/gosec). Gosec is a Golang security checker that inspects source 
code for security problems by scanning the Go AST and SSA code representation.

There are existing GitHub Actions for gosec, but the purpose of this GitHub Action is to support specifying the 
working directory and the installation of Go being optional.

## GitHub Action

You can use the gosec GitHub Action by adding the below to your workflow:
```yaml
  - id: gosec
    uses: ellogroup/gosec-action@v1
    with:
      # The working directory to run gosec against. Default: .
      working-directory: '.'
      # The go package to run gosec against. Default: ./...
      go-package: './...'
```

By default, the action will presume golang has been installed in a previous step. You can install golang as part of this 
action with the below optional inputs:
```yaml
  - id: gosec
    uses: ellogroup/gosec-action@v1
    with:
      # The working directory to run gosec against. Default: .
      working-directory: '.'
      # The go package to run gosec against. Default: ./...
      go-package: './...'
      # Whether to install Go. Default: false
      go-install: true
      # The Go version to download (if necessary) and use
      go-version: '1.21.1'
      # Path to the go.mod or go.work file
      go-version-file: 'go.mod'
      # Used to specify the path to a dependency file - go.sum
      go-cache-dependency-path: 'go.sum'
      # Check for the latest available version. Default: false
      go-check-latest: true
      # Used to specify whether caching is needed. Default: true
      go-cache: true
```