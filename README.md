<h1 align="center">forensicworkflows</h1>

<p  align="center">
 <a href="https://github.com/forensicanalysis/forensicworkflows/actions"><img src="https://github.com/forensicanalysis/forensicworkflows/workflows/CI/badge.svg" alt="build" /></a>
 <a href="https://codecov.io/gh/forensicanalysis/forensicworkflows"><img src="https://codecov.io/gh/forensicanalysis/forensicworkflows/branch/master/graph/badge.svg" alt="coverage" /></a>
 <a href="https://goreportcard.com/report/github.com/forensicanalysis/forensicworkflows"><img src="https://goreportcard.com/badge/github.com/forensicanalysis/forensicworkflows" alt="report" /></a>
 <a href="https://pkg.go.dev/github.com/forensicanalysis/forensicworkflows"><img src="https://godoc.org/github.com/forensicanalysis/forensicworkflows?status.svg" alt="doc" /></a>
</p>

Packages forensicworkflows provides a workflow engine to automate forensic processes in forensicstores.

## Installation

```shell
go get -u github.com/forensicanalysis/forensicworkflows
```

## Usage
The command line tool requires a workflow yml file which is executed on an
arbitrary number of forensicstores, e.g.:

```
forensicworkflows --workflow workflow.yml test/example1.forensicstore
```
## Workflow format
The workflow.yml file contains a list of tasks like the following:

```
hello_task:
    type: plugin
    command: hello.exe

docker_task:
    type: docker
    image: alpine
    command: echo bye
    requires:
        - hello_task
```

There are currently 4 different types of tasks.

## Bash
Run a script from bash. The working directory is the forensicstore. Example:

```
list_dir:
    type: bash
    command: ls
```
## Plugin
Run either a builtin Go plugin or an executeable from the plugins folder. The
working directory is the forensicstore. Example:

```
hotfixes:
    type: plugin
    command: hotfixes
```
## Docker
Run a docker container. The forensicstore is located at &#39;/store&#39; and the plugin
folder is located at &#39;/plugins&#39;. Example:

```
docker_task:
    type: docker
    image: alpine
    command: echo bye
```
## Dockerfile
Build a dockerfile from &#39;plugin/{dockerfile}/Dockerfile&#39; and run the created
image. Otherwise behaved as the docker type. Example:

```
dockerfalse:
    type: dockerfile
    dockerfile: jq
    command: echo Dockerfile
```



## Contact

For feedback, questions and discussions you can use the [Open Source DFIR Slack](https://github.com/open-source-dfir/slack).

## Acknowledgment

The development of this software was partially sponsored by Siemens CERT, but
is not an official Siemens product.
