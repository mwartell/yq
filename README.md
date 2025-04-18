# yq - a degenerate converter inspired by python yq

[yq](https://github.com/kislyuk/yq) is a fully featured command-line YAML, XML, TOML
processor which wraps around the jq JSON processor.

At present there is only one incantation

    yq . file…

which where the only filter allowed (and required) is `.` and the only output
is YAML on the standard output.

Someday I might make it do more.

## motivation

I had a json file that I wanted to add comments to, but comments are famously
disallowed in json. So I wanted a yaml version of the json file and knew that
`pip install yq` would get me that, but I didn't want to be bothered with a
virtualenv for this one-off task. Having recently seen the epehmeral environment
that allows

   go run <package>

without installation. I figured I'd do the same in Go.

## confounds

So I made this repo, and then realized that Astral's `uv` tool also has the ability
to make ephemeral environments so that

    uvx run jq . thing.json --yaml-output > thing.yaml

will pull package `jq` from pypi.org and run it as a one-off.

### reinventing wheels

And then I found that there was a golang program [Dasel](https://daseldocs.tomwright.me/)
which does the conversion I wanted in Go.

Full in the knowledge that code you don't write has zero bugs, and having found two
viable substitutions for what I wanted, this is probably my last commit to this repo.
