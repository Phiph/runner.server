# How to run Azure Pipelines locally.

[ChristopherHX/runner.server](https://github.com/ChristopherHX/runner.server) is a project that allows local development and testing of your pipelines.

This introduction guide will install the tool globally so you can easily use the command from any directory. 

## Prerequisites

.Net 6


## Getting Started

### Install [ChristopherHX/runner.server](https://github.com/ChristopherHX/runner.server) as a dotnet tool

`dotnet tool install --global io.github.christopherhx.gharun --version 3.11.2`

### Open a terminal or command promt in a directory that contains a  pipeline.yml file.

`gharun --event azpipelines -W pipeline.yml --runner-version 3.217.1`

The output of your pipeline should output to your cli. 

## Useful commands

### Keep Web UI alive

By the runner server will spawn a web ui hoever it exits onces all tasks have completed. 

To keep the server alive and also watch you directory for live changes run:

add `-w` or `--watch` to the command. 

`gharun --event azpipelines -W pipeline.yml --runner-version 3.217.1`

### Multiple Workers/Parallel Jobs

To simulate multiple runners to use Jobs in parallel use this command.

`--parallel n`

where N is the number of runners. 

`gharun --event azpipelines -W ./pipeline.yml --runner-version 3.217.1 --watch 5`

### Known Issues

The version `3.11.2` of the dotnet tool is the latest at time of writing.

When attempting to run the tool without the `--runner-version 3.217.1` command it would attempt to download a version that is no longer available to download. 

Version `3.217.1` of the runner is selected in the [latest source](https://github.com/ChristopherHX/runner.server/blob/2877d334a1c2a3ff10002650b225252d20da4697/src/Runner.Client/Program.cs#L1112). Maybe the dotnet tool hasn't been published yet. 

https://www.nuget.org/packages/io.github.christopherhx.gharun



## Reference Azure Pipelines:

https://github.com/ChristopherHX/runner.server/tree/main/testworkflows/azpipelines

