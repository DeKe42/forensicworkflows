<h1 align="center">{{.Name}}</h1>

<p  align="center">
 <a href="https://{{.ModulePath}}/actions"><img src="https://{{.ModulePath}}/workflows/CI/badge.svg" alt="build" /></a>
 <a href="https://codecov.io/gh/{{.RelModulePath}}"><img src="https://codecov.io/gh/{{.RelModulePath}}/branch/master/graph/badge.svg" alt="coverage" /></a>
 <a href="https://goreportcard.com/report/{{.ModulePath}}"><img src="https://goreportcard.com/badge/{{.ModulePath}}" alt="report" /></a>
 <a href="https://pkg.go.dev/{{.ModulePath}}"><img src="https://godoc.org/{{.ModulePath}}?status.svg" alt="doc" /></a>
</p>

{{.Synopsis}}

## Installation

```shell
go get -u {{.ModulePath}}
```

{{.MainDoc}}

{{if .Examples}}
## Examples
{{ range $key, $value := .Examples }}

{{if $key}}### {{ $key }}{{end}}
` + "```" + ` go
{{ $value }}
` + "```" + `
{{end}}{{end}}

## Contact

For feedback, questions and discussions you can use the [Open Source DFIR Slack](https://github.com/open-source-dfir/slack).

## Acknowledgment

The development of this software was partially sponsored by Siemens CERT, but
is not an official Siemens product.
