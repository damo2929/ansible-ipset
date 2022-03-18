# Contributing

## Submitting a change request

* Fork the repository
* Create a branch from _master_
* Open a pull request into the _master_ branch

## pre-commit hooks

This project uses [pre-commit](https://pre-commit.com/) to ensure that code
standard checks pass locally before pushing to the remote project repo. Follow
the [installation instructions](https://pre-commit.com/#installation), then set
up hooks with pre-commit install. Checks should be run with every commit.

Make sure everything is working correctly by running

```shell
pre-commit run --all
```
