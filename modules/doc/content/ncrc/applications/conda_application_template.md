# {{ApplicationName}} Local Installation

{{ApplicationName}} is available via Conda, from our [NCRC Channel](https://conda.software.inl.gov/ncrc-{{ApplicationLower}}). In order to install {{ApplicationName}} on your machine, you will first need to install a Conda Package Manager.

!include ncrc/applications/ncrc_conda.md

## Install {{ApplicationName}}

Using the ncrc client, install {{ApplicationName}}:

```bash
$ (base) > ncrc install {{ApplicationLower}}

Username: johndoe
PIN+TOKEN:
```

You will need to supply your INL HPC username, and your PIN+TOKEN to proceed.

## Use {{ApplicationName}}

Once installation has finished (this can take a few minutes), you need to activate this environment:

```bash
$ (base) ~> mamba activate {{ApplicationLower}}
$ ({{ApplicationLower}}) ~>
```

With {{ApplicationName}} activated (denoted by the prompt header), `{{binary}}-opt` becomes available within your PATH. This makes `{{binary}}-opt` available for execution from any directory.

```bash
$ ({{ApplicationLower}}) ~> {{binary}}-opt --help

<The {{ApplicationName}} help page is displayed>
```

A good first usage, would be to run the built-in tests. You should run this command while somewhere in your home directory (somewhere where you and only you has write access):

```bash
$ ({{ApplicationLower}}) ~> cd ~/
$ ({{ApplicationLower}}) ~> {{binary}}-opt --copy-inputs tests

<Output of files being copied is displayed>

Directory successfully copied into ./{{binary}}/tests/
```

The very last line indicates the directory you need to enter next in order to run the tests. In our case `./{{binary}}/tests`. Change into this directory, and then run the tests:

```bash
$ ({{ApplicationLower}}) ~> cd ./{{binary}}/tests
$ ({{ApplicationLower}}) ~/{{binary}}/tests> {{binary}}-opt --run -j 5

<Output of tests being run>
```

One or two failures may indicate those tests have their tolerances set too tight. You likely can ignore a few failures.
